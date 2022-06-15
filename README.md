
#




## Ingestion
Geo-redundant storage with the highest level of availability and performance is ideal for low-latency, high-QPS content serving to users distributed across geographic regions. Cloud Storage provides the availability and throughput needed to stream audio or video directly to apps or websites.

### 
Once you create a bucket and set a geographic location for storing your object data it is permanent  when you create a bucket. All Cloud Storage data is redundant across at least two zones within at least one geographic place as soon as you upload it.

![Alt text](/images/simple-gcs-arch.jpg?raw=true "Optional Title")

<a href="https://stackoverflow.com/"><img src="RELATIVE_PATH_TO_IMAGE></img></a>

When creating the cloud storage bucket you can specific whether the objects will be stored in a 
- region is a specific geographic place, such as São Paulo.
- dual-region is a specific pair of regions, such as Tokyo and Osaka.
- multi-region is a large geographic area, such as the United States, that contains two or more geographic places.

Objects can be stored in different storage classes for any workload

* **Standard Storage:** Good for “hot” data that’s accessed frequently, including websites, streaming videos, and mobile apps.
* **Nearline Storage:** Low cost. Good for data that can be stored for at least 30 days, including data backup and long-tail multimedia content.
* **Coldline Storage:** Very low cost. Good for data that can be stored for at least 90 days, including disaster recovery.
* **Archive Storage:** Lowest cost. Good for data that can be stored for at least 365 days, including regulatory archives.

#### Useful Links
Object Storage: https://cloud.google.com/storage
Bucket locations https://cloud.google.com/storage/docs/locations


## Setup

1. Create a GCP Project
2. Launch Cloud Shell
3. In your development environment, run the gsutil mb command:

```gsutil mb -p PROJECT_ID gs://BUCKET_NAME```

Where:

 **PROJECT_ID** is the ID of the Cloud project that you want to create the bucket in.
 **BUCKET_NAME** is the name you want to give your bucket, subject to naming requirements. 
 
 
For example, my-bucket.
If the request is successful, the command returns the following message:


Creating gs://BUCKET_NAME/...
Set the following optional flags to have greater control over the creation of your bucket. You can specify the

**-c:** default storage class of your bucket. For example, NEARLINE.
**-l:** location of your bucket. For example, US-EAST1.
**-b:** uniform bucket-level access setting for your bucket.

For example:

gsutil mb -p PROJECT_ID -c STORAGE_CLASS -l BUCKET_LOCATION -b on gs://BUCKET_NAME



### Key concepts
Understanding RTO and RPO
The **recovery time objective (RTO)** is the window of time after the onset of an outage. It represents the maximum acceptable length of time before a service comes back online.

The **recovery point objective (RPO)** is the window of time prior to an outage. It represents the maximum acceptable length of time required to complete object replication. It also represents the amount of time that data could be considered "at-risk".


