# Configuration
- create a file clientSecrt in the correct overlay directory, add the google credentials for IDP
 - Something is broken with the way kustomize secretGenerator in the overlays/<dir>/kustomize.yaml works,  
   this produces 4 extra chars as padding to the end which OCP doesn't like, instead run:
   `oc create secret generic idp-secret-test --from-literal=clientSecret=$(cat overlays/lab/clientSecret) -n openshift-config`
- edit `google-oauth-cr.yaml`
  - changed googleID


# Apply
- `oc apply -k overlays/lab`
