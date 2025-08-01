
In the examples/gke-a4/gke-a4-deployment.yaml blueprint from the GitHub repo, fill in the following settings in the terraform_backend_defaults and vars sections to match the specific values for your deployment:
DEPLOYMENT_NAME: a unique name for the deployment. If the deployment name isn't unique within a project, cluster creation fails.
BUCKET_NAME: the name of the Cloud Storage bucket you created in the previous step.
PROJECT_ID: your Google Cloud project ID.
COMPUTE_REGION: the compute region for the cluster.
COMPUTE_ZONE: the compute zone for the node pool of A4 machines.
Remove static_node_count.
IP_ADDRESS/SUFFIX: The IP address range that you want to allow to connect with the cluster. This CIDR block must include the IP address of the machine to call Terraform. For more information, see How authorized networks work.
Remove the extended_reservation field, and replace the field with enable_flex_start: true. Add on the next line enable_queued_provisioning: true if you'd also like to use queued provisioning. For more information, see Use node pools with flex-start with queued provisioning.
Set the boot disk sizes for each node of the system and A4 node pools. The disk size that you need depends on your use case. For example, if using the disk as a cache to reduce the latency of pulling an image repeatedly, you can set a larger disk size to accommodate your framework, model or container image:
SYSTEM_NODE_POOL_DISK_SIZE_GB: the size of the boot disk for each node of the system node pool. The smallest allowed disk size is 10. The default value is 100.
A4_NODE_POOL_DISK_SIZE_GB: the size of the boot disk for each node of the A4 node pool. The smallest allowed disk size is 10. The default value is 100.