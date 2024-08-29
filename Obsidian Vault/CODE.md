
`package com.circlek.ngrp.easypay.card.autolink;

import com.circlek.ngrp.easypay.card.autolink.clients.LoyaltyOrchClient;
import com.circlek.ngrp.easypay.card.autolink.clients.MessageOrchClient;
import com.circlek.ngrp.easypay.card.autolink.configs.LoyaltyOrchConnConfigs;
import com.circlek.ngrp.easypay.card.autolink.dto.EnrollmentQueueItem;
import com.circlek.ngrp.easypay.card.autolink.exception.CardLinkErrorException;
import com.circlek.ngrp.easypay.card.autolink.exception.CardUnlinkErrorException;
import com.circlek.ngrp.easypay.card.autolink.exception.MemberNotFoundException;
import com.circlek.ngrp.easypay.card.autolink.exception.MessageErrorException;
import com.google.gson.Gson;
import com.google.gson.GsonBuilder;
import com.microsoft.azure.functions.ExecutionContext;
import com.microsoft.azure.functions.annotation.FunctionName;
import com.microsoft.azure.functions.annotation.QueueTrigger;
import com.microsoft.azure.functions.annotation.StorageAccount;
import java.io.IOException;
import java.net.URISyntaxException;
import java.util.List;
import org.apache.commons.lang3.StringUtils;

public class EnrollmentQueueProcessor {

  private static final Gson gson = new GsonBuilder().create();
  private static final String STORAGE_CONN_STRING = "enrollment.storageAccount";
  private static final String EMAIL_TEMPLATE = "TBD_template_name";
  private String failureReason;
  private String token;
  private

  @StorageAccount(STORAGE_CONN_STRING)
  @FunctionName("queue-function")
  public void run(
      @QueueTrigger(name = "EnrollmentQueueTrigger",
          queueName = "%enrollment.autolink.queueName%") String message,
      final ExecutionContext context
  ) throws URISyntaxException, IOException, InterruptedException, MemberNotFoundException {
    final MessageOrchClient messageOrchClient = new MessageOrchClient();
    final LoyaltyOrchClient loyaltyOrchClient = new LoyaltyOrchClient();
    token = loyaltyOrchClient.generateSessionToken(LoyaltyOrchConnConfigs.getSessionPath(), LoyaltyOrchConnConfigs.getMasterToken(), LoyaltyOrchConnConfigs.getTimeout(), gson);

    EnrollmentQueueItem enrollmentQueueItem = gson.fromJson(message, EnrollmentQueueItem.class);

    //Quando fizer essa Busca se o email não existir ou se não houver resposta da API devo lançar exceptions
    LoyaltyOrchClient.Member member = loyaltyOrchClient.getMember(token, enrollmentQueueItem.email());

    if (member == null || !(member.memberStatus() == "Active"))
      throw new MemberNotFoundException(enrollmentQueueItem.email());

    if(member.extensions().properties().get())


    //Corrigir if
    if (member.extensions().

        properties().

        get("")) {
      failureReason = "Expiration date > 7";
      context.getLogger().warning(failureReason);
      return;
    }

    // Data sempre preenchida.


    // memberStatus != Active
    // ou
    // EasyPayApplicationDate > 7 dias


    // memberStatus != Active
    // ou
    // EasyPayApplicationDate > 7 dias

    //

    //Quais exceptions?

    processQueueItem(enrollmentQueueItem, loyaltyOrchClient, messageOrchClient, context);
  }

  static void processQueueItem(
      EnrollmentQueueItem item,
      LoyaltyOrchClient loyaltyOrchClient,
      MessageOrchClient messageOrchClient,
      ExecutionContext context
  ) throws URISyntaxException, IOException, InterruptedException {

    final String startedTrigger = String.format(
        "Queue trigger for enrollment %s started: %s", item.email(), item.timerInfo().getScheduleStatus()
            .getLastUpdated()
    );
    context.getLogger().info(startedTrigger);
    final long start = System.nanoTime();

    final String sessionToken = loyaltyOrchClient.generateSessionToken(
        LoyaltyOrchConnConfigs.getSessionPath(),
        LoyaltyOrchConnConfigs.getMasterToken(),
        LoyaltyOrchConnConfigs.getTimeout(),
        gson
    );
    LoyaltyOrchClient.Member member = loyaltyOrchClient.getMember(sessionToken, item.email());
    List<LoyaltyOrchClient.CardData> cards = loyaltyOrchClient.listCards(sessionToken, member.oktaId());

    try {
      loyaltyOrchClient.linkCard(sessionToken, member.oktaId(),
          StringUtils.right(item.cardNumber(), 4));
    } catch (CardLinkErrorException e) {
      throw new RuntimeException(e);
    }

    try {
      loyaltyOrchClient.unlinkCard(sessionToken, member.oktaId(), item.cardNumber());
    } catch (CardUnlinkErrorException e) {
      throw new RuntimeException(e);
    }

    try {
      messageOrchClient.send(sessionToken, item.email(), EMAIL_TEMPLATE);
    } catch (MessageErrorException e) {
      throw new RuntimeException(e);
    }

    final long finish = System.nanoTime();
    final String logInfoElapsedTime = String.format("elapsedTime for enrollment %s: %s",
        item.email(), (finish - start) / 1_000_000L);
    context.getLogger().info(logInfoElapsedTime);
    context.getLogger().info("Queue trigger finished.");

  }
}`