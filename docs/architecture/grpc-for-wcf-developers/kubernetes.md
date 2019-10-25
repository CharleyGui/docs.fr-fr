---
title: Kubernetes-gRPC pour les développeurs WCF
description: Exécution des services ASP.NET Core gRPC dans un cluster Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 819c761a7a55485612b7fb0c8b392971751d8724
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846638"
---
# <a name="kubernetes"></a><span data-ttu-id="0a632-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a632-103">Kubernetes</span></span>

<span data-ttu-id="0a632-104">Bien qu’il soit possible d’exécuter des conteneurs manuellement sur les hôtes de l’ordinateur de production, il est préférable d’utiliser un moteur d’orchestration de conteneur pour gérer plusieurs instances exécutées sur plusieurs serveurs d’un cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's preferable to use a Container Orchestration Engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="0a632-105">Plusieurs moteurs d’orchestration de conteneur sont disponibles, y compris Kubernetes, Dockr essaim et Apache méson.</span><span class="sxs-lookup"><span data-stu-id="0a632-105">There are various Container Orchestration Engines available, including Kubernetes, Docker Swarm and Apache Mesos.</span></span> <span data-ttu-id="0a632-106">Mais de ces moteurs, Kubernetes est loin et éloigné le plus couramment utilisé. il sera donc axé sur ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="0a632-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="0a632-107">Kubernetes comprend les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a632-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="0a632-108">La **planification** exécute des conteneurs sur plusieurs nœuds au sein d’un cluster, en garantissant une utilisation équilibrée de la ressource disponible, en conservant les conteneurs en cours d’exécution en cas de panne et en gérant les mises à jour propagées vers les nouvelles versions d’images ou les nouvelles configurations.</span><span class="sxs-lookup"><span data-stu-id="0a632-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="0a632-109">Les **contrôles d’intégrité** analysent les conteneurs pour garantir un service continu.</span><span class="sxs-lookup"><span data-stu-id="0a632-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="0a632-110">La **découverte du service de & DNS** gère le routage entre les services au sein d’un cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="0a632-111">L’entrée **expose les** services sélectionnés en externe et fournit généralement un équilibrage de la charge entre les instances de ces services.</span><span class="sxs-lookup"><span data-stu-id="0a632-111">**Ingress** exposes selected services externally, and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="0a632-112">La **gestion des ressources** attache des ressources externes, telles que le stockage, aux conteneurs.</span><span class="sxs-lookup"><span data-stu-id="0a632-112">**Resource management** attaches external resources such as storage to containers.</span></span>

<span data-ttu-id="0a632-113">Ce chapitre explique en détail comment déployer un service ASP.NET Core gRPC et un site Web qui consomme le service dans un cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0a632-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="0a632-114">L’exemple d’application utilisé est disponible dans le référentiel [dotnet-architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub,</span><span class="sxs-lookup"><span data-stu-id="0a632-114">The sample application used is available from on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub,</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="0a632-115">Terminologie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a632-115">Kubernetes terminology</span></span>

<span data-ttu-id="0a632-116">Kubernetes utilise *la configuration d’état souhaité*: l’API est utilisée pour décrire des objets tels que les *Pod*, les *déploiements* et les *services*, et le *plan de contrôle* prend en charge l’implémentation de l’état souhaité sur tous les *nœuds.* dans un *cluster*.</span><span class="sxs-lookup"><span data-stu-id="0a632-116">Kubernetes uses *desired state configuration*: the API is used to describe objects such as *Pods*, *Deployments* and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="0a632-117">Un cluster Kubernetes possède un nœud *principal* qui exécute l' *API Kubernetes*, qui peut être communiquée par programmation ou à l’aide de l’outil de ligne de commande `kubectl`.</span><span class="sxs-lookup"><span data-stu-id="0a632-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which can be communicated with programmatically or using the `kubectl` command-line tool.</span></span> <span data-ttu-id="0a632-118">`kubectl` pouvez créer et gérer des objets à l’aide d’arguments de ligne de commande, mais fonctionne mieux avec les fichiers YAML qui contiennent des données de déclaration pour les objets Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0a632-118">`kubectl` can create and manage objects using command-line arguments, but works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="0a632-119">Fichiers YAML Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a632-119">Kubernetes YAML files</span></span>

<span data-ttu-id="0a632-120">Chaque fichier Kubernetes YAML aura au moins trois propriétés de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="0a632-120">Every Kubernetes YAML file will have at least three top-level properties.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="0a632-121">La propriété `apiVersion` est utilisée pour spécifier la version (et l’API) à laquelle le fichier est destiné.</span><span class="sxs-lookup"><span data-stu-id="0a632-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="0a632-122">La propriété `kind` spécifie le type d’objet représenté par le YAML.</span><span class="sxs-lookup"><span data-stu-id="0a632-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="0a632-123">La propriété `metadata` contient des propriétés d’objet telles que `name`, `namespace` ou `labels`.</span><span class="sxs-lookup"><span data-stu-id="0a632-123">The `metadata` property contains object properties such as `name`, `namespace`, or `labels`.</span></span>

<span data-ttu-id="0a632-124">La plupart des fichiers YAML Kubernetes comporteront également une section `spec` qui décrit les ressources et la configuration nécessaires à la création de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0a632-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="0a632-125">Boîtier</span><span class="sxs-lookup"><span data-stu-id="0a632-125">Pods</span></span>

<span data-ttu-id="0a632-126">Les POD sont les unités d’exécution de base dans Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0a632-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="0a632-127">Ils peuvent exécuter plusieurs conteneurs, mais ils sont également utilisés pour exécuter des conteneurs uniques.</span><span class="sxs-lookup"><span data-stu-id="0a632-127">They can run multiple containers, but are also used to run single containers.</span></span> <span data-ttu-id="0a632-128">Le pod comprend également toutes les ressources de stockage requises par le ou les conteneurs, ainsi que l’adresse IP du réseau.</span><span class="sxs-lookup"><span data-stu-id="0a632-128">The pod also includes any storage resources required by the container(s), and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="0a632-129">Services</span><span class="sxs-lookup"><span data-stu-id="0a632-129">Services</span></span>

<span data-ttu-id="0a632-130">Les services sont des méta-objets qui décrivent des gousses (ou ensembles de Pod) et offrent un moyen d’y accéder au sein du cluster, comme le mappage d’un nom de service à un ensemble d’adresses IP Pod à l’aide du service DNS de cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-130">Services are meta-objects that describe pods (or sets of pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="0a632-131">Déploiements</span><span class="sxs-lookup"><span data-stu-id="0a632-131">Deployments</span></span>

<span data-ttu-id="0a632-132">Les déploiements sont les objets d' *État décrits* pour les pod.</span><span class="sxs-lookup"><span data-stu-id="0a632-132">Deployments are the *described state* objects for Pods.</span></span> <span data-ttu-id="0a632-133">Si vous créez un pod manuellement, lorsqu’il s’arrête, il ne sera pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="0a632-133">If you create a Pod manually, when it terminates it won't be restarted.</span></span> <span data-ttu-id="0a632-134">Les déploiements sont utilisés pour indiquer au cluster les Pod, ainsi que le nombre de réplicas de ces gousses, qui doivent être exécutés à l’heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="0a632-134">Deployments are used to tell the cluster which pods, and how many replicas of those pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="0a632-135">Autres objets</span><span class="sxs-lookup"><span data-stu-id="0a632-135">Other objects</span></span>

<span data-ttu-id="0a632-136">Les Pod, les services et les déploiements représentent seulement trois des types d’objets les plus basiques.</span><span class="sxs-lookup"><span data-stu-id="0a632-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="0a632-137">Il existe des dizaines d’autres types d’objets qui sont gérés par un cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0a632-137">There are dozens of other types of object that are managed by a Kubernetes cluster.</span></span> <span data-ttu-id="0a632-138">Pour plus d’informations, consultez la documentation sur les [concepts de Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="0a632-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="0a632-139">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="0a632-139">Namespaces</span></span>

<span data-ttu-id="0a632-140">Les clusters Kubernetes sont conçus pour s’adapter à des centaines voire des milliers de nœuds et exécuter des nombres de services similaires.</span><span class="sxs-lookup"><span data-stu-id="0a632-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes, and run similar numbers of services.</span></span> <span data-ttu-id="0a632-141">Pour éviter les conflits entre les noms d’objets, les espaces de noms sont utilisés pour regrouper des objets dans le cadre d’applications plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="0a632-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="0a632-142">Les Kubernetes propres services s’exécutent dans un espace de noms `default`.</span><span class="sxs-lookup"><span data-stu-id="0a632-142">Kubernetes own services run in a `default` namespace.</span></span> <span data-ttu-id="0a632-143">Tous les objets utilisateur doivent être créés dans leurs propres espaces de noms pour éviter les conflits potentiels avec les objets par défaut ou d’autres locataires dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="0a632-144">Prise en main de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a632-144">Get started with Kubernetes</span></span>

<span data-ttu-id="0a632-145">Si vous exécutez Desktop Dockr pour Windows ou macOS, Kubernetes est déjà disponible.</span><span class="sxs-lookup"><span data-stu-id="0a632-145">If you're running Docker Desktop for Windows or macOS, Kubernetes is already available.</span></span> <span data-ttu-id="0a632-146">Il suffit de l’activer dans la section Kubernetes de la fenêtre Paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a632-146">Just enable it in the Kubernetes section of the Settings window.</span></span>

![Activer Kubernetes dans le Bureau de l’ancrage](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="0a632-148">Pour exécuter un cluster Kubernetes local dans Linux, examinez [minikube](https://github.com/kubernetes/minikube)ou [MicroK8s](https://microk8s.io/) si votre distribution Linux prend en charge les [instantanés](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="0a632-148">To run a local Kubernetes cluster in Linux, look at [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="0a632-149">Pour vérifier que votre cluster est en cours d’exécution et accessible, exécutez la commande `kubectl version`.</span><span class="sxs-lookup"><span data-stu-id="0a632-149">To check that your cluster is running and accessible, run the `kubectl version` command.</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="0a632-150">Dans cet exemple, l’interface CLI `kubectl` et le serveur Kubernetes exécutent la version 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="0a632-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="0a632-151">Chaque version de `kubectl` est supposée prendre en charge la version précédente et la version suivante du serveur, donc `kubectl` 1,14 doit également fonctionner avec les versions de serveur 1,13 et 1,15.</span><span class="sxs-lookup"><span data-stu-id="0a632-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="0a632-152">Exécuter des services sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a632-152">Run services on Kubernetes</span></span>

<span data-ttu-id="0a632-153">L’exemple d’application possède un répertoire `kube` contenant trois fichiers YAML.</span><span class="sxs-lookup"><span data-stu-id="0a632-153">The sample application has a `kube` directory containing three YAML files.</span></span> <span data-ttu-id="0a632-154">Le fichier `namespace.yml` déclare un espace de noms personnalisé, `stocks`.</span><span class="sxs-lookup"><span data-stu-id="0a632-154">The `namespace.yml` file declares a custom namespace, `stocks`.</span></span> <span data-ttu-id="0a632-155">Le fichier `stockdata.yml` déclare le déploiement et le service pour l’application gRPC, et le fichier `stockweb.yml` déclare le déploiement et le service pour une application Web ASP.NET Core 3,0 MVC qui utilise le service gRPC.</span><span class="sxs-lookup"><span data-stu-id="0a632-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="0a632-156">Pour utiliser un fichier de `YAML` avec `kubectl`, utilisez la commande `apply -f`.</span><span class="sxs-lookup"><span data-stu-id="0a632-156">To use a `YAML` file with `kubectl`, use the `apply -f` command.</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="0a632-157">La commande `apply` vérifie la validité du fichier YAML et affiche toutes les erreurs reçues de l’API, mais n’attend pas que tous les objets déclarés dans le fichier aient été créés, car cette opération peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="0a632-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created as this can take some time.</span></span> <span data-ttu-id="0a632-158">Utilisez la commande `kubectl get` avec les types d’objets appropriés pour vérifier la création d’objets dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="0a632-159">Déclaration d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="0a632-159">The namespace declaration</span></span>

<span data-ttu-id="0a632-160">La déclaration d’espace de noms est simple et requiert uniquement l’affectation d’un `name`.</span><span class="sxs-lookup"><span data-stu-id="0a632-160">Namespace declaration is simple and requires only assigning a `name`.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="0a632-161">Utilisez `kubectl` pour appliquer le fichier `namespace.yml` et vérifier que l’espace de noms est correctement créé.</span><span class="sxs-lookup"><span data-stu-id="0a632-161">Use `kubectl` to apply the `namespace.yml` file and check the namespace is created successfully.</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="0a632-162">L’application StockData</span><span class="sxs-lookup"><span data-stu-id="0a632-162">The StockData application</span></span>

<span data-ttu-id="0a632-163">Le fichier `stockdata.yml` déclare deux objets : un déploiement et un service.</span><span class="sxs-lookup"><span data-stu-id="0a632-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="0a632-164">Le déploiement StockData</span><span class="sxs-lookup"><span data-stu-id="0a632-164">The StockData Deployment</span></span>

<span data-ttu-id="0a632-165">La partie déploiement fournit les `spec` pour le déploiement proprement dit, y compris le nombre de réplicas requis et un `template` pour les objets Pod à créer et à gérer par le déploiement.</span><span class="sxs-lookup"><span data-stu-id="0a632-165">The Deployment part provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="0a632-166">Notez que les objets de déploiement sont gérés avec l’API `apps`, comme spécifié dans `apiVersion`, plutôt que l’API Kubernetes principale.</span><span class="sxs-lookup"><span data-stu-id="0a632-166">Note that Deployment objects are managed with the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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

<span data-ttu-id="0a632-167">La propriété `spec.selector` est utilisée pour faire correspondre les pod en cours d’exécution au déploiement.</span><span class="sxs-lookup"><span data-stu-id="0a632-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="0a632-168">La propriété de `metadata.labels` Pod doit correspondre à la propriété `matchLabels` ou l’appel d’API échoue.</span><span class="sxs-lookup"><span data-stu-id="0a632-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="0a632-169">La section `template.spec` déclare le conteneur à exécuter.</span><span class="sxs-lookup"><span data-stu-id="0a632-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="0a632-170">Lorsque vous travaillez avec un cluster Kubernetes local, tel que celui fourni par le Bureau de l’ordinateur de bureau de station d’accueil, vous pouvez spécifier des images qui ont été générées localement tant qu’elles ont une balise de version.</span><span class="sxs-lookup"><span data-stu-id="0a632-170">When working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a632-171">Par défaut, Kubernetes recherche et tente d’extraire une nouvelle image.</span><span class="sxs-lookup"><span data-stu-id="0a632-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="0a632-172">S’il ne peut pas trouver l’image dans l’un de ses référentiels connus, la création du Pod échoue.</span><span class="sxs-lookup"><span data-stu-id="0a632-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="0a632-173">Pour travailler avec des images locales, définissez le `imagePullPolicy` sur `Never`.</span><span class="sxs-lookup"><span data-stu-id="0a632-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="0a632-174">La propriété `ports` spécifie les ports de conteneur qui doivent être publiés sur le POD.</span><span class="sxs-lookup"><span data-stu-id="0a632-174">The `ports` property specifies which container ports should be published on the Pod.</span></span>  <span data-ttu-id="0a632-175">L’image `stockservice` exécute le service sur le port HTTP standard, le port 80 est donc publié.</span><span class="sxs-lookup"><span data-stu-id="0a632-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="0a632-176">La section `resources` applique des limites de ressources au conteneur en cours d’exécution dans le POD.</span><span class="sxs-lookup"><span data-stu-id="0a632-176">The `resources` section applies resource limits to the container running within the pod.</span></span> <span data-ttu-id="0a632-177">C’est une bonne pratique, car elle empêche un pod individuel de consommer tout le processeur ou la mémoire disponible sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="0a632-177">This is good practice as it prevents an individual pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="0a632-178">ASP.NET Core 3,0 a été optimisé et réglé pour s’exécuter dans des conteneurs à ressources limitées, et l’image de l' `dotnet/core/aspnet` d’ancrage définit une variable d’environnement pour indiquer au runtime `dotnet` qu’il se trouve dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="0a632-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers, and the `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="0a632-179">Service StockData</span><span class="sxs-lookup"><span data-stu-id="0a632-179">The StockData Service</span></span>

<span data-ttu-id="0a632-180">La partie service du fichier YAML déclare le service qui fournit l’accès aux Pod au sein du cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-180">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

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

<span data-ttu-id="0a632-181">La spécification de service utilise la propriété `selector` pour faire correspondre les `Pods` en cours d’exécution. dans ce cas, recherchez les Pod avec une étiquette `run: stockdata`.</span><span class="sxs-lookup"><span data-stu-id="0a632-181">The Service spec uses the `selector` property to match running `Pods`, in this case looking for Pods with a label `run: stockdata`.</span></span> <span data-ttu-id="0a632-182">La `port` spécifiée sur les Pod correspondants est publiée par le service nommé.</span><span class="sxs-lookup"><span data-stu-id="0a632-182">The specified `port` on matching Pods are published by the named service.</span></span> <span data-ttu-id="0a632-183">Les autres pod en cours d’exécution dans l’espace de noms `stocks` peuvent accéder au protocole HTTP sur ce service à l’aide de `http://stockdata` comme adresse.</span><span class="sxs-lookup"><span data-stu-id="0a632-183">Other Pods running in the `stocks` namespace can access HTTP on this service using `http://stockdata` as the address.</span></span> <span data-ttu-id="0a632-184">Les pod en cours d’exécution dans d’autres espaces de noms peuvent utiliser le nom d’hôte `http://stockdata.stocks`.</span><span class="sxs-lookup"><span data-stu-id="0a632-184">Pods running in other namespaces can use the `http://stockdata.stocks` hostname.</span></span> <span data-ttu-id="0a632-185">Vous pouvez contrôler l’accès au service entre espaces de noms à l’aide de [stratégies réseau](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="0a632-185">You can control cross-namespace service access using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="0a632-186">Déployer l’application StockData</span><span class="sxs-lookup"><span data-stu-id="0a632-186">Deploy the StockData application</span></span>

<span data-ttu-id="0a632-187">Utilisez `kubectl` pour appliquer le fichier `stockdata.yml` et vérifier que le déploiement et le service ont été créés.</span><span class="sxs-lookup"><span data-stu-id="0a632-187">Use `kubectl` to apply the `stockdata.yml` file and check that the Deployment and Service were created.</span></span>

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

### <a name="the-stockweb-application"></a><span data-ttu-id="0a632-188">L’application StockWeb</span><span class="sxs-lookup"><span data-stu-id="0a632-188">The StockWeb application</span></span>

<span data-ttu-id="0a632-189">Le fichier `stockweb.yml` déclare le déploiement et le service pour l’application MVC.</span><span class="sxs-lookup"><span data-stu-id="0a632-189">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

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

#### <a name="environment-variables"></a><span data-ttu-id="0a632-190">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="0a632-190">Environment variables</span></span>

<span data-ttu-id="0a632-191">La section `env` de l’objet de déploiement spécifie les variables d’environnement à définir dans le conteneur qui exécute les images `stockweb:1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="0a632-191">The `env` section of the Deployment object specifies environment variables to be set in the container running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="0a632-192">La variable d’environnement **`StockData__Address`** est mappée au paramètre de configuration `StockData:Address` grâce au fournisseur de configuration EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="0a632-192">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="0a632-193">Ce paramètre utilise des traits de soulignement doubles entre les noms et des sections distinctes.</span><span class="sxs-lookup"><span data-stu-id="0a632-193">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="0a632-194">L’adresse utilise le nom du service `stockdata`, qui s’exécute dans le même espace de noms Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0a632-194">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="0a632-195">La variable d’environnement **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** définit un commutateur <xref:System.AppContext> qui autorise les connexions http/2 non chiffrées pour <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="0a632-195">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="0a632-196">Cette variable d’environnement est l’équivalent de la définition du commutateur dans le code, comme indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="0a632-196">This environment variable is the equivalent of setting the switch in code as shown here.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="0a632-197">L’utilisation d’une variable d’environnement pour le commutateur signifie que le paramètre peut facilement être modifié en fonction du contexte dans lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0a632-197">Using an environment variable for the switch means the setting can easily be changed depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="0a632-198">Types de service</span><span class="sxs-lookup"><span data-stu-id="0a632-198">Service types</span></span>

<span data-ttu-id="0a632-199">Pour rendre l’application Web accessible depuis l’extérieur du cluster, la propriété `type: NodePort` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0a632-199">To make the Web application accessible from outside the cluster, the `type: NodePort` property is used.</span></span> <span data-ttu-id="0a632-200">Ce type de propriété force Kubernetes à publier le port 80 sur le service sur un port arbitraire sur les sockets réseau externes du cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-200">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="0a632-201">Le port affecté peut être trouvé à l’aide de la commande `kubectl get service`.</span><span class="sxs-lookup"><span data-stu-id="0a632-201">The port assigned can be found using the `kubectl get service` command.</span></span>

<span data-ttu-id="0a632-202">Le service `stockdata` ne doit pas être accessible depuis l’extérieur du cluster, il a donc utilisé le type par défaut, `ClusterIP`.</span><span class="sxs-lookup"><span data-stu-id="0a632-202">The `stockdata` service shouldn't be accessible from outside the cluster, so it used the default type, `ClusterIP`.</span></span>

<span data-ttu-id="0a632-203">Les systèmes de production utiliseront très probablement un équilibreur de charge intégré pour exposer les applications publiques aux consommateurs externes.</span><span class="sxs-lookup"><span data-stu-id="0a632-203">Production systems will most likely use an integrated load-balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="0a632-204">Les services exposés de cette manière doivent utiliser le type de `LoadBalancer`.</span><span class="sxs-lookup"><span data-stu-id="0a632-204">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="0a632-205">Pour plus d’informations sur les types de services, consultez la documentation des [services de publication Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="0a632-205">For more information on service types, see the [Kubernetes' Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="0a632-206">Déployer l’application StockWeb</span><span class="sxs-lookup"><span data-stu-id="0a632-206">Deploy the StockWeb application</span></span>

<span data-ttu-id="0a632-207">Utilisez `kubectl` pour appliquer le fichier `stockweb.yml` et vérifier que le déploiement et le service ont été créés.</span><span class="sxs-lookup"><span data-stu-id="0a632-207">Use `kubectl` to apply the `stockweb.yml` file and check that the Deployment and Service were created.</span></span>

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

<span data-ttu-id="0a632-208">La sortie de la commande `get service` indique que le port HTTP a été publié sur le port `32564` sur le réseau externe. pour le Bureau de l’arrimeur, il s’agit de localhost.</span><span class="sxs-lookup"><span data-stu-id="0a632-208">The output from the `get service` command shows that the HTTP port has been published to port `32564` on the external network; for Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="0a632-209">Vous pouvez accéder à l’application en accédant à `http://localhost:32564`.</span><span class="sxs-lookup"><span data-stu-id="0a632-209">The application can be accessed by browsing to `http://localhost:32564`.</span></span>

### <a name="testing-the-application"></a><span data-ttu-id="0a632-210">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="0a632-210">Testing the application</span></span>

<span data-ttu-id="0a632-211">L’application StockWeb affiche une liste des actions NASDAQ récupérées à partir d’un service de requête-réponse simple.</span><span class="sxs-lookup"><span data-stu-id="0a632-211">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="0a632-212">À des fins de démonstration, chaque ligne affiche également l’ID unique de l’instance de service qui l’a retournée.</span><span class="sxs-lookup"><span data-stu-id="0a632-212">For demonstration purposes, each line also shows the unique ID of the service instance that returned it.</span></span>

![Capture d’écran StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="0a632-214">Si le nombre de réplicas du service `stockdata` a été augmenté, vous pouvez vous attendre à ce que la valeur du **serveur** passe d’un trait à l’autres, mais en fait, tous les enregistrements 100 sont toujours retournés à partir de la même instance.</span><span class="sxs-lookup"><span data-stu-id="0a632-214">If the number of replicas of the `stockdata` service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="0a632-215">Si vous actualisez la page toutes les quelques secondes, l’ID du serveur reste le même.</span><span class="sxs-lookup"><span data-stu-id="0a632-215">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="0a632-216">Pourquoi cela se produit-il ?</span><span class="sxs-lookup"><span data-stu-id="0a632-216">Why does this happen?</span></span> <span data-ttu-id="0a632-217">Il existe deux facteurs à lire ici.</span><span class="sxs-lookup"><span data-stu-id="0a632-217">There are two factors at play here.</span></span>

<span data-ttu-id="0a632-218">Tout d’abord, le système de détection du service Kubernetes utilise l’équilibrage de charge « Round Robin » par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a632-218">First, the Kubernetes service discovery system uses "round-robin" load-balancing by default.</span></span> <span data-ttu-id="0a632-219">La première fois que le serveur DNS est interrogé, il retourne la première adresse IP correspondante pour le service.</span><span class="sxs-lookup"><span data-stu-id="0a632-219">The first time the DNS server is queried, it will return the first matching IP address for the service.</span></span> <span data-ttu-id="0a632-220">La prochaine fois, l’adresse IP suivante dans la liste, et ainsi de suite, jusqu’à la fin, à partir de laquelle elle repasse au début.</span><span class="sxs-lookup"><span data-stu-id="0a632-220">The next time, the next IP address in the list, and so on, until the end, at which point it loops back to the start.</span></span>

<span data-ttu-id="0a632-221">Deuxièmement, le `HttpClient` utilisé pour le client gRPC de l’application StockWeb est créé et géré par le [ASP.net Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), et une seule instance de ce client est utilisée pour chaque appel à la page.</span><span class="sxs-lookup"><span data-stu-id="0a632-221">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="0a632-222">Le client n’effectue qu’une seule recherche DNS, donc toutes les demandes sont acheminées vers la même adresse IP.</span><span class="sxs-lookup"><span data-stu-id="0a632-222">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="0a632-223">En outre, étant donné que le `HttpClientHandler` est mis en cache pour des raisons de performances, plusieurs demandes en succession rapide utilisent *toutes* la même adresse IP, jusqu’à ce que l’entrée DNS mise en cache expire ou que l’instance de gestionnaire soit supprimée pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="0a632-223">Furthermore, because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="0a632-224">Cela signifie que, par défaut, les demandes adressées à un service gRPC ne sont pas équilibrées sur toutes les instances de ce service dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="0a632-224">This means that by default requests to a gRPC service aren't balanced across all instances of that service in the cluster.</span></span> <span data-ttu-id="0a632-225">Les différents consommateurs utilisent des instances différentes, mais cela ne garantit pas une bonne distribution des demandes et une utilisation équilibrée des ressources.</span><span class="sxs-lookup"><span data-stu-id="0a632-225">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests and a balanced use of resources.</span></span>

<span data-ttu-id="0a632-226">Le chapitre suivant, [maillages de service](service-mesh.md), va vous montrer comment résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="0a632-226">The next chapter, [Service Meshes](service-mesh.md), will look at how to address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0a632-227">[Précédent](docker.md)
>[Suivant](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="0a632-227">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
