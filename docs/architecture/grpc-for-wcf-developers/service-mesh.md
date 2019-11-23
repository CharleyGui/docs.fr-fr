---
title: Maillages de service-gRPC pour les développeurs WCF
description: Utilisation d’une maille de service pour acheminer et équilibrer les demandes vers les services gRPC dans un cluster Kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: d20275082973f30bddbb342da90454401d4f019b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966966"
---
# <a name="service-meshes"></a>Maillages de service

Une maille de service est un composant d’infrastructure qui prend le contrôle des demandes de service de routage au sein d’un réseau. Les maillages de service peuvent gérer tous les types de problèmes au niveau du réseau au sein d’un cluster Kubernetes, notamment :

- Détection du service
- Équilibrage de charge
- Tolérance de panne
- Chiffrement
- Analyse

Les maillages de service Kubernetes fonctionnent en ajoutant un conteneur supplémentaire, appelé *proxy de side-car*, à chaque Pod inclus dans la maille. Le proxy prend en charge la gestion de toutes les demandes réseau entrantes et sortantes, ce qui permet à la configuration et à la gestion de la mise en réseau de rester séparées des conteneurs d’applications et, dans de nombreux cas, sans nécessiter de modification du code de l’application.

Prenons l' [exemple du chapitre précédent](kubernetes.md#testing-the-application), où les requêtes gRPC de l’application Web ont toutes été routées vers une seule instance du service gRPC. Cela est dû au fait que le nom d’hôte du service est résolu en une adresse IP et que cette adresse IP est mise en cache pendant la durée de vie de l’instance `HttpClientHandler`. Il peut être possible de contourner ce risque en gérant manuellement les recherches DNS ou en créant plusieurs clients, mais cela complique considérablement le code de l’application sans ajouter de valeur commerciale ou client.

À l’aide d’un maillage de service, les demandes du conteneur d’application sont envoyées au proxy side-car, qui peut les distribuer intelligemment sur toutes les instances de l’autre service. La maille peut également :

- Réagir en toute transparence aux défaillances des instances individuelles d’un service.
- Gérer la sémantique des nouvelles tentatives pour les échecs d’appels ou de délais d’attente
- Rediriger les demandes ayant échoué vers une autre instance sans revenir à l’application cliente.

La capture d’écran suivante montre l’application StockWeb en cours d’exécution avec la maille du service Linkerd, sans aucune modification du code de l’application, ou même l’image de l’arrimeur utilisée. La seule modification requise était l’ajout d’une annotation au déploiement dans les fichiers YAML pour les services `stockdata` et `stockweb`.

![StockWeb avec maillage de service](media/service-mesh/stockweb-servicemesh-screenshot.png)

Vous pouvez voir à partir de la colonne de serveur que les demandes de l’application StockWeb ont été routées vers les deux réplicas du service StockData, bien qu’elles proviennent d’une instance de `HttpClient` unique dans le code de l’application. En fait, si vous examinez le code, vous verrez que toutes les demandes 100 au service StockData sont effectuées simultanément à l’aide de la même instance de `HttpClient`, mais avec la maille de service, ces demandes sont équilibrées entre plusieurs instances de service disponibles.

Les maillages de service s’appliquent uniquement au trafic au sein d’un cluster. Pour les clients externes, consultez [le chapitre suivant, équilibrage de charge](load-balancing.md).

## <a name="service-mesh-options"></a>Options de maillage de service

Trois implémentations de maille de service à usage général peuvent actuellement être utilisées avec Kubernetes : Istio, Linkerd et consulaire Connect. Les trois fournissent le routage/proxy des demandes, le chiffrement du trafic, la résilience, l’authentification hôte à hôte et le contrôle du trafic.

Le choix d’un maillage de service dépend de plusieurs facteurs :

- Exigences spécifiques de l’Organisation concernant les coûts, la conformité, les plans de support payants, etc.
- La nature du cluster, sa taille, le nombre de services déployés et le volume de trafic au sein du réseau du cluster.
- Facilité de déploiement et de gestion de la maille et de son utilisation avec les services.

Pour plus d’informations sur chaque maille de service, vous pouvez accéder à partir de leurs sites Web respectifs.

- [**Istio** -istio.IO](https://istio.io)
- [**Linkerd** -linkerd.IO](https://linkerd.io)
- [**Consul** -consul.IO/Mesh.html](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a>Exemple : Ajouter Linkerd à un déploiement

Dans cet exemple, vous allez apprendre à utiliser la maille du service Linkerd avec l’application *StockKube* de [la section précédente](kubernetes.md).
Pour suivre cet exemple, vous devez [installer l’interface CLI Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Les fichiers binaires Windows peuvent être téléchargés à partir de la section GitHub releases. Veillez à utiliser la version **stable** la plus récente et non une des versions de périphérie.

Une fois l’interface CLI Linkerd installée, suivez les instructions [*prise en main* sur le site Web Linkerd] pour installer les composants Linkerd sur votre cluster Kubernetes. Les instructions sont directes et l’installation ne doit prendre que quelques minutes sur une instance Kubernetes locale.

### <a name="add-linkerd-to-kubernetes-deployments"></a>Ajouter Linkerd à des déploiements Kubernetes

L’interface CLI Linkerd fournit une commande `inject` pour ajouter les sections et les propriétés nécessaires aux fichiers Kubernetes. Vous pouvez exécuter la commande et écrire la sortie dans un nouveau fichier.

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

Vous pouvez inspecter les nouveaux fichiers pour voir les modifications apportées. Pour les objets de déploiement, une annotation de métadonnées est ajoutée pour indiquer à Linkerd d’injecter un conteneur de proxy side-car dans le pod lorsqu’il est créé.

Il est également possible de diriger la sortie de la commande `linkerd inject` vers `kubectl` directement. Les commandes suivantes fonctionnent dans PowerShell ou dans n’importe quel shell Linux.

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>Inspecter les services dans le tableau de bord Linkerd

Lancez le tableau de bord Linkerd à l’aide de l’interface de commande `linkerd`.

```console
linkerd dashboard
```

Le tableau de bord fournit des informations détaillées sur tous les services qui sont connectés à la maille.

![Tableau de bord Linkerd présentant les applications StockKube](media/service-mesh/linkerd-screenshot.png)

Si vous augmentez le nombre de réplicas du service StockData gRPC comme indiqué dans l’exemple suivant, et actualisez la page StockWeb dans le navigateur, vous devriez voir une combinaison d’ID dans la colonne serveur, indiquant que les demandes sont servies par toutes les instances disponibles .

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
>[Précédent](kubernetes.md)
>[Suivant](load-balancing.md)
