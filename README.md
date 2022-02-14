# bsc-node
BSc node with snapshot
To have our own bsc-node running on GKE cluster follow these steps.
1. Create node pool using Gcloud command
    - gcloud beta container node-pools create bsc-node-pool --cluster=london-b --disk-size=200gb --disk-type=pd-balanced --image-type=UBUNTU --machine-type=n2-highmem-8 --max-pods-per-node=64 --node-locations=europe-west4-c --node-taints=bsc-taint=bsc-pod-taint:PreferNoSchedule --num-nodes=1 --ephemeral-storage local-ssd-count=16 --zone=europe-west2-b       
2. Do not enable node auto-upgrades or node auto-repair      for clusters or node pools using local SSDs for persistent data.
3. Create PV.yaml to use the nvme disks we have created in the command above.