# Documentasi gcloud-cli 
## Create VPC menggunakan CLI 

### Check List VPC dan Subnets
```bash
gcloud compute networks list

NAME     SUBNET_MODE  BGP_ROUTING_MODE  IPV4_RANGE  GATEWAY_IPV4
default  AUTO         REGIONAL

gcloud compute networks subnets list

NAME     REGION                   NETWORK  RANGE
default  us-central1              default  10.128.0.0/20
default  us-east1                 default  10.142.0.0/20
default  asia-northeast1          default  10.146.0.0/20
default  southamerica-east1       default  10.158.0.0/20
default  asia-southeast1          default  10.148.0.0/20
default  asia-southeast2          default  10.184.0.0/20
default  asia-northeast2          default  10.174.0.0/20
default  northamerica-northeast1  default  10.162.0.0/20
default  us-west3                 default  10.180.0.0/20
default  europe-west4             default  10.164.0.0/20
default  europe-west3             default  10.156.0.0/20
default  asia-east2               default  10.170.0.0/20
default  europe-north1            default  10.166.0.0/20
default  asia-east1               default  10.140.0.0/20
default  us-west2                 default  10.168.0.0/20
default  australia-southeast1     default  10.152.0.0/20
default  europe-west2             default  10.154.0.0/20
default  us-west1                 default  10.138.0.0/20
default  asia-northeast3          default  10.178.0.0/20
default  us-east4                 default  10.150.0.0/20
default  europe-west1             default  10.132.0.0/20
default  europe-west6             default  10.172.0.0/20
default  asia-south1              default  10.160.0.0/20
default  us-west4                 default  10.182.0.0/20
```

### create vpc dan subnets
```bash
#create vpc custom subnet 
gcloud compute networks create [VPC_NAME] --description "descriprion vpc" --subnet-mode custom

gcloud compute networks create vpc-bku-devel --description "vpc untuk project bku development" --subnet-mode custom
Created [https://www.googleapis.com/compute/v1/projects/bkudevel/global/networks/vpc-bku-devel].
NAME           SUBNET_MODE  BGP_ROUTING_MODE  IPV4_RANGE  GATEWAY_IPV4
vpc-bku-devel  CUSTOM       REGIONAL

#example firewall config 
$ gcloud compute firewall-rules create <FIREWALL_NAME> --network vpc-bku-devel --allow tcp,udp,icmp --source-ranges <IP_RANGE>
$ gcloud compute firewall-rules create <FIREWALL_NAME> --network vpc-bku-devel --allow tcp:22,tcp:3389,icmp

#create vpc subnet
gcloud compute networks subnets create subnet-vpc-bku-devel-asia-southeast2-1 --network vpc-bku-devel --region asia-southeast2 --range 10.0.1.0/24

#check list subnet
gcloud compute networks subnets list 
gcloud compute networks subnets list --network vpc-bku-devel

#create firewall
gcloud compute firewall-rules create vpc-bku-allow-rdp --network vpc-bku-devel --allow tcp:3389
gcloud compute firewall-rules create vpc-bku-allow-ssh --network vpc-bku-devel --allow tcp:22
gcloud compute firewall-rules create vpc-bku-allow-postgres --network vpc-bku-devel --allow tcp:5432
```