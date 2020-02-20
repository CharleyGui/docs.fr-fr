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
# <a name="service-meshes"></a><span data-ttu-id="d0b8f-103">Maillages de service</span><span class="sxs-lookup"><span data-stu-id="d0b8f-103">Service meshes</span></span>

<span data-ttu-id="d0b8f-104">Une maille de service est un composant d’infrastructure qui prend le contrôle des demandes de service de routage au sein d’un réseau.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="d0b8f-105">Les maillages de service peuvent gérer tous les types de problèmes au niveau du réseau au sein d’un cluster Kubernetes, notamment :</span><span class="sxs-lookup"><span data-stu-id="d0b8f-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="d0b8f-106">Détection du service</span><span class="sxs-lookup"><span data-stu-id="d0b8f-106">Service discovery</span></span>
- <span data-ttu-id="d0b8f-107">Équilibrage de la charge</span><span class="sxs-lookup"><span data-stu-id="d0b8f-107">Load balancing</span></span>
- <span data-ttu-id="d0b8f-108">Tolérance de panne</span><span class="sxs-lookup"><span data-stu-id="d0b8f-108">Fault tolerance</span></span>
- <span data-ttu-id="d0b8f-109">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="d0b8f-109">Encryption</span></span>
- <span data-ttu-id="d0b8f-110">Surveillance</span><span class="sxs-lookup"><span data-stu-id="d0b8f-110">Monitoring</span></span>

<span data-ttu-id="d0b8f-111">Les maillages de service Kubernetes fonctionnent en ajoutant un conteneur supplémentaire, appelé *proxy de side-car*, à chaque Pod inclus dans la maille.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="d0b8f-112">Le proxy prend en charge la gestion de toutes les demandes réseau entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="d0b8f-113">Vous pouvez alors conserver la configuration et la gestion des aspects de la mise en réseau séparément des conteneurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-113">You can then keep configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="d0b8f-114">Dans de nombreux cas, cette séparation ne nécessite aucune modification du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="d0b8f-115">Dans l' [exemple du chapitre précédent](kubernetes.md#test-the-application), les demandes gRPC de l’application Web étaient toutes acheminées vers une seule instance du service gRPC.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="d0b8f-116">Cela est dû au fait que le nom d’hôte du service est résolu en une adresse IP et que cette adresse IP est mise en cache pendant la durée de vie de l’instance `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="d0b8f-117">Il peut être possible de contourner ce risque en gérant manuellement les recherches DNS ou en créant plusieurs clients.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-117">It might be possible to work around this by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="d0b8f-118">Toutefois, cette solution de contournement compliquerait le code de l’application sans ajouter de valeur commerciale ou client.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="d0b8f-119">Lorsque vous utilisez un maillage de service, les demandes du conteneur d’application sont envoyées au proxy side-car.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="d0b8f-120">Le proxy side-car peut ensuite les distribuer intelligemment sur toutes les instances de l’autre service.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="d0b8f-121">La maille peut également :</span><span class="sxs-lookup"><span data-stu-id="d0b8f-121">The mesh can also:</span></span>

- <span data-ttu-id="d0b8f-122">Réagir en toute transparence aux défaillances des instances individuelles d’un service.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="d0b8f-123">Gérez la sémantique des nouvelles tentatives pour les échecs d’appels ou de délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="d0b8f-124">Rediriger les demandes ayant échoué vers une autre instance sans revenir à l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="d0b8f-125">La capture d’écran suivante montre l’application StockWeb en cours d’exécution avec la maille de service Linkerd.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="d0b8f-126">Aucune modification n’est apportée au code de l’application, et l’image de l’Ancreur n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="d0b8f-127">La seule modification requise était l’ajout d’une annotation au déploiement dans les fichiers YAML pour les services `stockdata` et `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb avec maillage de service](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="d0b8f-129">Vous pouvez voir à partir de la colonne de **serveur** que les demandes de l’application StockWeb ont été routées vers les deux réplicas du service stockdata, bien qu’elles proviennent d’une instance de `HttpClient` unique dans le code de l’application.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="d0b8f-130">En fait, si vous examinez le code, vous verrez que toutes les demandes 100 au service StockData sont effectuées simultanément à l’aide de la même instance de `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="d0b8f-131">Avec la maille de service, ces demandes sont équilibrées entre plusieurs instances de service disponibles.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="d0b8f-132">Les maillages de service s’appliquent uniquement au trafic au sein d’un cluster.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="d0b8f-133">Pour les clients externes, consultez le chapitre suivant, [équilibrage de charge](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="d0b8f-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="d0b8f-134">Options de maillage de service</span><span class="sxs-lookup"><span data-stu-id="d0b8f-134">Service mesh options</span></span>

<span data-ttu-id="d0b8f-135">Trois implémentations de maille de service à usage général peuvent actuellement être utilisées avec Kubernetes : [Istio](https://istio.io), [Linkerd](https://linkerd.io)et [consulaire Connect](https://consul.io/mesh.html).</span><span class="sxs-lookup"><span data-stu-id="d0b8f-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="d0b8f-136">Les trois fournissent le routage/proxy des demandes, le chiffrement du trafic, la résilience, l’authentification hôte à hôte et le contrôle du trafic.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="d0b8f-137">Le choix d’un maillage de service dépend de plusieurs facteurs :</span><span class="sxs-lookup"><span data-stu-id="d0b8f-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="d0b8f-138">Exigences spécifiques de l’Organisation concernant les coûts, la conformité, les plans de support payants, etc.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="d0b8f-139">La nature du cluster, sa taille, le nombre de services déployés et le volume de trafic au sein du réseau du cluster.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="d0b8f-140">Facilité de déploiement et de gestion de la maille et de son utilisation avec les services.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="d0b8f-141">Exemple : Ajouter Linkerd à un déploiement</span><span class="sxs-lookup"><span data-stu-id="d0b8f-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="d0b8f-142">Dans cet exemple, vous allez apprendre à utiliser la maille du service Linkerd avec l’application *StockKube* de [la section précédente](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="d0b8f-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="d0b8f-143">Pour suivre cet exemple, vous devez [installer l’interface CLI Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="d0b8f-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="d0b8f-144">Vous pouvez télécharger les fichiers binaires Windows à partir de la section qui répertorie les versions de GitHub.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="d0b8f-145">Veillez à utiliser la version *stable* la plus récente et non une des versions de périphérie.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="d0b8f-146">Une fois l’interface CLI Linkerd installée, suivez les instructions [prise en main](https://linkerd.io/2/getting-started/index.html) pour installer les composants Linkerd sur votre cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="d0b8f-147">Les instructions sont simples et l’installation ne doit prendre que quelques minutes sur une instance Kubernetes locale.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-147">The instructions are straightforward, and installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="d0b8f-148">Ajouter Linkerd à des déploiements Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d0b8f-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="d0b8f-149">L’interface CLI Linkerd fournit une commande `inject` pour ajouter les sections et les propriétés nécessaires aux fichiers Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="d0b8f-150">Vous pouvez exécuter la commande et écrire la sortie dans un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="d0b8f-151">Vous pouvez inspecter les nouveaux fichiers pour voir les modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="d0b8f-152">Pour les objets de déploiement, une annotation de métadonnées est ajoutée pour indiquer à Linkerd d’injecter un conteneur de proxy side-car dans le pod lorsqu’il est créé.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="d0b8f-153">Il est également possible de diriger la sortie de la commande `linkerd inject` vers `kubectl` directement.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="d0b8f-154">Les commandes suivantes fonctionnent dans PowerShell ou dans n’importe quel shell Linux.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="d0b8f-155">Inspecter les services dans le tableau de bord Linkerd</span><span class="sxs-lookup"><span data-stu-id="d0b8f-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="d0b8f-156">Ouvrez le tableau de bord Linkerd à l’aide de l’interface de commande `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="d0b8f-157">Le tableau de bord fournit des informations détaillées sur tous les services qui sont connectés à la maille.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Tableau de bord Linkerd présentant les applications StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="d0b8f-159">Si vous augmentez le nombre de réplicas du service StockData gRPC comme indiqué dans l’exemple suivant, et actualisez la page StockWeb dans le navigateur, vous devriez voir une combinaison d’ID dans la colonne **serveur** .</span><span class="sxs-lookup"><span data-stu-id="d0b8f-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="d0b8f-160">Cette combinaison indique que toutes les instances disponibles servent les demandes.</span><span class="sxs-lookup"><span data-stu-id="d0b8f-160">This mix indicates that all the available instances are serving requests.</span></span>

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
><span data-ttu-id="d0b8f-161">[Précédent](kubernetes.md)
>[Suivant](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="d0b8f-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
