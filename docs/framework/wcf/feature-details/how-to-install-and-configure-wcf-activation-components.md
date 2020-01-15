---
title: "Comment : installer et configurer des composants d'activation WCF"
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: e71664b4361ba28a50b29499585b20a8adbaefd2
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964467"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="993b6-102">Comment : installer et configurer des composants d'activation WCF</span><span class="sxs-lookup"><span data-stu-id="993b6-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="993b6-103">Cette rubrique décrit les étapes nécessaires à la configuration du service d’activation des processus Windows (également appelé WAS) sur Windows Vista pour héberger des services Windows Communication Foundation (WCF) qui ne communiquent pas sur les protocoles réseau HTTP.</span><span class="sxs-lookup"><span data-stu-id="993b6-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="993b6-104">Les sections suivantes définissent les étapes pour cette configuration :</span><span class="sxs-lookup"><span data-stu-id="993b6-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="993b6-105">Installez (ou confirmez l’installation de) les composants d’activation WCF.</span><span class="sxs-lookup"><span data-stu-id="993b6-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="993b6-106">Configurer le service WAS pour prendre en charge un protocole non HTTP.</span><span class="sxs-lookup"><span data-stu-id="993b6-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="993b6-107">La procédure suivante configure Windows Vista pour l’activation TCP.</span><span class="sxs-lookup"><span data-stu-id="993b6-107">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="993b6-108">Après l’installation et la configuration de WAS, consultez [Comment : héberger un service WCF dans was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) pour les procédures de création d’un service WCF qui expose un point de terminaison non-http qui utilise was.</span><span class="sxs-lookup"><span data-stu-id="993b6-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="993b6-109">Pour installer les composants d'activation non HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="993b6-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="993b6-110">Cliquez sur le bouton **Démarrer** , puis sur **panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="993b6-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="993b6-111">Cliquez sur **Programmes** puis sur **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="993b6-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="993b6-112">Dans le menu **tâches** , cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="993b6-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="993b6-113">Recherchez le nœud WinFX, sélectionnez-le, puis développez-le.</span><span class="sxs-lookup"><span data-stu-id="993b6-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="993b6-114">Sélectionnez la zone **composants d’activation non HTTP WCF** et enregistrez le paramètre.</span><span class="sxs-lookup"><span data-stu-id="993b6-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="993b6-115">Pour configurer le service WAS pour prendre en charge l'activation TCP</span><span class="sxs-lookup"><span data-stu-id="993b6-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="993b6-116">Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp.</span><span class="sxs-lookup"><span data-stu-id="993b6-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="993b6-117">Pour ce faire, vous pouvez utiliser Appcmd. exe, qui est installé avec l’ensemble d’outils de gestion d’IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="993b6-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="993b6-118">Dans une fenêtre d'invite de commandes au niveau de l'administrateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="993b6-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="993b6-119">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-119">This command is a single line of text.</span></span> <span data-ttu-id="993b6-120">Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="993b6-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="993b6-121">Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacune d'elle peut activer de manière individuelle la prise en charge net.pipe.</span><span class="sxs-lookup"><span data-stu-id="993b6-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="993b6-122">Afin d'activer net.tcp pour l'application, exécutez la commande suivante à partir d'une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="993b6-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="993b6-123">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-123">This command is a single line of text.</span></span> <span data-ttu-id="993b6-124">Cette commande permet d’accéder à l’application\<*WCF*> à l’aide de `http://localhost/<WCF Application>` et `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="993b6-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="993b6-125">Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="993b6-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="993b6-126">Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="993b6-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="993b6-127">Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="993b6-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="993b6-128">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="993b6-129">Supprimez la liaison du site net.tcp en exécutant la commande suivante dans une invite de commandes de niveau élevé :</span><span class="sxs-lookup"><span data-stu-id="993b6-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="993b6-130">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="993b6-131">Pour supprimer net.tcp de la liste des protocoles actifs</span><span class="sxs-lookup"><span data-stu-id="993b6-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="993b6-132">Pour supprimer net.tcp de la liste des protocoles actifs, exécutez la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="993b6-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="993b6-133">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="993b6-134">Pour supprimer la liaison de site net.tcp</span><span class="sxs-lookup"><span data-stu-id="993b6-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="993b6-135">Pour supprimer la liaison de site net.tcp, exécutez la commande suivante dans une fenêtre d’invite de commandes au niveau de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="993b6-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="993b6-136">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="993b6-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="993b6-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="993b6-137">See also</span></span>

- [<span data-ttu-id="993b6-138">Activation TCP</span><span class="sxs-lookup"><span data-stu-id="993b6-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="993b6-139">Activation MSMQ</span><span class="sxs-lookup"><span data-stu-id="993b6-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="993b6-140">Activation de NamedPipe</span><span class="sxs-lookup"><span data-stu-id="993b6-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- <span data-ttu-id="993b6-141">[Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="993b6-141">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
