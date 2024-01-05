
# KUBERNETES - QUELQUES CAS D'USAGE -
## Taint et Toleration

Les Taints sont utilisés pour isoler les pods de certains noeuds. En effet, si Taint est appliqué à un noeud quelconque, aucun pod ne pourra être planifié dans ce noeud. Cependant, si Taint est appliqué à un noeud, on pourra appliquer Toleration à certains pods afin qu’ils puissent être planifiés dans ce noeud.


Appliquons Taint au noeud minikube
kubectl taint nodes minikube key=value:NoSchedule
