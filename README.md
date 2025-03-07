# k8s-crd

# How to deploy

# amit@k8s-master-01:~/k8s$ kubectl apply -f kv-crd.yml
`` customresourcedefinition.apiextensions.k8s.io/keyvaluestores.myk8s.local created

# amit@k8s-master-01:~/k8s$ kubectl apply -f create-resource.yml 
keyvaluestore.myk8s.local/k8s-kv-store-crd created

# amit@k8s-master-01:~/k8s$ kubectl get crd
NAME                                         CREATED AT
keyvaluestores.myk8s.local                   2025-03-06T16:01:05Z

# amit@k8s-master-01:~/k8s$ kubectl describe crd keyvaluestores.myk8s.local
Name:         keyvaluestores.myk8s.local
Namespace:    
Labels:       <none>
Annotations:  <none>
API Version:  apiextensions.k8s.io/v1
Kind:         CustomResourceDefinition
Metadata:
  Creation Timestamp:  2025-03-06T16:01:05Z
  Generation:          1
  Resource Version:    544971
  UID:                 8c006a99-b1e7-4e0e-98eb-e9441db4c3ad
Spec:
  Conversion:
    Strategy:  None
  Group:       myk8s.local
  Names:
    Categories:
      custom
    Kind:       keyvaluestore
    List Kind:  keyvaluestoreList
    Plural:     keyvaluestores
    Short Names:
      kv
    Singular:  keyvaluestore
  Scope:       Namespaced
  Versions:
    Name:  v1
    Schema:
      openAPIV3Schema:
        Properties:
          Spec:
            Properties:
              field1:
                Type:  string
              field2:
                Type:  integer
            Type:      object
        Type:          object
    Served:            true
    Storage:           true
Status:
  Accepted Names:
    Categories:
      custom
    Kind:       keyvaluestore
    List Kind:  keyvaluestoreList
    Plural:     keyvaluestores
    Short Names:
      kv
    Singular:  keyvaluestore
  Conditions:
    Last Transition Time:  2025-03-06T16:01:05Z
    Message:               no conflicts found
    Reason:                NoConflicts
    Status:                True
    Type:                  NamesAccepted
    Last Transition Time:  2025-03-06T16:01:05Z
    Message:               the initial names have been accepted
    Reason:                InitialNamesAccepted
    Status:                True
    Type:                  Established
  Stored Versions:
    v1
Events:  <none>

# amit@k8s-master-01:~/k8s$ kubectl get keyvaluestores
NAME               AGE
k8s-kv-store-crd   3m20s

# amit@k8s-master-01:~/k8s$ kubectl describe keyvaluestores/k8s-kv-store-crd
Name:         k8s-kv-store-crd
Namespace:    default
Labels:       <none>
Annotations:  <none>
API Version:  myk8s.local/v1
Kind:         keyvaluestore
Metadata:
  Creation Timestamp:  2025-03-06T16:04:56Z
  Generation:          1
  Resource Version:    545491
  UID:                 a2e22c8b-86f9-49d1-985a-7e094b6364fa
Spec:
  field1:  AccountBalance
  field2:  1000
Events:    <none>
