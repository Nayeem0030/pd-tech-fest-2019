# Steps by step guide for Reactor Demo on Event Driven Autoscaling with KEDA

## Initialize AKS cluster

```powershell

.\initializeAKS.ps1

```

## Install RabbitMQ

```powershell

.\deployRabbitMQ.ps1

```

## Port forward RabbtiMQ service

```powershell

kubectl port-forward svc/rabbitmq 15672:15672

```

## Deploy TechTalks Producer and Consumer

```powershell

.\deployTechTalks-AKS.ps1

```

## Generate messages using TechTalks API

```powershell

http://20.44.242.190/api/TechTalks/Generate?numberOfMessages=4000

```

Note: replace IP address with the service load balancer external IP

## Deploy KEDA Autoscaler

```powershell

.\deployAutoScaler.ps1

```

## Watch autoscaling in action

```powershell

kubectl get deploy --watch

kubectl get pods --watch

```