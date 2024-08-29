### **Important Points**

- #### pshue-service-redeem-qa

- #### Grupo: NGRP Asphalt Loyalty QA Alert Group

- #### Applicaiton: Partnership Redeem

- #### Avaliar: Verificar a cada 5min; Retroativo a cada 15min
### **Saturation Alert**

- #### Capacity used in terms of memory or CPU:
	- ##### < 70%: Normal.
	- ##### 70% - 85%: Monitor, possible bottlenecks.
	- ##### 85%: High risk of saturation, must scale resources
		- ##### Azure Metric: Process CPU and Process private bytes
		- 


- #### Failure rate in database queries:
	- ##### < 1% failures: Normal.
	- ##### < 1-3% failures: Monitor, there may be network or database issues.
	- ##### > 3% failures: Critical, investigate immediately.
		- ##### Azure Metric: Failed requests 

