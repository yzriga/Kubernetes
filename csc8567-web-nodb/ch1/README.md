kubectl -n u-9nl7s create deployment monpod --image=xhelozs/csc8567:v1

kubectl -n u-9nl7s port-forward pods/monpod 8080:80

kubectl -n u-9nl7s logs monpod