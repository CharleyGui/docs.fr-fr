---
title: Environnement de développement pour les applications Docker
description: Découvrez les options les plus importantes des outils de développement qui prennent en charge le cycle de développement Docker.
ms.date: 04/16/2020
ms.openlocfilehash: b1df16db88fa85f794407c989f5428030c4cddf7
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394885"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="ac62d-103">Environnement de développement pour les applications Docker</span><span class="sxs-lookup"><span data-stu-id="ac62d-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="ac62d-104">Choix des outils de développement : IDE ou éditeur</span><span class="sxs-lookup"><span data-stu-id="ac62d-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="ac62d-105">Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft met à votre disposition tout ce dont vous avez besoin pour développer des applications Docker.</span><span class="sxs-lookup"><span data-stu-id="ac62d-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="ac62d-106">Visual Studio Code et Docker CLI (outils multiplateformes pour Mac, Linux et Windows)</span><span class="sxs-lookup"><span data-stu-id="ac62d-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="ac62d-107">Si vous préférez un éditeur léger et multiplateforme prenant en charge n’importe quel langage de développement, vous pouvez utiliser Visual Studio Code et l’interface de ligne de commande Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="ac62d-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="ac62d-108">Ces produits offrent une expérience simple mais robuste, ce qui est indispensable pour simplifier le workflow du développeur.</span><span class="sxs-lookup"><span data-stu-id="ac62d-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="ac62d-109">En installant « Docker pour Mac » ou « Docker pour Windows » (environnement de développement), les développeurs Docker peuvent utiliser une interface de ligne de commande Docker unique pour créer des applications pour Windows ou Linux (environnement d’exécution).</span><span class="sxs-lookup"><span data-stu-id="ac62d-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="ac62d-110">De plus, Visual Studio Code prend en charge les extensions pour Docker avec IntelliSense pour les fichiers Dockerfile et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="ac62d-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="ac62d-111">Pour télécharger Visual Studio Code, accédez à <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="ac62d-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="ac62d-112">Pour télécharger Docker pour Mac et Windows, accédez à <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="ac62d-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="ac62d-113">Visual Studio avec les outils Docker (machine de développement Windows)</span><span class="sxs-lookup"><span data-stu-id="ac62d-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="ac62d-114">Nous vous recommandons d’utiliser Visual Studio 2019 avec les outils intégrés de l’ancrage activés.</span><span class="sxs-lookup"><span data-stu-id="ac62d-114">We recommend you use Visual Studio 2019 with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="ac62d-115">Avec Visual Studio, vous pouvez développer, exécuter et valider vos applications directement dans l’environnement Docker de votre choix.</span><span class="sxs-lookup"><span data-stu-id="ac62d-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="ac62d-116">Appuyez sur F5 pour déboguer votre application (à un ou plusieurs conteneurs) directement dans un hôte Docker ou appuyez sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à regénérer le conteneur.</span><span class="sxs-lookup"><span data-stu-id="ac62d-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="ac62d-117">Il s’agit du choix le plus simple et le plus robuste pour les développeurs Windows qui souhaitent créer des conteneurs Docker pour Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ac62d-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="ac62d-118">Visual Studio pour Mac (machine de développement Mac)</span><span class="sxs-lookup"><span data-stu-id="ac62d-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="ac62d-119">Vous pouvez utiliser [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour développer des applications basées sur Docker.</span><span class="sxs-lookup"><span data-stu-id="ac62d-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="ac62d-120">Visual Studio pour Mac offre un environnement de développement intégré (IDE) plus riche par rapport à Visual Studio Code pour Mac.</span><span class="sxs-lookup"><span data-stu-id="ac62d-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="ac62d-121">Choix en matière de langage et de framework</span><span class="sxs-lookup"><span data-stu-id="ac62d-121">Language and framework choices</span></span>

<span data-ttu-id="ac62d-122">Vous pouvez développer des applications Docker en utilisant les outils Microsoft avec les langages les plus modernes.</span><span class="sxs-lookup"><span data-stu-id="ac62d-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="ac62d-123">En voici une liste non exhaustive :</span><span class="sxs-lookup"><span data-stu-id="ac62d-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="ac62d-124">.NET Core et ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ac62d-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="ac62d-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="ac62d-125">Node.js</span></span>
- <span data-ttu-id="ac62d-126">Go</span><span class="sxs-lookup"><span data-stu-id="ac62d-126">Go</span></span>
- <span data-ttu-id="ac62d-127">Java</span><span class="sxs-lookup"><span data-stu-id="ac62d-127">Java</span></span>
- <span data-ttu-id="ac62d-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="ac62d-128">Ruby</span></span>
- <span data-ttu-id="ac62d-129">Python</span><span class="sxs-lookup"><span data-stu-id="ac62d-129">Python</span></span>

<span data-ttu-id="ac62d-130">En fait, vous pouvez utiliser n’importe quel langage moderne pris en charge par Docker dans Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ac62d-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac62d-131">[Précédent](deploy-azure-kubernetes-service.md) 
> [Suivant](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ac62d-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
