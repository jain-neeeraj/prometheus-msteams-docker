
prometheus-msteams-docker
=================================================
This repo is based on the code from [dockerprom](https://github.com/stefanprodan/dockprom). While original one did not had support for MS Teams, I have added the same using code from [prometheus-msteams](https://github.com/bzon/prometheus-msteams). 

This is also consuming an API health status exporter from [api-exporter](https://github.com/jain-neeeraj/api-health-check-exporter-prometheus)

In order to send alerts to MS-Teams channel, you need to provide webhook URL of specified channel under prometheus-msteams of compose file. As shown below:

```
  prometheus-msteams:
    image: docker.io/bzon/prometheus-msteams:v1.1.4
    container_name: prometheus-msteams
    restart: unless-stopped
    environment:
        - TEAMS_INCOMING_WEBHOOK_URL=https://outlook.office.com/webhook/d295a717-549b-4420-a4a9-2efedf46cab2@8f3e36ea-8039-4b40-81a7-7dc0599e8645/IncomingWebhook/aff9e2fcabdf483fbf64c03fd97d20a4/b2e204be-1188-425e-9178-6563f42c357d
        - TEAMS_REQUEST_URI=alertmanager
    expose:
      - 2000
    networks:
      - monitor-net
    labels:
      org.label-schema.group: "monitoring"
```
For more details, you can refer to documentation of referenced projects at:

 - Dockerprom - [Readme file](https://github.com/stefanprodan/dockprom/blob/master/README.md)
 - prometheus-msteams - [Readme file](https://github.com/bzon/prometheus-msteams/blob/master/README.md)
- api-health-check-exporter-prometheus - [Readme file]([https://github.com/jain-neeeraj/api-health-check-exporter-prometheus](https://github.com/jain-neeeraj/api-health-check-exporter-prometheus))