---
title: Créer des applications ASP.NET Core 2.2 déployées en tant que conteneurs Linux dans des clusters AKS/Kubernetes
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70848756"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="00f62-103">Créer des applications ASP.NET Core 2.2 déployées en tant que conteneurs Linux dans un orchestrateur AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="00f62-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="00f62-104">Azure Kubernetes Service (AKS) correspond à des services d’orchestrations Kubernetes gérés par Azure qui simplifient la gestion et le déploiement de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="00f62-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="00f62-105">Les principales fonctionnalités AKS sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="00f62-105">AKS main features are:</span></span>

- <span data-ttu-id="00f62-106">Plan de contrôle hébergé par Azure</span><span class="sxs-lookup"><span data-stu-id="00f62-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="00f62-107">Mises à niveau automatisées</span><span class="sxs-lookup"><span data-stu-id="00f62-107">Automated upgrades</span></span>
- <span data-ttu-id="00f62-108">Réparation spontanée</span><span class="sxs-lookup"><span data-stu-id="00f62-108">Self-healing</span></span>
- <span data-ttu-id="00f62-109">Mise à l’échelle configurable par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="00f62-109">User configurable scaling</span></span>
- <span data-ttu-id="00f62-110">Expérience utilisateur plus simple pour les développeurs et les opérateurs de cluster</span><span class="sxs-lookup"><span data-stu-id="00f62-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="00f62-111">Les exemples suivants décrivent la création d’une application ASP.NET Core 2.2 qui s’exécute sur Linux et se déploie sur un cluster AKS dans Azure, tandis que le développement est effectué à l’aide de Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="00f62-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="00f62-112">Création du projet ASP.NET Core 2.2 à l’aide de Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="00f62-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="00f62-113">ASP.NET Core est une plateforme de développement généraliste tenue à jour par Microsoft et la communauté .NET sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="00f62-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="00f62-114">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT.</span><span class="sxs-lookup"><span data-stu-id="00f62-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="00f62-115">Cet exemple utilise un projet simple basé sur un modèle d’API web Visual Studio, si bien que vous n’avez pas besoin de connaissances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="00f62-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="00f62-116">Vous devez uniquement créer le projet à l’aide d’un modèle standard qui inclut tous les éléments nécessaires pour exécuter un petit projet avec une API REST, à l’aide de la technologie ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="00f62-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Ajoutez une nouvelle fenêtre de projet dans Visual Studio, en sélectionnant Application web ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="00f62-118">**Figure 4-36**.</span><span class="sxs-lookup"><span data-stu-id="00f62-118">**Figure 4-36**.</span></span> <span data-ttu-id="00f62-119">Création d’une application ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00f62-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="00f62-120">Pour créer l’exemple de projet dans Visual Studio, sélectionnez **File** > **New** > **Project**, sélectionnez les types de projet **Web** dans le volet gauche, **suivis de ASP.NET application Web de base.**</span><span class="sxs-lookup"><span data-stu-id="00f62-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="00f62-121">Visual Studio liste les modèles pour les projets web.</span><span class="sxs-lookup"><span data-stu-id="00f62-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="00f62-122">Pour notre exemple, sélectionnez **API** pour créer une application API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="00f62-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="00f62-123">Vérifiez que vous avez sélectionné le framework ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="00f62-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="00f62-124">.NET Core 2.2, inclus dans la dernière version de Visual Studio 2017, est automatiquement installé et configuré pour vous lorsque vous installez Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="00f62-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Boîte de dialogue Visual Studio permettant de sélectionner le type Application web ASP.NET Core avec l’option API sélectionnée.](media/create-web-api-application.png)

<span data-ttu-id="00f62-126">**Figure 4-37**.</span><span class="sxs-lookup"><span data-stu-id="00f62-126">**Figure 4-37**.</span></span> <span data-ttu-id="00f62-127">Sélection du type de projet ASP.NET CORE 2.2 et API web</span><span class="sxs-lookup"><span data-stu-id="00f62-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="00f62-128">Si vous avez des versions antérieures de .NET Core, vous pouvez télécharger et installer la version 2.2 à partir de <https://dotnet.microsoft.com/download>.</span><span class="sxs-lookup"><span data-stu-id="00f62-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="00f62-129">Vous pouvez ajouter la prise en charge de Docker lors de la création du projet ou par la suite, de sorte à pouvoir « dockeriser » votre projet à tout moment.</span><span class="sxs-lookup"><span data-stu-id="00f62-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="00f62-130">Pour ajouter le support Docker après la création du projet, cliquez à droite sur le nœud du projet dans Solution Explorer et **sélectionnez le** > support Add**Docker** sur le menu context.</span><span class="sxs-lookup"><span data-stu-id="00f62-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Option de menu contextuelle pour ajouter le support Docker à un projet existant : Cliquez à droite (sur le projet) > Ajouter > support Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="00f62-132">**Figure 4-38**.</span><span class="sxs-lookup"><span data-stu-id="00f62-132">**Figure 4-38**.</span></span> <span data-ttu-id="00f62-133">Ajout de la prise en charge de Docker à un projet existant</span><span class="sxs-lookup"><span data-stu-id="00f62-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="00f62-134">Pour terminer l’ajout de la prise en charge de Docker, vous pouvez choisir Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="00f62-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="00f62-135">Pour notre exemple, sélectionnez **Linux**, car AKS ne prend pas en charge les conteneurs Windows (depuis la fin 2018).</span><span class="sxs-lookup"><span data-stu-id="00f62-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Boîte de dialogue Option permettant de sélectionner le système d’exploitation cible pour Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="00f62-137">**Figure 4-39**.</span><span class="sxs-lookup"><span data-stu-id="00f62-137">**Figure 4-39**.</span></span> <span data-ttu-id="00f62-138">Sélection de conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="00f62-138">Selecting Linux containers.</span></span>

<span data-ttu-id="00f62-139">À l’issue de ces étapes simples, votre application ASP.NET Core 2.2 s’exécute sur un conteneur Linux.</span><span class="sxs-lookup"><span data-stu-id="00f62-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="00f62-140">Comme vous pouvez le voir, l’intégration entre Visual Studio 2017 et Docker est entièrement orientée vers la productivité du développeur.</span><span class="sxs-lookup"><span data-stu-id="00f62-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="00f62-141">Vous pouvez maintenant exécuter votre application avec la touche **F5** ou en utilisant le bouton **Lecture**.</span><span class="sxs-lookup"><span data-stu-id="00f62-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="00f62-142">Après avoir exécuté le projet, vous pouvez lister les images à l’aide de la commande `docker images`.</span><span class="sxs-lookup"><span data-stu-id="00f62-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="00f62-143">Vous devez voir l’image `mssampleapplication` créée par le déploiement automatique de notre projet avec Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="00f62-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Sortie de la console à partir de la commande d’images docker, montre une liste avec: Dépôt, Tag, Id Image, Créé (date), et La taille.](media/docker-images-command.png)

<span data-ttu-id="00f62-145">**Figure 4-40**.</span><span class="sxs-lookup"><span data-stu-id="00f62-145">**Figure 4-40**.</span></span> <span data-ttu-id="00f62-146">Affichage des images Docker</span><span class="sxs-lookup"><span data-stu-id="00f62-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="00f62-147">Inscrire la solution dans Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="00f62-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="00f62-148">Chargez l’image dans un registre Docker, comme [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) ou Docker Hub, de sorte à pouvoir la déployer sur le cluster AKS de ce registre.</span><span class="sxs-lookup"><span data-stu-id="00f62-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="00f62-149">Pour notre exemple, nous chargeons l’image dans Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="00f62-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="00f62-150">Créer l’image en mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="00f62-150">Create the image in Release mode</span></span>

<span data-ttu-id="00f62-151">Nous allons maintenant créer l’image en mode **Mise en production** en choisissant l’option **Mise en production**, comme illustré dans la figure 4-41, puis en exécutant l’application comme nous l’avons fait auparavant.</span><span class="sxs-lookup"><span data-stu-id="00f62-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Option de barre d’outils dans Visual Studio pour créer en mode Mise en production.](media/select-release-mode.png)

<span data-ttu-id="00f62-153">**Figure 4-41**.</span><span class="sxs-lookup"><span data-stu-id="00f62-153">**Figure 4-41**.</span></span> <span data-ttu-id="00f62-154">Sélection du mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="00f62-154">Selecting Release Mode</span></span>

<span data-ttu-id="00f62-155">Si vous exécutez la commande `docker image`, vous voyez deux images créées, une pour le mode `debug` et l’autre pour le mode `release`.</span><span class="sxs-lookup"><span data-stu-id="00f62-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="00f62-156">Créer une balise pour l’image</span><span class="sxs-lookup"><span data-stu-id="00f62-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="00f62-157">Chaque image de conteneur doit être marquée avec le `loginServer` nom du registre.</span><span class="sxs-lookup"><span data-stu-id="00f62-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="00f62-158">Cette balise est utilisée pour l’acheminement lors de l’envoi des images de conteneur dans un registre d’images.</span><span class="sxs-lookup"><span data-stu-id="00f62-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="00f62-159">Vous pouvez voir le nom `loginServer` à partir du portail Azure, en prenant les informations auprès d’Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="00f62-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Affichage dans le navigateur du nom du registre de conteneurs Azure, dans le coin supérieur droit.](media/loginServer-name.png)

<span data-ttu-id="00f62-161">**Figure 4-42**.</span><span class="sxs-lookup"><span data-stu-id="00f62-161">**Figure 4-42**.</span></span> <span data-ttu-id="00f62-162">Affichage du nom du registre</span><span class="sxs-lookup"><span data-stu-id="00f62-162">View of the name of the Registry</span></span>

<span data-ttu-id="00f62-163">Ou en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="00f62-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Sortie de console issue de la commande ci-dessus.](media/az-cli-loginServer-name.png)

<span data-ttu-id="00f62-165">**Figure 4-43**.</span><span class="sxs-lookup"><span data-stu-id="00f62-165">**Figure 4-43**.</span></span> <span data-ttu-id="00f62-166">Obtenir le nom du registre à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="00f62-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="00f62-167">Dans les deux cas, vous obtenez le nom.</span><span class="sxs-lookup"><span data-stu-id="00f62-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="00f62-168">Dans notre exemple, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="00f62-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="00f62-169">Maintenant vous pouvez baliser l’image, en prenant la dernière (l’image de mise en production), avec la commande :</span><span class="sxs-lookup"><span data-stu-id="00f62-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="00f62-170">Après avoir exécuté la commande `docker tag`, listez les images avec la commande `docker images`. L’image doit apparaître avec la nouvelle balise.</span><span class="sxs-lookup"><span data-stu-id="00f62-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Sortie de console issue de la commande docker images.](media/tagged-docker-images-list.png)

<span data-ttu-id="00f62-172">**Figure 4-44**.</span><span class="sxs-lookup"><span data-stu-id="00f62-172">**Figure 4-44**.</span></span> <span data-ttu-id="00f62-173">Vue des images balisées</span><span class="sxs-lookup"><span data-stu-id="00f62-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="00f62-174">Pousser (push) l’image vers Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="00f62-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="00f62-175">Connectez-vous à Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="00f62-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="00f62-176">Poussez (push) l’image vers Azure Container Registry avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="00f62-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="00f62-177">Cette commande a besoin de temps pour charger les images, mais vous tient informé pendant le processus.</span><span class="sxs-lookup"><span data-stu-id="00f62-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![La sortie de console issue de la commande docker push présente une barre de progression sous forme de caractères pour chaque couche.](media/uploading-image-to-acr.png)

<span data-ttu-id="00f62-179">**Figure 4-45**.</span><span class="sxs-lookup"><span data-stu-id="00f62-179">**Figure 4-45**.</span></span> <span data-ttu-id="00f62-180">Chargement de l’image dans Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="00f62-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="00f62-181">Vous pouvez voir ci-dessous le résultat que vous devez obtenir lorsque le processus est terminé :</span><span class="sxs-lookup"><span data-stu-id="00f62-181">You can see below the result you should get when the process completes:</span></span>

![Sortie de console issue de la commande docker push terminée, montrant la totalité des couches ou nœuds.](media/uploading-docker-images-complete.png)

<span data-ttu-id="00f62-183">**Figure 4-46**.</span><span class="sxs-lookup"><span data-stu-id="00f62-183">**Figure 4-46**.</span></span> <span data-ttu-id="00f62-184">Affichage des nœuds</span><span class="sxs-lookup"><span data-stu-id="00f62-184">View of nodes</span></span>

<span data-ttu-id="00f62-185">L’étape suivante consiste à déployer votre conteneur dans votre cluster AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="00f62-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="00f62-186">Pour cela, vous avez besoin d’un fichier (**fichier de déploiement .yml**) qui contient ceci :</span><span class="sxs-lookup"><span data-stu-id="00f62-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="00f62-187">Pour plus d’informations sur le déploiement avec Kubernetes, consultez : <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="00f62-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="00f62-188">Vous êtes maintenant presque prêt à effectuer un déploiement en utilisant **Kubectl**, mais vous devez tout d’abord obtenir les informations d’identification pour le cluster AKS avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="00f62-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Sortie de console de la commande ci-dessus: Fusionné "MSSampleK8Cluster comme contexte actuel dans /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="00f62-190">**Figure 4-47**.</span><span class="sxs-lookup"><span data-stu-id="00f62-190">**Figure 4-47**.</span></span> <span data-ttu-id="00f62-191">Obtention des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="00f62-191">getting credentials</span></span>

<span data-ttu-id="00f62-192">Ensuite, utilisez la commande `kubectl create` pour lancer le déploiement.</span><span class="sxs-lookup"><span data-stu-id="00f62-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Sortie de console issue de la commande ci-dessus : deployment "mssamplesbook" created.](media/kubectl-create-command.png)

<span data-ttu-id="00f62-195">**Figure 4-48**.</span><span class="sxs-lookup"><span data-stu-id="00f62-195">**Figure 4-48**.</span></span> <span data-ttu-id="00f62-196">Déployer sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="00f62-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="00f62-197">Lorsque le déploiement est terminé, vous pouvez accéder à la console Kubernetes avec un proxy local auquel vous pouvez accéder temporairement avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="00f62-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="00f62-198">Puis accédez à l’URL `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="00f62-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Affichage dans le navigateur du tableau de bord Kubernetes, montrant les déploiements, les pods, les jeux de réplicas et les services.](media/kubernetes-cluster-information.png)

<span data-ttu-id="00f62-200">**Figure 4-49**.</span><span class="sxs-lookup"><span data-stu-id="00f62-200">**Figure 4-49**.</span></span> <span data-ttu-id="00f62-201">Afficher les informations de cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="00f62-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="00f62-202">Votre application est maintenant déployée sur Azure, à l’aide d’un conteneur Linux et d’un cluster AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="00f62-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="00f62-203">Vous pouvez accéder à votre application par le biais de l’adresse IP publique de votre service, que vous pouvez obtenir à partir du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="00f62-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="00f62-204">Vous pouvez voir comment créer le cluster AKS pour cet exemple dans la section [**Déployer sur Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) de ce guide.</span><span class="sxs-lookup"><span data-stu-id="00f62-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00f62-205">[Suivant précédent](set-up-windows-containers-with-powershell.md)
>[Next](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="00f62-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
