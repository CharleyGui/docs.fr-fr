---
title: Maillages de service-gRPC pour les développeurs WCF
description: Utilisation d’une maille de service pour acheminer et équilibrer les demandes vers les services gRPC dans un cluster Kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503383"
---
# <a name="service-meshes"></a>Maillages de service

Une maille de service est un composant d’infrastructure qui prend le contrôle des demandes de service de routage au sein d’un réseau. Les maillages de service peuvent gérer tous les types de problèmes au niveau du réseau au sein d’un cluster Kubernetes, notamment :

- Détection du service
- Équilibrage de la charge
- Tolérance de panne
- Chiffrement
- Surveillance

Les maillages de service Kubernetes fonctionnent en ajoutant un conteneur supplémentaire, appelé *proxy de side-car*, à chaque Pod inclus dans la maille. Le proxy prend en charge la gestion de toutes les demandes réseau entrantes et sortantes. Vous pouvez alors conserver la configuration et la gestion des aspects de la mise en réseau séparément des conteneurs d’applications. Dans de nombreux cas, cette séparation ne nécessite aucune modification du code de l’application.

Dans l' [exemple du chapitre précédent](kubernetes.md#test-the-application), les demandes gRPC de l’application Web étaient toutes acheminées vers une seule instance du service gRPC. Cela est dû au fait que le nom d’hôte du service est résolu en une adresse IP et que cette adresse IP est mise en cache pendant la durée de vie de l’instance `HttpClientHandler`. Il peut être possible de contourner ce risque en gérant manuellement les recherches DNS ou en créant plusieurs clients. Toutefois, cette solution de contournement compliquerait le code de l’application sans ajouter de valeur commerciale ou client.

Lorsque vous utilisez un maillage de service, les demandes du conteneur d’application sont envoyées au proxy side-car. Le proxy side-car peut ensuite les distribuer intelligemment sur toutes les instances de l’autre service. La maille peut également :

- Réagir en toute transparence aux défaillances des instances individuelles d’un service.
- Gérez la sémantique des nouvelles tentatives pour les échecs d’appels ou de délais d’attente.
- Rediriger les demandes ayant échoué vers une autre instance sans revenir à l’application cliente.

La capture d’écran suivante montre l’application StockWeb en cours d’exécution avec la maille de service Linkerd. Aucune modification n’est apportée au code de l’application, et l’image de l’Ancreur n’est pas utilisée. La seule modification requise était l’ajout d’une annotation au déploiement dans les fichiers YAML pour les services `stockdata` et `stockweb`.

![StockWeb avec maillage de service](media/service-mesh/stockweb-servicemesh-screenshot.png)

Vous pouvez voir à partir de la colonne de **serveur** que les demandes de l’application StockWeb ont été routées vers les deux réplicas du service stockdata, bien qu’elles proviennent d’une instance de `HttpClient` unique dans le code de l’application. En fait, si vous examinez le code, vous verrez que toutes les demandes 100 au service StockData sont effectuées simultanément à l’aide de la même instance de `HttpClient`. Avec la maille de service, ces demandes sont équilibrées entre plusieurs instances de service disponibles.

Les maillages de service s’appliquent uniquement au trafic au sein d’un cluster. Pour les clients externes, consultez le chapitre suivant, [équilibrage de charge](load-balancing.md).

## <a name="service-mesh-options"></a>Options de maillage de service

Trois implémentations de maille de service à usage général peuvent actuellement être utilisées avec Kubernetes : [Istio](https://istio.io), [Linkerd](https://linkerd.io)et [consulaire Connect](https://consul.io/mesh.html). Les trois fournissent le routage/proxy des demandes, le chiffrement du trafic, la résilience, l’authentification hôte à hôte et le contrôle du trafic.

Le choix d’un maillage de service dépend de plusieurs facteurs :

- Exigences spécifiques de l’Organisation concernant les coûts, la conformité, les plans de support payants, etc.
- La nature du cluster, sa taille, le nombre de services déployés et le volume de trafic au sein du réseau du cluster.
- Facilité de déploiement et de gestion de la maille et de son utilisation avec les services.

## <a name="example-add-linkerd-to-a-deployment"></a>Exemple : Ajouter Linkerd à un déploiement

Dans cet exemple, vous allez apprendre à utiliser la maille du service Linkerd avec l’application *StockKube* de [la section précédente](kubernetes.md).
Pour suivre cet exemple, vous devez [installer l’interface CLI Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Vous pouvez télécharger les fichiers binaires Windows à partir de la section qui répertorie les versions de GitHub. Veillez à utiliser la version *stable* la plus récente et non une des versions de périphérie.

Une fois l’interface CLI Linkerd installée, suivez les instructions [prise en main](https://linkerd.io/2/getting-started/index.html) pour installer les composants Linkerd sur votre cluster Kubernetes. Les instructions sont simples et l’installation ne doit prendre que quelques minutes sur une instance Kubernetes locale.

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

Ouvrez le tableau de bord Linkerd à l’aide de l’interface de commande `linkerd`.

```console
linkerd dashboard
```

Le tableau de bord fournit des informations détaillées sur tous les services qui sont connectés à la maille.

![Tableau de bord Linkerd présentant les applications StockKube](media/service-mesh/linkerd-screenshot.png)

Si vous augmentez le nombre de réplicas du service StockData gRPC comme indiqué dans l’exemple suivant, et actualisez la page StockWeb dans le navigateur, vous devriez voir une combinaison d’ID dans la colonne **serveur** . Cette combinaison indique que toutes les instances disponibles servent les demandes.

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
