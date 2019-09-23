---
title: Maillages de service-gRPC pour les développeurs WCF
description: Utilisation d’une maille de service pour acheminer et équilibrer les demandes vers les services gRPC dans un cluster Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7fc80b95937dab9153b72aa6bc8da90f6453779f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184091"
---
# <a name="service-meshes"></a><span data-ttu-id="3c560-103">Maillages de service</span><span class="sxs-lookup"><span data-stu-id="3c560-103">Service meshes</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3c560-104">Une maille de service est un composant d’infrastructure qui prend le contrôle des demandes de service de routage au sein d’un réseau.</span><span class="sxs-lookup"><span data-stu-id="3c560-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="3c560-105">Les maillages de service peuvent gérer tous les types de problèmes au niveau du réseau au sein d’un cluster Kubernetes, notamment :</span><span class="sxs-lookup"><span data-stu-id="3c560-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="3c560-106">Détection du service</span><span class="sxs-lookup"><span data-stu-id="3c560-106">Service discovery</span></span>
- <span data-ttu-id="3c560-107">Équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="3c560-107">Load balancing</span></span>
- <span data-ttu-id="3c560-108">Tolérance de pannes</span><span class="sxs-lookup"><span data-stu-id="3c560-108">Fault tolerance</span></span>
- <span data-ttu-id="3c560-109">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="3c560-109">Encryption</span></span>
- <span data-ttu-id="3c560-110">Analyse</span><span class="sxs-lookup"><span data-stu-id="3c560-110">Monitoring</span></span>

<span data-ttu-id="3c560-111">Les maillages de service Kubernetes fonctionnent en ajoutant un conteneur supplémentaire, appelé *proxy de side-car*, à chaque Pod inclus dans la maille.</span><span class="sxs-lookup"><span data-stu-id="3c560-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="3c560-112">Le proxy prend en charge la gestion de toutes les demandes réseau entrantes et sortantes, ce qui permet à la configuration et à la gestion de la mise en réseau de rester séparées des conteneurs d’applications et, dans de nombreux cas, sans nécessiter de modification du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c560-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="3c560-113">Prenons l' [exemple du chapitre précédent](kubernetes.md#testing-the-application), où les requêtes gRPC de l’application Web ont toutes été routées vers une seule instance du service gRPC.</span><span class="sxs-lookup"><span data-stu-id="3c560-113">Take the [previous chapter's example](kubernetes.md#testing-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="3c560-114">Cela se produit parce que le nom d’hôte du service est résolu en une adresse IP et que cette adresse IP est mise en cache `HttpClientHandler` pendant la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="3c560-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="3c560-115">Il peut être possible de contourner ce risque en gérant manuellement les recherches DNS ou en créant plusieurs clients, mais cela complique considérablement le code de l’application sans ajouter de valeur commerciale ou client.</span><span class="sxs-lookup"><span data-stu-id="3c560-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="3c560-116">À l’aide d’un maillage de service, les demandes du conteneur d’application sont envoyées au proxy side-car, qui peut les distribuer intelligemment sur toutes les instances de l’autre service.</span><span class="sxs-lookup"><span data-stu-id="3c560-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="3c560-117">La maille peut également :</span><span class="sxs-lookup"><span data-stu-id="3c560-117">The mesh can also:</span></span>

- <span data-ttu-id="3c560-118">Réagir en toute transparence aux défaillances des instances individuelles d’un service.</span><span class="sxs-lookup"><span data-stu-id="3c560-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="3c560-119">Gérer la sémantique des nouvelles tentatives pour les échecs d’appels ou de délais d’attente</span><span class="sxs-lookup"><span data-stu-id="3c560-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="3c560-120">Rediriger les demandes ayant échoué vers une autre instance sans revenir à l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="3c560-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="3c560-121">La capture d’écran suivante montre l’application StockWeb en cours d’exécution avec la maille du service Linkerd, sans aucune modification du code de l’application, ou même l’image de l’arrimeur utilisée.</span><span class="sxs-lookup"><span data-stu-id="3c560-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="3c560-122">La seule modification requise était l’ajout d’une annotation au déploiement dans les fichiers YAML pour les `stockdata` services et. `stockweb`</span><span class="sxs-lookup"><span data-stu-id="3c560-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb avec maillage de service](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="3c560-124">Vous pouvez voir à partir de la colonne serveur que les demandes de l’application StockWeb ont été routées vers les deux réplicas du service stockdata, bien qu' `HttpClient` elles proviennent d’une instance unique dans le code de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c560-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="3c560-125">En fait, si vous examinez le code, vous verrez que toutes les demandes 100 au service stockdata sont effectuées simultanément à l' `HttpClient` aide de la même instance, mais avec la maille de service, ces demandes sont équilibrées entre plusieurs instances de service disponibles.</span><span class="sxs-lookup"><span data-stu-id="3c560-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="3c560-126">Les maillages de service s’appliquent uniquement au trafic au sein d’un cluster.</span><span class="sxs-lookup"><span data-stu-id="3c560-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="3c560-127">Pour les clients externes, consultez [le chapitre suivant, équilibrage de charge](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="3c560-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="3c560-128">Options de maillage de service</span><span class="sxs-lookup"><span data-stu-id="3c560-128">Service mesh options</span></span>

<span data-ttu-id="3c560-129">Trois implémentations de maille de service à usage général peuvent actuellement être utilisées avec Kubernetes : Istio, Linkerd et consulaire Connect.</span><span class="sxs-lookup"><span data-stu-id="3c560-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="3c560-130">Les trois fournissent le routage/proxy des demandes, le chiffrement du trafic, la résilience, l’authentification hôte à hôte et le contrôle du trafic.</span><span class="sxs-lookup"><span data-stu-id="3c560-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="3c560-131">Le choix d’un maillage de service dépend de plusieurs facteurs :</span><span class="sxs-lookup"><span data-stu-id="3c560-131">Choosing a service mesh depends multiple factors:</span></span> 

- <span data-ttu-id="3c560-132">Exigences spécifiques de l’Organisation concernant les coûts, la conformité, les plans de support payants, etc.</span><span class="sxs-lookup"><span data-stu-id="3c560-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span> 
- <span data-ttu-id="3c560-133">La nature du cluster, sa taille, le nombre de services déployés et le volume de trafic au sein du réseau du cluster.</span><span class="sxs-lookup"><span data-stu-id="3c560-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="3c560-134">Facilité de déploiement et de gestion de la maille et de son utilisation avec les services.</span><span class="sxs-lookup"><span data-stu-id="3c560-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="3c560-135">Pour plus d’informations sur chaque maille de service, vous pouvez accéder à partir de leurs sites Web respectifs.</span><span class="sxs-lookup"><span data-stu-id="3c560-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="3c560-136">**Istio** -istio.IO</span><span class="sxs-lookup"><span data-stu-id="3c560-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="3c560-137">**Linkerd** -linkerd.IO</span><span class="sxs-lookup"><span data-stu-id="3c560-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="3c560-138">**Consul** -consul.IO/Mesh.html</span><span class="sxs-lookup"><span data-stu-id="3c560-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="3c560-139">Exemple : Ajouter Linkerd à un déploiement</span><span class="sxs-lookup"><span data-stu-id="3c560-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="3c560-140">Dans cet exemple, vous allez apprendre à utiliser la maille du service Linkerd avec l’application *StockKube* de [la section précédente](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="3c560-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="3c560-141">Pour suivre cet exemple, vous devez [installer l’interface CLI Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="3c560-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="3c560-142">Les fichiers binaires Windows peuvent être téléchargés à partir de la section GitHub releases. Veillez à utiliser la version **stable** la plus récente et non une des versions de périphérie.</span><span class="sxs-lookup"><span data-stu-id="3c560-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="3c560-143">Une fois l’interface CLI Linkerd installée, suivez les instructions [*prise en main* sur le site Web Linkerd] pour installer les composants Linkerd sur votre cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3c560-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="3c560-144">Les instructions sont directes et l’installation ne doit prendre que quelques minutes sur une instance Kubernetes locale.</span><span class="sxs-lookup"><span data-stu-id="3c560-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="3c560-145">Ajouter Linkerd à des déploiements Kubernetes</span><span class="sxs-lookup"><span data-stu-id="3c560-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="3c560-146">L’interface CLI Linkerd fournit `inject` une commande pour ajouter les sections et les propriétés nécessaires aux fichiers Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3c560-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="3c560-147">Vous pouvez exécuter la commande et écrire la sortie dans un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="3c560-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="3c560-148">Vous pouvez inspecter les nouveaux fichiers pour voir les modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="3c560-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="3c560-149">Pour les objets de déploiement, une annotation de métadonnées est ajoutée pour indiquer à Linkerd d’injecter un conteneur de proxy side-car dans le pod lorsqu’il est créé.</span><span class="sxs-lookup"><span data-stu-id="3c560-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="3c560-150">Il est également possible de diriger `linkerd inject` `kubectl` directement la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="3c560-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="3c560-151">Les commandes suivantes fonctionnent dans PowerShell ou dans n’importe quel shell Linux.</span><span class="sxs-lookup"><span data-stu-id="3c560-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="3c560-152">Inspecter les services dans le tableau de bord Linkerd</span><span class="sxs-lookup"><span data-stu-id="3c560-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="3c560-153">Lancez le tableau de bord Linkerd `linkerd` à l’aide de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="3c560-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="3c560-154">Le tableau de bord fournit des informations détaillées sur tous les services qui sont connectés à la maille.</span><span class="sxs-lookup"><span data-stu-id="3c560-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Tableau de bord Linkerd présentant les applications StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="3c560-156">Si vous augmentez le nombre de réplicas du service StockData gRPC comme indiqué dans l’exemple suivant, et actualisez la page StockWeb dans le navigateur, vous devriez voir une combinaison d’ID dans la colonne serveur, indiquant que les demandes sont servies par toutes les instances disponibles .</span><span class="sxs-lookup"><span data-stu-id="3c560-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

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
><span data-ttu-id="3c560-157">[Précédent](kubernetes.md)
>[Suivant](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="3c560-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
