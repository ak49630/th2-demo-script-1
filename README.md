# Description:
The th2-script is a code, which contains a set of requests to the th2 components, executed in turns. The script can be written in any language that supports a common library. This script is written on python and contains one general types of actions.

* Sending events to **the estore** queue to organize test results into a structure, or to supplement information in the report.

**Schema of a simplified example script:**

<img src="https://github.com/th2-net/th2-documentation/blob/master/images/demo-ver154-main/script-base-flow.png" data-canonical-src="https://github.com/th2-net/th2-documentation/blob/master/images/demo-ver154-main/script-base-flow.png"  />

## How to start:
**Schema(th2 environment) needed:** https://github.com/th2-net/th2-infra-schema-demo/tree/ver-1.6.1-main_scenario

Python 3.7+ environment required.
1. Change **configs** based on your **RabbitMQ**
    1. Fill **mq.json** in a folder **config** with **RabbitMQ exchange** and **routing key** from **script** to **estore**. You can find this queue in Kubernetes Dashboard in Config Maps tab - script-entry-point-app-config. 
    1. Fill **rabbitMQ.json** in a folder **config** with your **RabbitMQ credentials**. You can find these credentials in Kubernetes Dashboard in Config Maps tab - rabbit-mq-app-config.
1. Install required packages described in **requirements.txt**
1. Start **run.py**

## Test Scenario:

1. Sending a child event with the FAILED status and a trace of the parent event.
2. Sending a child event with the FAILED status, pausing for one second and sending the parent event.
3. Sending a child event with the FAILED status, a pause exceeding the waiting time of parentId in crawler-process-healer, sending a child event with the FAILED status and a trace of the parent event.


