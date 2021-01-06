---
title: Kubernetes-gRPC pour les développeurs WCF
description: Exécution des services ASP.NET Core gRPC dans un cluster Kubernetes.
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938055"
---
# <a name="kubernetes"></a>Kubernetes

Bien qu’il soit possible d’exécuter des conteneurs manuellement sur des hôtes de l’arrimeur, il est préférable d’utiliser un moteur d’orchestration de conteneur pour gérer plusieurs instances exécutées sur plusieurs serveurs d’un cluster dans le cas d’un système de production fiable. Plusieurs moteurs d’orchestration de conteneur sont disponibles, y compris Kubernetes, Dockr essaim et Apache méson. Mais de ces moteurs, Kubernetes est loin et éloigné le plus couramment utilisé. il sera donc axé sur ce chapitre.

Kubernetes comprend les fonctionnalités suivantes :

- La **planification** exécute des conteneurs sur plusieurs nœuds au sein d’un cluster, en garantissant une utilisation équilibrée de la ressource disponible, en conservant les conteneurs en cours d’exécution en cas de panne et en gérant les mises à jour propagées vers les nouvelles versions d’images ou les nouvelles configurations.
- Les **contrôles d’intégrité** analysent les conteneurs pour garantir un service continu.
- La **découverte du service de & DNS** gère le routage entre les services au sein d’un cluster.
- L’entrée **expose les** services sélectionnés en externe et fournit généralement un équilibrage de la charge entre les instances de ces services.
- La **gestion des ressources** associe des ressources externes telles que le stockage à des conteneurs.

Ce chapitre explique en détail comment déployer un service ASP.NET Core gRPC et un site Web qui consomme le service dans un cluster Kubernetes. L’exemple d’application utilisé est disponible dans le référentiel [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.

## <a name="kubernetes-terminology"></a>Terminologie Kubernetes

Kubernetes utilise la *configuration d’état souhaité*: l’API est utilisée pour décrire des objets tels que les *Pod*, les *déploiements* et les *services*, et le *plan de contrôle* prend en charge l’implémentation de l’état souhaité sur tous les *nœuds* d’un *cluster*. Un cluster Kubernetes possède un nœud *principal* qui exécute l' *API Kubernetes*, que vous pouvez communiquer avec par programmation ou à l’aide de l' `kubectl` outil en ligne de commande. `kubectl` peut créer et gérer des objets à l’aide d’arguments de ligne de commande, mais il fonctionne mieux avec les fichiers YAML qui contiennent des données de déclaration pour les objets Kubernetes.

### <a name="kubernetes-yaml-files"></a>Fichiers YAML Kubernetes

Chaque fichier Kubernetes YAML aura au moins trois propriétés de niveau supérieur :

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

La `apiVersion` propriété est utilisée pour spécifier la version (et l’API) à laquelle le fichier est destiné. La `kind` propriété spécifie le type d’objet représenté par le YAML. La `metadata` propriété contient des propriétés d’objet telles que `name` , `namespace` et `labels` .

La plupart des fichiers YAML Kubernetes comporteront également une `spec` section décrivant les ressources et la configuration nécessaires à la création de l’objet.

### <a name="pods"></a>Pods

Les POD sont les unités d’exécution de base dans Kubernetes. Ils peuvent exécuter plusieurs conteneurs, mais ils sont également utilisés pour exécuter des conteneurs uniques. Le pod comprend également toutes les ressources de stockage requises par les conteneurs, ainsi que l’adresse IP du réseau.

### <a name="services"></a>Services

Les services sont des méta-objets qui décrivent des gousses (ou ensembles de Pod) et offrent un moyen d’y accéder au sein du cluster, comme le mappage d’un nom de service à un ensemble d’adresses IP Pod à l’aide du service DNS de cluster.

### <a name="deployments"></a>Déploiements

Les déploiements sont les objets d' *État souhaités* pour les pod. Si vous créez une Pod manuellement, elle ne sera pas redémarrée lorsqu’elle se terminera. Les déploiements sont utilisés pour indiquer au cluster les Pod, ainsi que le nombre de réplicas de ces gousses, qui doivent être exécutés à l’heure actuelle.

### <a name="other-objects"></a>Autres objets

Les Pod, les services et les déploiements représentent seulement trois des types d’objets les plus basiques. Il existe des dizaines d’autres types d’objets qui sont gérés par les clusters Kubernetes. Pour plus d’informations, consultez la documentation sur les [concepts de Kubernetes](https://kubernetes.io/docs/concepts/) .

### <a name="namespaces"></a>Espaces de noms

Les clusters Kubernetes sont conçus pour évoluer vers des centaines ou des milliers de nœuds et pour exécuter des nombres de services similaires. Pour éviter les conflits entre les noms d’objets, les espaces de noms sont utilisés pour regrouper des objets dans le cadre d’applications plus volumineuses. Les services de Kubernetes s’exécutent dans un `default` espace de noms. Tous les objets utilisateur doivent être créés dans leurs propres espaces de noms pour éviter les conflits potentiels avec les objets par défaut ou d’autres locataires dans le cluster.

## <a name="get-started-with-kubernetes"></a>Prise en main de Kubernetes

Si vous exécutez le Bureau de la station d’accueil pour Windows ou le Bureau de station d’accueil pour Mac, Kubernetes est déjà disponible. Il suffit de l’activer dans la section **Kubernetes** de la fenêtre **paramètres** :

![Activer Kubernetes dans le Bureau de l’ancrage](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

Pour exécuter un cluster Kubernetes local sur Linux, envisagez [minikube](https://github.com/kubernetes/minikube)ou [MicroK8s](https://microk8s.io/) si votre distribution Linux prend en charge les [instantanés](https://snapcraft.io/).

Pour confirmer que votre cluster est en cours d’exécution et accessible, exécutez la `kubectl version` commande suivante :

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

Dans cet exemple, l' `kubectl` interface CLI et le serveur Kubernetes exécutent la version 1.14.6. Chaque version de `kubectl` est censée prendre en charge la version précédente et la version suivante du serveur, donc `kubectl` 1,14 doit également fonctionner avec les versions de serveur 1,13 et 1,15.

## <a name="run-services-on-kubernetes"></a>Exécuter des services sur Kubernetes

L’exemple d’application possède un `kube` répertoire qui contient trois fichiers YAML. Le `namespace.yml` fichier déclare un espace de noms personnalisé : `stocks` . Le `stockdata.yml` fichier déclare le déploiement et le service pour l’application gRPC, et le `stockweb.yml` fichier déclare le déploiement et le service pour une application web ASP.net Core 5,0 MVC qui utilise le service gRPC.

Pour utiliser un `YAML` fichier avec `kubectl` , exécutez la `apply -f` commande :

```console
kubectl apply -f object.yml
```

La `apply` commande vérifie la validité du fichier YAML et affiche toutes les erreurs reçues de l’API, mais n’attend pas que tous les objets déclarés dans le fichier aient été créés, car cette étape peut prendre un certain temps. Utilisez la `kubectl get` commande avec les types d’objets appropriés pour vérifier la création d’objets dans le cluster.

### <a name="the-namespace-declaration"></a>Déclaration d’espace de noms

La déclaration d’espace de noms est simple et requiert uniquement l’affectation d’un `name` :

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

Utilisez `kubectl` pour appliquer le `namespace.yml` fichier et confirmer que l’espace de noms a été créé avec succès :

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>L’application StockData

Le `stockdata.yml` fichier déclare deux objets : un déploiement et un service.

#### <a name="the-stockdata-deployment"></a>Le déploiement StockData

La partie déploiement du fichier YAML fournit le `spec` pour le déploiement lui-même, y compris le nombre de réplicas requis et un `template` pour les objets Pod à créer et gérer par le déploiement. Notez que les objets de déploiement sont gérés par l' `apps` API, comme spécifié dans `apiVersion` , plutôt que l’API Kubernetes principale.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

La `spec.selector` propriété est utilisée pour faire correspondre les pod en cours d’exécution au déploiement. La propriété du Pod `metadata.labels` doit correspondre à la `matchLabels` propriété, sans quoi l’appel de l’API échoue.

La `template.spec` section déclare le conteneur à exécuter. Lorsque vous travaillez avec un cluster Kubernetes local, tel que celui fourni par le Bureau de l’ordinateur de bureau de station d’accueil, vous pouvez spécifier des images qui ont été générées localement tant qu’elles ont une balise de version.

> [!IMPORTANT]
> Par défaut, Kubernetes recherche et tente d’extraire une nouvelle image. S’il ne peut pas trouver l’image dans l’un de ses référentiels connus, la création du Pod échoue. Pour travailler avec des images locales, affectez la valeur `imagePullPolicy` à `Never` .

La `ports` propriété spécifie les ports de conteneur qui doivent être publiés sur le POD. L' `stockservice` image exécute le service sur le port http standard, le port 80 est donc publié.

La `resources` section applique des limites de ressources au conteneur en cours d’exécution dans le POD. C’est une bonne pratique, car elle empêche un pod individuel de consommer tout le processeur ou la mémoire disponible sur un nœud.

> [!NOTE]
> ASP.NET Core 5,0 a été optimisé et réglé pour s’exécuter dans des conteneurs à ressources limitées. L' `dotnet/core/aspnet` image de l’ancreur définit une variable d’environnement pour indiquer à l' `dotnet` exécution qu’il se trouve dans un conteneur.

#### <a name="the-stockdata-service"></a>Service StockData

La partie service du fichier YAML déclare le service qui fournit l’accès aux Pod au sein du cluster.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

Le service `spec` utilise la `selector` propriété pour faire correspondre l’exécution `Pods` , dans ce cas, en recherchant les Pod qui ont une étiquette `run: stockdata` . Le spécifié `port` sur les Pod correspondants est publié par le service nommé. D’autres pod en cours d’exécution dans l' `stocks` espace de noms peuvent accéder à http sur ce service en utilisant `http://stockdata` comme adresse. Les pod en cours d’exécution dans d’autres espaces de noms peuvent utiliser le `http://stockdata.stocks` nom d’hôte. Vous pouvez contrôler l’accès au service entre espaces de noms à l’aide de [stratégies réseau](https://kubernetes.io/docs/concepts/services-networking/network-policies/).

#### <a name="deploy-the-stockdata-application"></a>Déployer l’application StockData

Utilisez `kubectl` pour appliquer le `stockdata.yml` fichier et confirmer que le déploiement et le service ont été créés :

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>L’application StockWeb

Le `stockweb.yml` fichier déclare le déploiement et le service pour l’application MVC.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>Variables d'environnement

La `env` section de l’objet de déploiement spécifie les variables d’environnement à définir dans le conteneur qui exécute les `stockweb:1.0.0` images.

La **`StockData__Address`** variable d’environnement est mappée au `StockData:Address` paramètre de configuration grâce au fournisseur de configuration EnvironmentVariables. Ce paramètre utilise des traits de soulignement doubles entre les noms et des sections distinctes. L’adresse utilise le nom de service du `stockdata` service, qui s’exécute dans le même espace de noms Kubernetes.

La **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** variable d’environnement définit un <xref:System.AppContext> commutateur qui autorise les connexions http/2 non chiffrées pour <xref:System.Net.Http.HttpClient> . Cette variable d’environnement fait la même chose que la définition du commutateur dans le code, comme illustré ici :

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Si vous utilisez une variable d’environnement pour le commutateur, vous pouvez facilement modifier le contexte en fonction du contexte dans lequel l’application s’exécute.

#### <a name="service-types"></a>Types de service

La `type: NodePort` propriété est utilisée pour rendre l’application Web accessible à partir de l’extérieur du cluster. Ce type de propriété force Kubernetes à publier le port 80 sur le service sur un port arbitraire sur les sockets réseau externes du cluster. Vous pouvez trouver le port attribué à l’aide de la `kubectl get service` commande.

Le `stockdata` service ne doit pas être accessible depuis l’extérieur du cluster, donc il utilise le type par défaut, `ClusterIP` .

Les systèmes de production utiliseront très probablement un équilibreur de charge intégré pour exposer les applications publiques aux consommateurs externes. Les services exposés de cette manière doivent utiliser le `LoadBalancer` type.

Pour plus d’informations sur les types de services, consultez la documentation des [services de publication Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .

#### <a name="deploy-the-stockweb-application"></a>Déployer l’application StockWeb

Utilisez `kubectl` pour appliquer le `stockweb.yml` fichier et confirmer que le déploiement et le service ont été créés :

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

La sortie de la `get service` commande indique que le port http a été publié sur `32564` le port sur le réseau externe. Pour le Bureau de l’arrimeur, cette adresse IP sera localhost. Vous pouvez accéder à l’application en accédant à `http://localhost:32564` .

### <a name="test-the-application"></a>Tester l’application

L’application StockWeb affiche une liste des actions NASDAQ récupérées à partir d’un service de requête-réponse simple. Pour cette démonstration, chaque ligne affiche également l’ID unique de l’instance de service qui l’a retournée.

![Capture d’écran StockWeb](media/kubernetes/stockweb-screenshot.png)

Si le nombre de réplicas du `stockdata` service a été augmenté, vous pouvez vous attendre à ce que la valeur du **serveur** passe d’une ligne à l’autres, mais en fait, tous les enregistrements 100 sont toujours retournés à partir de la même instance. Si vous actualisez la page toutes les quelques secondes, l’ID du serveur reste le même. Pourquoi cela se produit-il ? Il existe deux facteurs à lire ici.

Tout d’abord, le système de détection du service Kubernetes utilise l’équilibrage de charge par tourniquet (Round Robin) par défaut. La première fois que le serveur DNS est interrogé, il retourne la première adresse IP correspondante pour le service. La prochaine fois, elle renverra l’adresse IP suivante dans la liste, et ainsi de suite, jusqu’à la fin. À ce stade, il repasse au début.

Deuxièmement, le `HttpClient` utilisé pour le client gRPC de l’application StockWeb est créé et géré par l' [ASP.net Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), et une seule instance de ce client est utilisée pour chaque appel à la page. Le client n’effectue qu’une seule recherche DNS, donc toutes les demandes sont acheminées vers la même adresse IP. Et étant donné que le `HttpClientHandler` est mis en cache pour des raisons de performances, plusieurs demandes en succession rapide utilisent *toutes* la même adresse IP, jusqu’à ce que l’entrée DNS mise en cache expire ou que l’instance de gestionnaire soit supprimée pour une raison quelconque.

Le résultat est que par défaut, les demandes adressées à un service gRPC ne sont pas équilibrées sur toutes les instances de ce service dans le cluster. Les différents consommateurs utilisent des instances différentes, mais cela ne garantit pas une bonne distribution des demandes ou une utilisation équilibrée des ressources.

Le chapitre suivant, [maillages de service](service-mesh.md), traite ce problème.

>[!div class="step-by-step"]
>[Précédent](docker.md) 
> [Suivant](service-mesh.md)
