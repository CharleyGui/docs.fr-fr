---
title: Déployer des applications .NET sur Raspberry pi
description: Découvrez comment déployer des applications .NET sur Raspberry pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588683"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="f57b5-103">Déployer des applications .NET sur Raspberry pi</span><span class="sxs-lookup"><span data-stu-id="f57b5-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="f57b5-104">Le déploiement d’applications .NET vers Raspberry pi est identique à celui de toute autre plateforme.</span><span class="sxs-lookup"><span data-stu-id="f57b5-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="f57b5-105">Votre application peut s’exécuter en mode de déploiement *autonome* ou *dépendant du Framework* .</span><span class="sxs-lookup"><span data-stu-id="f57b5-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="f57b5-106">Chaque stratégie présente des avantages.</span><span class="sxs-lookup"><span data-stu-id="f57b5-106">There are advantages to each strategy.</span></span> <span data-ttu-id="f57b5-107">Pour plus d’informations, consultez [vue d’ensemble de la publication d’applications .net](../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f57b5-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="f57b5-108">Déploiement d’une application dépendante du Framework</span><span class="sxs-lookup"><span data-stu-id="f57b5-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="f57b5-109">Pour déployer votre application comme une application dépendante du Framework, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f57b5-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="f57b5-110">Installez .NET sur Raspberry pi à l’aide des [scripts dotnet-install](../core/tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f57b5-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="f57b5-111">Effectuez les étapes suivantes à partir d’une invite bash sur le Raspberry pi (local ou SSH) :</span><span class="sxs-lookup"><span data-stu-id="f57b5-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="f57b5-112">Exécutez la commande suivante pour installer .NET :</span><span class="sxs-lookup"><span data-stu-id="f57b5-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="f57b5-113">Cela installe la dernière version.</span><span class="sxs-lookup"><span data-stu-id="f57b5-113">This installs the latest version.</span></span> <span data-ttu-id="f57b5-114">Si vous avez besoin d’une version spécifique, ajoutez `--version <VERSION>` à la fin, où `<VERSION>` correspond à la version de build spécifique.</span><span class="sxs-lookup"><span data-stu-id="f57b5-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="f57b5-115">Pour simplifier la résolution des chemins d’accès, ajoutez une `DOTNET_ROOT` variable d’environnement et ajoutez le répertoire *. dotnet* à `$PATH` avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f57b5-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="f57b5-116">Vérifiez l’installation de .NET à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f57b5-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="f57b5-117">Vérifiez que la version affichée correspond à la version que vous avez installée.</span><span class="sxs-lookup"><span data-stu-id="f57b5-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="f57b5-118">Publiez l’application sur l’ordinateur de développement comme suit, selon l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="f57b5-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="f57b5-119">Si vous utilisez **Visual Studio**, [déployez l’application dans un dossier local](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="f57b5-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="f57b5-120">Avant la publication, sélectionnez **modifier** dans le résumé du profil de publication et sélectionnez l’onglet **paramètres** . Assurez-vous que le **mode de déploiement** est défini sur dépendant du Framework et que *le* **Runtime cible** est défini sur *portable*.</span><span class="sxs-lookup"><span data-stu-id="f57b5-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="f57b5-121">Si vous utilisez l' **interface CLI .net**, utilisez la commande [dotnet Publish](../core/tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="f57b5-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="f57b5-122">Aucun argument supplémentaire n’est requis.</span><span class="sxs-lookup"><span data-stu-id="f57b5-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="f57b5-123">À partir d’une invite bash sur le Raspberry pi (local ou SSH), exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="f57b5-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="f57b5-124">Pour ce faire, définissez le dossier de déploiement en tant que répertoire actif et exécutez la commande suivante (où *HelloWorld.dll* est le point d’entrée de l’application) :</span><span class="sxs-lookup"><span data-stu-id="f57b5-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="f57b5-125">Déploiement d’une application autonome</span><span class="sxs-lookup"><span data-stu-id="f57b5-125">Deploying a self-contained app</span></span>

<span data-ttu-id="f57b5-126">Pour déployer votre application en tant qu’application autonome, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f57b5-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="f57b5-127">Publiez l’application sur l’ordinateur de développement comme suit, selon l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="f57b5-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="f57b5-128">Si vous utilisez **Visual Studio**, [déployez l’application dans un dossier local](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="f57b5-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="f57b5-129">Avant la publication, sélectionnez **modifier** dans le résumé du profil de publication et sélectionnez l’onglet **paramètres** . Assurez-vous que le **mode de déploiement** est défini sur *autonome* et que le **Runtime cible** a la valeur *Linux-ARM*.</span><span class="sxs-lookup"><span data-stu-id="f57b5-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="f57b5-130">Si vous utilisez l' **interface CLI .net**, utilisez la commande [dotnet Publish](../core/tools/dotnet-publish.md) avec l' `-r linux-arm` argument :</span><span class="sxs-lookup"><span data-stu-id="f57b5-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="f57b5-131">À partir d’une invite bash sur le Raspberry pi (local ou SSH), exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="f57b5-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="f57b5-132">Pour ce faire, définissez le répertoire actif sur l’emplacement de déploiement et procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f57b5-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="f57b5-133">Attribuez à l’exécutable l’autorisation *Execute* (où `HelloWorld` est le nom du fichier exécutable).</span><span class="sxs-lookup"><span data-stu-id="f57b5-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="f57b5-134">Exécutez le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="f57b5-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```
