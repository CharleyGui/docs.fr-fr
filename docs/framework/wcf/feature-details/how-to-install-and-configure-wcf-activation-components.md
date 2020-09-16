---
title: 'Procédure : installer et configurer des composants d’activation WCF'
description: Découvrez comment configurer le service d’activation des processus Windows (WAS) sur Windows Vista pour héberger des services WCF qui ne communiquent pas via HTTP.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 085a69421f0aa7b763bd2222820ced4b4a7e1c81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557864"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="56fd9-103">Procédure : installer et configurer des composants d’activation WCF</span><span class="sxs-lookup"><span data-stu-id="56fd9-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="56fd9-104">Cette rubrique décrit les étapes nécessaires à la configuration du service d’activation des processus Windows (également appelé WAS) sur Windows Vista pour héberger des services Windows Communication Foundation (WCF) qui ne communiquent pas sur les protocoles réseau HTTP.</span><span class="sxs-lookup"><span data-stu-id="56fd9-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="56fd9-105">Les sections suivantes définissent les étapes pour cette configuration :</span><span class="sxs-lookup"><span data-stu-id="56fd9-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="56fd9-106">Installez (ou confirmez l’installation de) les composants d’activation WCF.</span><span class="sxs-lookup"><span data-stu-id="56fd9-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="56fd9-107">Configurer le service WAS pour prendre en charge un protocole non HTTP.</span><span class="sxs-lookup"><span data-stu-id="56fd9-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="56fd9-108">La procédure suivante configure Windows Vista pour l’activation TCP.</span><span class="sxs-lookup"><span data-stu-id="56fd9-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="56fd9-109">Après l’installation et la configuration de WAS, consultez [Comment : héberger un service WCF dans was](how-to-host-a-wcf-service-in-was.md) pour les procédures de création d’un service WCF qui expose un point de terminaison non-http qui utilise was.</span><span class="sxs-lookup"><span data-stu-id="56fd9-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="56fd9-110">Pour installer les composants d'activation non HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="56fd9-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="56fd9-111">Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="56fd9-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="56fd9-112">Cliquez sur **Programmes** puis sur **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="56fd9-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="56fd9-113">Dans le menu **tâches** , cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="56fd9-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="56fd9-114">Recherchez le nœud WinFX, sélectionnez-le, puis développez-le.</span><span class="sxs-lookup"><span data-stu-id="56fd9-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="56fd9-115">Sélectionnez la zone **composants d’activation non HTTP WCF** et enregistrez le paramètre.</span><span class="sxs-lookup"><span data-stu-id="56fd9-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="56fd9-116">Pour configurer le service WAS pour prendre en charge l'activation TCP</span><span class="sxs-lookup"><span data-stu-id="56fd9-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="56fd9-117">Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp.</span><span class="sxs-lookup"><span data-stu-id="56fd9-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="56fd9-118">Pour ce faire, vous pouvez utiliser Appcmd.exe, qui est installé avec l’ensemble d’outils de gestion d’IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="56fd9-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="56fd9-119">Dans une fenêtre d'invite de commandes au niveau de l'administrateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="56fd9-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="56fd9-120">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-120">This command is a single line of text.</span></span> <span data-ttu-id="56fd9-121">Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="56fd9-122">Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacune d'elle peut activer de manière individuelle la prise en charge net.pipe.</span><span class="sxs-lookup"><span data-stu-id="56fd9-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="56fd9-123">Afin d'activer net.tcp pour l'application, exécutez la commande suivante à partir d'une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="56fd9-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="56fd9-124">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-124">This command is a single line of text.</span></span> <span data-ttu-id="56fd9-125">Cette commande permet \<*WCF Application*> d’accéder à l’application/à l’aide de `http://localhost/<WCF Application>` et de `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="56fd9-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="56fd9-126">Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="56fd9-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="56fd9-127">Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="56fd9-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="56fd9-128">Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="56fd9-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="56fd9-129">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="56fd9-130">Supprimez la liaison du site net.tcp en exécutant la commande suivante dans une invite de commandes de niveau élevé :</span><span class="sxs-lookup"><span data-stu-id="56fd9-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="56fd9-131">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="56fd9-132">Pour supprimer net.tcp de la liste des protocoles actifs</span><span class="sxs-lookup"><span data-stu-id="56fd9-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="56fd9-133">Pour supprimer net.tcp de la liste des protocoles actifs, exécutez la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="56fd9-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="56fd9-134">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="56fd9-135">Pour supprimer la liaison de site net.tcp</span><span class="sxs-lookup"><span data-stu-id="56fd9-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="56fd9-136">Pour supprimer la liaison de site net.tcp, exécutez la commande suivante dans une fenêtre d’invite de commandes au niveau de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="56fd9-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="56fd9-137">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="56fd9-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="56fd9-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56fd9-138">See also</span></span>

- [<span data-ttu-id="56fd9-139">Activation de TCP</span><span class="sxs-lookup"><span data-stu-id="56fd9-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="56fd9-140">MSMQ Activation</span><span class="sxs-lookup"><span data-stu-id="56fd9-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="56fd9-141">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="56fd9-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="56fd9-142">[Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="56fd9-142">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
