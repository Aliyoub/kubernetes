<br /><br />
<span class="sub-title">Taint et Toleration</span>
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


<span class="sub-title">Installation du dépôt Docker</span>
<Code language="bash">
sudo apt install ca-certificates curl gnupg lsb-release
</Code>
<p class="description">
*gnupg* pour les clés gpg<br>
*lsb-release* pour retrouver la version de notre système d’exploitation</p>
<img src="/docker/images/ca-certificates_curl_gnupg _lsb-release.png" style="width:100%;"/>



<span class="sub-title">Creation du repertoire /etc/apt/keyrings pour le stockage de la clé gpg</span>
<Code language="bash">
sudo mkdir -m 0755 -p /etc/apt/keyrings
</Code>
<img src="/docker/images/mkdir_keyrings.png" style="width:100%; "/>


<span class="sub-title">Récupération de la clé gpg depuis le site officiel de Docker, à l’adresse suivante:  download.docker.com/linux/ubuntu/gpg, 
<br />pour l’installer dans le répertoire préalablement crée: etc/apt/keyrings
<br />Nommons cette clé docker.gpg</span>
<Code language="bash">
curl -fsSL https:\//download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
</Code>
<img src="/docker/images/docker-gpg.png" style="width:100%;"/>




<span class="sub-title">Mise en place du dépôt Docker proprement dite</span>
<Code language="bash">
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https:\//download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
</Code>

<br />
<br />
<br />
<span class="sub-title"> Mise à jour des paquets </span>
<Code language="bash">
sudo apt-get update
</Code>
<img src="/docker/images/maj-caches.png" style="width:100%;"/>


<span class="sub-title">Installation de DOCKER</span>
<Code language="bash">
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
</Code>
<img src="/docker/images/installation-docker.png" style="width:100%;"/>