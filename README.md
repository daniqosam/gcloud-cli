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