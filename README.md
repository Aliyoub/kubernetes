
# KUBERNETES - QUELQUES CAS D'USAGE -
## Taint et Toleration

Les Taints sont utilisés pour isoler les pods de certains noeuds. En effet, si Taint est appliqué à un noeud quelconque, aucun pod ne pourra être planifié dans ce noeud. Cependant, si Taint est appliqué à un noeud, on pourra appliquer Toleration à certains pods afin qu’ils puissent être planifiés dans ce noeud.


**Appliquons Taint au noeud minikube** <br />
_kubectl taint nodes minikube key=value:NoSchedule_  <br />
![alt taint](https://aliyoub.github.io/kubernetes/images/taints-tolerations_1.png)

**Ensuite, planifions un pod et voyons s’il a été mis en place dans le noeud minikube** <br />
_> kubectl run aliyou-test-taint-pod --image=nginx_  <br />
![alt taint](https://aliyoub.github.io/kubernetes/images/taints-tolerations_2.png)


**Application de Toleration sur 3 replicas de pods** <br />
_kubectl apply -f toleration.yaml_ <br />
![alt toleration](https://aliyoub.github.io/kubernetes/images/taints-tolerations_3.png)
![alt toleration](https://aliyoub.github.io/kubernetes/images/taints-tolerations_5b.png)


**_Retrait de Taint du noeud minikube_** <br />
kubectl taint nodes minikube key=value:NoSchedule-
![alt toleration](https://aliyoub.github.io/kubernetes/images/taints-tolerations_5.png)
