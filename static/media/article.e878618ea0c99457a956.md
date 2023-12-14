<br /><br />
<span class="main-sub-title">Taint et Toleration</span>
<p class="introduction"> Les Taints sont utilisés pour isoler les pods de certains noeuds.
En effet, si Taint est appliqué à un noeud quelconque, aucun pod ne pourra être planifié dans ce noeud.
Cependant, si Taint est appliqué à un noeud, on pourra appliquer Toleration à certains pods afin qu’ils puissent être planifiés dans ce noeud.</p>


<span class="sub-title">Appliquer Taint au noeud minikube</span>
<Code language="bash">
kubectl taint nodes minikube key=value:NoSchedule
</Code>
<img src="/kubernetes/images/taints-tolerations_1.png" style="width:100%; "/>


<span class="sub-title">Ensuite, planifions un pod et voyons s’il a été  mis en place dans le noeud minikube</span>
<Code language="bash">
kubectl run aliyou-test-taint-pod --image=nginx
</Code>
<img src="/kubernetes/images/taints-tolerations_2.png" style="width:100%; "/>




<span class="sub-title">Application de Toleration sur 3 replicas de pods</span>
<Code language="bash">
kubectl apply -f toleration.yaml
</Code>
<img src="/kubernetes/images/taints-tolerations_3.png" style="width:100%; "/>



<img src="/kubernetes/images/taints-tolerations_5b.png" style="width:100%;"/>


<span class="sub-title">retrait de Taint du noeud minikube</span>
<Code language="bash">
kubectl taint nodes minikube key=value:NoSchedule-
</Code>
<img src="/kubernetes/images/taints-tolerations_5.png" style="width:100%; "/>