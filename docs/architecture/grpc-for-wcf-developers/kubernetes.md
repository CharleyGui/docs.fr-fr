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
# <a name="kubernetes"></a><span data-ttu-id="5b8e0-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5b8e0-103">Kubernetes</span></span>

<span data-ttu-id="5b8e0-104">Bien qu’il soit possible d’exécuter des conteneurs manuellement sur des hôtes de l’arrimeur, il est préférable d’utiliser un moteur d’orchestration de conteneur pour gérer plusieurs instances exécutées sur plusieurs serveurs d’un cluster dans le cas d’un système de production fiable.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="5b8e0-105">Plusieurs moteurs d’orchestration de conteneur sont disponibles, y compris Kubernetes, Dockr essaim et Apache méson.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="5b8e0-106">Mais de ces moteurs, Kubernetes est loin et éloigné le plus couramment utilisé. il sera donc axé sur ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="5b8e0-107">Kubernetes comprend les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="5b8e0-108">La **planification** exécute des conteneurs sur plusieurs nœuds au sein d’un cluster, en garantissant une utilisation équilibrée de la ressource disponible, en conservant les conteneurs en cours d’exécution en cas de panne et en gérant les mises à jour propagées vers les nouvelles versions d’images ou les nouvelles configurations.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="5b8e0-109">Les **contrôles d’intégrité** analysent les conteneurs pour garantir un service continu.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="5b8e0-110">La **découverte du service de & DNS** gère le routage entre les services au sein d’un cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="5b8e0-111">L’entrée **expose les** services sélectionnés en externe et fournit généralement un équilibrage de la charge entre les instances de ces services.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="5b8e0-112">La **gestion des ressources** associe des ressources externes telles que le stockage à des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="5b8e0-113">Ce chapitre explique en détail comment déployer un service ASP.NET Core gRPC et un site Web qui consomme le service dans un cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="5b8e0-114">L’exemple d’application utilisé est disponible dans le référentiel [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="5b8e0-115">Terminologie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5b8e0-115">Kubernetes terminology</span></span>

<span data-ttu-id="5b8e0-116">Kubernetes utilise la *configuration d’état souhaité*: l’API est utilisée pour décrire des objets tels que les *Pod*, les *déploiements* et les *services*, et le *plan de contrôle* prend en charge l’implémentation de l’état souhaité sur tous les *nœuds* d’un *cluster*.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="5b8e0-117">Un cluster Kubernetes possède un nœud *principal* qui exécute l' *API Kubernetes*, que vous pouvez communiquer avec par programmation ou à l’aide de l' `kubectl` outil en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="5b8e0-118">`kubectl` peut créer et gérer des objets à l’aide d’arguments de ligne de commande, mais il fonctionne mieux avec les fichiers YAML qui contiennent des données de déclaration pour les objets Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="5b8e0-119">Fichiers YAML Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5b8e0-119">Kubernetes YAML files</span></span>

<span data-ttu-id="5b8e0-120">Chaque fichier Kubernetes YAML aura au moins trois propriétés de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="5b8e0-121">La `apiVersion` propriété est utilisée pour spécifier la version (et l’API) à laquelle le fichier est destiné.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="5b8e0-122">La `kind` propriété spécifie le type d’objet représenté par le YAML.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="5b8e0-123">La `metadata` propriété contient des propriétés d’objet telles que `name` , `namespace` et `labels` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="5b8e0-124">La plupart des fichiers YAML Kubernetes comporteront également une `spec` section décrivant les ressources et la configuration nécessaires à la création de l’objet.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="5b8e0-125">Pods</span><span class="sxs-lookup"><span data-stu-id="5b8e0-125">Pods</span></span>

<span data-ttu-id="5b8e0-126">Les POD sont les unités d’exécution de base dans Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="5b8e0-127">Ils peuvent exécuter plusieurs conteneurs, mais ils sont également utilisés pour exécuter des conteneurs uniques.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="5b8e0-128">Le pod comprend également toutes les ressources de stockage requises par les conteneurs, ainsi que l’adresse IP du réseau.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="5b8e0-129">Services</span><span class="sxs-lookup"><span data-stu-id="5b8e0-129">Services</span></span>

<span data-ttu-id="5b8e0-130">Les services sont des méta-objets qui décrivent des gousses (ou ensembles de Pod) et offrent un moyen d’y accéder au sein du cluster, comme le mappage d’un nom de service à un ensemble d’adresses IP Pod à l’aide du service DNS de cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="5b8e0-131">Déploiements</span><span class="sxs-lookup"><span data-stu-id="5b8e0-131">Deployments</span></span>

<span data-ttu-id="5b8e0-132">Les déploiements sont les objets d' *État souhaités* pour les pod.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="5b8e0-133">Si vous créez une Pod manuellement, elle ne sera pas redémarrée lorsqu’elle se terminera.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="5b8e0-134">Les déploiements sont utilisés pour indiquer au cluster les Pod, ainsi que le nombre de réplicas de ces gousses, qui doivent être exécutés à l’heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="5b8e0-135">Autres objets</span><span class="sxs-lookup"><span data-stu-id="5b8e0-135">Other objects</span></span>

<span data-ttu-id="5b8e0-136">Les Pod, les services et les déploiements représentent seulement trois des types d’objets les plus basiques.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="5b8e0-137">Il existe des dizaines d’autres types d’objets qui sont gérés par les clusters Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="5b8e0-138">Pour plus d’informations, consultez la documentation sur les [concepts de Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="5b8e0-139">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="5b8e0-139">Namespaces</span></span>

<span data-ttu-id="5b8e0-140">Les clusters Kubernetes sont conçus pour évoluer vers des centaines ou des milliers de nœuds et pour exécuter des nombres de services similaires.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="5b8e0-141">Pour éviter les conflits entre les noms d’objets, les espaces de noms sont utilisés pour regrouper des objets dans le cadre d’applications plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="5b8e0-142">Les services de Kubernetes s’exécutent dans un `default` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="5b8e0-143">Tous les objets utilisateur doivent être créés dans leurs propres espaces de noms pour éviter les conflits potentiels avec les objets par défaut ou d’autres locataires dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="5b8e0-144">Prise en main de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5b8e0-144">Get started with Kubernetes</span></span>

<span data-ttu-id="5b8e0-145">Si vous exécutez le Bureau de la station d’accueil pour Windows ou le Bureau de station d’accueil pour Mac, Kubernetes est déjà disponible.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="5b8e0-146">Il suffit de l’activer dans la section **Kubernetes** de la fenêtre **paramètres** :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Activer Kubernetes dans le Bureau de l’ancrage](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

<span data-ttu-id="5b8e0-148">Pour exécuter un cluster Kubernetes local sur Linux, envisagez [minikube](https://github.com/kubernetes/minikube)ou [MicroK8s](https://microk8s.io/) si votre distribution Linux prend en charge les [instantanés](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="5b8e0-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="5b8e0-149">Pour confirmer que votre cluster est en cours d’exécution et accessible, exécutez la `kubectl version` commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="5b8e0-150">Dans cet exemple, l' `kubectl` interface CLI et le serveur Kubernetes exécutent la version 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="5b8e0-151">Chaque version de `kubectl` est censée prendre en charge la version précédente et la version suivante du serveur, donc `kubectl` 1,14 doit également fonctionner avec les versions de serveur 1,13 et 1,15.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="5b8e0-152">Exécuter des services sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5b8e0-152">Run services on Kubernetes</span></span>

<span data-ttu-id="5b8e0-153">L’exemple d’application possède un `kube` répertoire qui contient trois fichiers YAML.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="5b8e0-154">Le `namespace.yml` fichier déclare un espace de noms personnalisé : `stocks` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="5b8e0-155">Le `stockdata.yml` fichier déclare le déploiement et le service pour l’application gRPC, et le `stockweb.yml` fichier déclare le déploiement et le service pour une application web ASP.net Core 5,0 MVC qui utilise le service gRPC.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 5.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="5b8e0-156">Pour utiliser un `YAML` fichier avec `kubectl` , exécutez la `apply -f` commande :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="5b8e0-157">La `apply` commande vérifie la validité du fichier YAML et affiche toutes les erreurs reçues de l’API, mais n’attend pas que tous les objets déclarés dans le fichier aient été créés, car cette étape peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this step can take some time.</span></span> <span data-ttu-id="5b8e0-158">Utilisez la `kubectl get` commande avec les types d’objets appropriés pour vérifier la création d’objets dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="5b8e0-159">Déclaration d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="5b8e0-159">The namespace declaration</span></span>

<span data-ttu-id="5b8e0-160">La déclaration d’espace de noms est simple et requiert uniquement l’affectation d’un `name` :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="5b8e0-161">Utilisez `kubectl` pour appliquer le `namespace.yml` fichier et confirmer que l’espace de noms a été créé avec succès :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="5b8e0-162">L’application StockData</span><span class="sxs-lookup"><span data-stu-id="5b8e0-162">The StockData application</span></span>

<span data-ttu-id="5b8e0-163">Le `stockdata.yml` fichier déclare deux objets : un déploiement et un service.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="5b8e0-164">Le déploiement StockData</span><span class="sxs-lookup"><span data-stu-id="5b8e0-164">The StockData Deployment</span></span>

<span data-ttu-id="5b8e0-165">La partie déploiement du fichier YAML fournit le `spec` pour le déploiement lui-même, y compris le nombre de réplicas requis et un `template` pour les objets Pod à créer et gérer par le déploiement.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="5b8e0-166">Notez que les objets de déploiement sont gérés par l' `apps` API, comme spécifié dans `apiVersion` , plutôt que l’API Kubernetes principale.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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

<span data-ttu-id="5b8e0-167">La `spec.selector` propriété est utilisée pour faire correspondre les pod en cours d’exécution au déploiement.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="5b8e0-168">La propriété du Pod `metadata.labels` doit correspondre à la `matchLabels` propriété, sans quoi l’appel de l’API échoue.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="5b8e0-169">La `template.spec` section déclare le conteneur à exécuter.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="5b8e0-170">Lorsque vous travaillez avec un cluster Kubernetes local, tel que celui fourni par le Bureau de l’ordinateur de bureau de station d’accueil, vous pouvez spécifier des images qui ont été générées localement tant qu’elles ont une balise de version.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b8e0-171">Par défaut, Kubernetes recherche et tente d’extraire une nouvelle image.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="5b8e0-172">S’il ne peut pas trouver l’image dans l’un de ses référentiels connus, la création du Pod échoue.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="5b8e0-173">Pour travailler avec des images locales, affectez la valeur `imagePullPolicy` à `Never` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="5b8e0-174">La `ports` propriété spécifie les ports de conteneur qui doivent être publiés sur le POD.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="5b8e0-175">L' `stockservice` image exécute le service sur le port http standard, le port 80 est donc publié.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="5b8e0-176">La `resources` section applique des limites de ressources au conteneur en cours d’exécution dans le POD.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="5b8e0-177">C’est une bonne pratique, car elle empêche un pod individuel de consommer tout le processeur ou la mémoire disponible sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="5b8e0-178">ASP.NET Core 5,0 a été optimisé et réglé pour s’exécuter dans des conteneurs à ressources limitées.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-178">ASP.NET Core 5.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="5b8e0-179">L' `dotnet/core/aspnet` image de l’ancreur définit une variable d’environnement pour indiquer à l' `dotnet` exécution qu’il se trouve dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="5b8e0-180">Service StockData</span><span class="sxs-lookup"><span data-stu-id="5b8e0-180">The StockData Service</span></span>

<span data-ttu-id="5b8e0-181">La partie service du fichier YAML déclare le service qui fournit l’accès aux Pod au sein du cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

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

<span data-ttu-id="5b8e0-182">Le service `spec` utilise la `selector` propriété pour faire correspondre l’exécution `Pods` , dans ce cas, en recherchant les Pod qui ont une étiquette `run: stockdata` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="5b8e0-183">Le spécifié `port` sur les Pod correspondants est publié par le service nommé.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="5b8e0-184">D’autres pod en cours d’exécution dans l' `stocks` espace de noms peuvent accéder à http sur ce service en utilisant `http://stockdata` comme adresse.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="5b8e0-185">Les pod en cours d’exécution dans d’autres espaces de noms peuvent utiliser le `http://stockdata.stocks` nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="5b8e0-186">Vous pouvez contrôler l’accès au service entre espaces de noms à l’aide de [stratégies réseau](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="5b8e0-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="5b8e0-187">Déployer l’application StockData</span><span class="sxs-lookup"><span data-stu-id="5b8e0-187">Deploy the StockData application</span></span>

<span data-ttu-id="5b8e0-188">Utilisez `kubectl` pour appliquer le `stockdata.yml` fichier et confirmer que le déploiement et le service ont été créés :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

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

### <a name="the-stockweb-application"></a><span data-ttu-id="5b8e0-189">L’application StockWeb</span><span class="sxs-lookup"><span data-stu-id="5b8e0-189">The StockWeb application</span></span>

<span data-ttu-id="5b8e0-190">Le `stockweb.yml` fichier déclare le déploiement et le service pour l’application MVC.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

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

#### <a name="environment-variables"></a><span data-ttu-id="5b8e0-191">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="5b8e0-191">Environment variables</span></span>

<span data-ttu-id="5b8e0-192">La `env` section de l’objet de déploiement spécifie les variables d’environnement à définir dans le conteneur qui exécute les `stockweb:1.0.0` images.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="5b8e0-193">La **`StockData__Address`** variable d’environnement est mappée au `StockData:Address` paramètre de configuration grâce au fournisseur de configuration EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="5b8e0-194">Ce paramètre utilise des traits de soulignement doubles entre les noms et des sections distinctes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="5b8e0-195">L’adresse utilise le nom de service du `stockdata` service, qui s’exécute dans le même espace de noms Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="5b8e0-196">La **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** variable d’environnement définit un <xref:System.AppContext> commutateur qui autorise les connexions http/2 non chiffrées pour <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="5b8e0-197">Cette variable d’environnement fait la même chose que la définition du commutateur dans le code, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="5b8e0-198">Si vous utilisez une variable d’environnement pour le commutateur, vous pouvez facilement modifier le contexte en fonction du contexte dans lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="5b8e0-199">Types de service</span><span class="sxs-lookup"><span data-stu-id="5b8e0-199">Service types</span></span>

<span data-ttu-id="5b8e0-200">La `type: NodePort` propriété est utilisée pour rendre l’application Web accessible à partir de l’extérieur du cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="5b8e0-201">Ce type de propriété force Kubernetes à publier le port 80 sur le service sur un port arbitraire sur les sockets réseau externes du cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="5b8e0-202">Vous pouvez trouver le port attribué à l’aide de la `kubectl get service` commande.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="5b8e0-203">Le `stockdata` service ne doit pas être accessible depuis l’extérieur du cluster, donc il utilise le type par défaut, `ClusterIP` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="5b8e0-204">Les systèmes de production utiliseront très probablement un équilibreur de charge intégré pour exposer les applications publiques aux consommateurs externes.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="5b8e0-205">Les services exposés de cette manière doivent utiliser le `LoadBalancer` type.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="5b8e0-206">Pour plus d’informations sur les types de services, consultez la documentation des [services de publication Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="5b8e0-207">Déployer l’application StockWeb</span><span class="sxs-lookup"><span data-stu-id="5b8e0-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="5b8e0-208">Utilisez `kubectl` pour appliquer le `stockweb.yml` fichier et confirmer que le déploiement et le service ont été créés :</span><span class="sxs-lookup"><span data-stu-id="5b8e0-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

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

<span data-ttu-id="5b8e0-209">La sortie de la `get service` commande indique que le port http a été publié sur `32564` le port sur le réseau externe.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-209">The output of the `get service` command shows that the HTTP port has been published to port `32564` on the external network.</span></span> <span data-ttu-id="5b8e0-210">Pour le Bureau de l’arrimeur, cette adresse IP sera localhost.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-210">For Docker Desktop, this IP address will be localhost.</span></span> <span data-ttu-id="5b8e0-211">Vous pouvez accéder à l’application en accédant à `http://localhost:32564` .</span><span class="sxs-lookup"><span data-stu-id="5b8e0-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="5b8e0-212">Tester l’application</span><span class="sxs-lookup"><span data-stu-id="5b8e0-212">Test the application</span></span>

<span data-ttu-id="5b8e0-213">L’application StockWeb affiche une liste des actions NASDAQ récupérées à partir d’un service de requête-réponse simple.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="5b8e0-214">Pour cette démonstration, chaque ligne affiche également l’ID unique de l’instance de service qui l’a retournée.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![Capture d’écran StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="5b8e0-216">Si le nombre de réplicas du `stockdata` service a été augmenté, vous pouvez vous attendre à ce que la valeur du **serveur** passe d’une ligne à l’autres, mais en fait, tous les enregistrements 100 sont toujours retournés à partir de la même instance.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="5b8e0-217">Si vous actualisez la page toutes les quelques secondes, l’ID du serveur reste le même.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="5b8e0-218">Pourquoi cela se produit-il ?</span><span class="sxs-lookup"><span data-stu-id="5b8e0-218">Why does this happen?</span></span> <span data-ttu-id="5b8e0-219">Il existe deux facteurs à lire ici.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-219">There are two factors at play here.</span></span>

<span data-ttu-id="5b8e0-220">Tout d’abord, le système de détection du service Kubernetes utilise l’équilibrage de charge par tourniquet (Round Robin) par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="5b8e0-221">La première fois que le serveur DNS est interrogé, il retourne la première adresse IP correspondante pour le service.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="5b8e0-222">La prochaine fois, elle renverra l’adresse IP suivante dans la liste, et ainsi de suite, jusqu’à la fin.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="5b8e0-223">À ce stade, il repasse au début.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-223">At that point, it loops back to the start.</span></span>

<span data-ttu-id="5b8e0-224">Deuxièmement, le `HttpClient` utilisé pour le client gRPC de l’application StockWeb est créé et géré par l' [ASP.net Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), et une seule instance de ce client est utilisée pour chaque appel à la page.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="5b8e0-225">Le client n’effectue qu’une seule recherche DNS, donc toutes les demandes sont acheminées vers la même adresse IP.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="5b8e0-226">Et étant donné que le `HttpClientHandler` est mis en cache pour des raisons de performances, plusieurs demandes en succession rapide utilisent *toutes* la même adresse IP, jusqu’à ce que l’entrée DNS mise en cache expire ou que l’instance de gestionnaire soit supprimée pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="5b8e0-227">Le résultat est que par défaut, les demandes adressées à un service gRPC ne sont pas équilibrées sur toutes les instances de ce service dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="5b8e0-228">Les différents consommateurs utilisent des instances différentes, mais cela ne garantit pas une bonne distribution des demandes ou une utilisation équilibrée des ressources.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="5b8e0-229">Le chapitre suivant, [maillages de service](service-mesh.md), traite ce problème.</span><span class="sxs-lookup"><span data-stu-id="5b8e0-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5b8e0-230">[Précédent](docker.md) 
> [Suivant](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="5b8e0-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
