# OpenShift 4 on vSphere deployment with vSphere CSI : StorageObject Review

### Environment **Test**

- vSphere 6.7U3 with vCenter 7
- OpenShift 4.11 UPI Deployment

### Test workload

- mockup postgresql deployment with pvc

### Scenario

- Log on to openshift console, verify PVC are provisioned 
record PVC name

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled.png)

- Log on to vSphere UI 
Go to Inventory → Storage View → Select Datastore → Cloud Native Storage → Container Volumes

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%201.png)

- In “Add filter” , select Kubernetes objects → PVC name , input name of PVC

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%202.png)

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%203.png)

select filtered PVC record , click on this icon

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%204.png)

Go to “Basics” tab , review Volume Path, note parameter of volume path

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%205.png)

Browse to exact path for vmdk file

review 

file VMDK is virtual disk for PVC

file VMFD is sidecar represent for PVC

(in example recording empty PVC)

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%206.png)

Go back to OpenShift Console , create Snapshot on same PVC

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%207.png)

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%208.png)

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%209.png)

Go to vSphere UI , filter contianer volume for the same PVC

**notice volume path change to new path**

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%2010.png)

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%2011.png)

Go to file browser, noticed new vDisk and sidecar file created for snapshot

![Untitled](OpenShift%204%20on%20vSphere%20deployment%20with%20vSphere%20CSI%204a20806eaade4e9882cc4bb5699c52ac/Untitled%2012.png)