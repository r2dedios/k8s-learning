# Persistent Storage
Create a project for this section
```sh
oc create ns storage-learning
oc project storage-learning
```

## Exercises
Before start with any exercise, create the storage classes required for this
section
```sh
oc apply -f 00-storage-classes.yaml
```

When you're finished
```sh
cd -
oc delete -f 00-storage-classes.yaml
oc delete ns storage learning
```

### 01-pv-manual
This exercise is for creating PVC manually and check how it triggers the PV
creation and bounding.
```sh
oc apply -f 01-pvc-manual/01-pvc.yaml
oc apply -f 01-pvc-manual/02-pod.yaml

oc delete -f 01-pvc-manual
```

### 02-pv-pvc
This exercise is for creating PV and PVC manually without automatic
provisioning
```sh
oc apply -f 02-pv-pvc/01-pv.yaml
oc apply -f 02-pv-pvc/02-pvc.yaml
```

### 03-statefulset
This exercise is for using StatefulSets
```sh
oc apply -f 03-statefulset
```
