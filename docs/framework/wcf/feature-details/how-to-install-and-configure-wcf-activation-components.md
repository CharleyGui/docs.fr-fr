---
title: 'Procédure : installer et configurer des composants d’activation WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 1141bd8344887990ddd8646eba9d25c5d9a4287d
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487049"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="a2983-102">Procédure : installer et configurer des composants d’activation WCF</span><span class="sxs-lookup"><span data-stu-id="a2983-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="a2983-103">Cette rubrique décrit les étapes requises pour configurer le service Windows Process Activation Service (également appelé WAS) sur [!INCLUDE[wv](../../../../includes/wv-md.md)] pour héberger des services Windows Communication Foundation (WCF) les protocoles de réseau de services qui ne communiquent pas sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2983-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="a2983-104">Les sections suivantes définissent les étapes pour cette configuration :</span><span class="sxs-lookup"><span data-stu-id="a2983-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="a2983-105">Installer (ou vérifiez l’installation) les composants d’activation de WCF.</span><span class="sxs-lookup"><span data-stu-id="a2983-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
- <span data-ttu-id="a2983-106">Configurer le service WAS pour prendre en charge un protocole non HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2983-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="a2983-107">La procédure suivante configure [!INCLUDE[wv](../../../../includes/wv-md.md)] pour l'activation TCP.</span><span class="sxs-lookup"><span data-stu-id="a2983-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="a2983-108">Une fois l’installation et configuration du service WAS, consultez [Comment : Héberger un Service WCF dans WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) pour connaître les procédures créer un service WCF qui expose un point de terminaison non HTTP qui emploie WAS.</span><span class="sxs-lookup"><span data-stu-id="a2983-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="a2983-109">Pour installer les composants d'activation non HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="a2983-109">To install the WCF non-HTTP activation components</span></span>  
  
1. <span data-ttu-id="a2983-110">Cliquez sur le **Démarrer** bouton, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="a2983-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="a2983-111">Cliquez sur **programmes**, puis cliquez sur **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="a2983-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3. <span data-ttu-id="a2983-112">Sur le **tâches** menu, cliquez sur **ou désactiver des fonctionnalités Windows activer**.</span><span class="sxs-lookup"><span data-stu-id="a2983-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4. <span data-ttu-id="a2983-113">Recherchez le nœud de WinFX, sélectionnez et puis développez-le.</span><span class="sxs-lookup"><span data-stu-id="a2983-113">Find the WinFX node, select and then expand it.</span></span>  
  
5. <span data-ttu-id="a2983-114">Sélectionnez le **les composants d’Activation Non-Http WCF** zone et d’enregistrer le paramètre.</span><span class="sxs-lookup"><span data-stu-id="a2983-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="a2983-115">Pour configurer le service WAS pour prendre en charge l'activation TCP</span><span class="sxs-lookup"><span data-stu-id="a2983-115">To configure the WAS to support TCP activation</span></span>  
  
1. <span data-ttu-id="a2983-116">Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp.</span><span class="sxs-lookup"><span data-stu-id="a2983-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="a2983-117">Pour cela, à l’aide d’Appcmd.exe, installé avec l’ensemble d’outils de gestion IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="a2983-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="a2983-118">Dans une fenêtre d'invite de commandes au niveau de l'administrateur, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="a2983-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a2983-119">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-119">This command is a single line of text.</span></span> <span data-ttu-id="a2983-120">Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="a2983-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2. <span data-ttu-id="a2983-121">Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacune d'elle peut activer de manière individuelle la prise en charge net.pipe.</span><span class="sxs-lookup"><span data-stu-id="a2983-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="a2983-122">Afin d'activer net.tcp pour l'application, exécutez la commande suivante à partir d'une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2983-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a2983-123">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-123">This command is a single line of text.</span></span> <span data-ttu-id="a2983-124">Cette commande active le /\<*Application WCF*> application accessible à l’aide des deux `http://localhost/<WCF Application>` et `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="a2983-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>
  
     <span data-ttu-id="a2983-125">Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="a2983-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="a2983-126">Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a2983-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1. <span data-ttu-id="a2983-127">Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2983-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="a2983-128">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-128">This command is a single line of text.</span></span>  
  
    2. <span data-ttu-id="a2983-129">Supprimez la liaison du site net.tcp en exécutant la commande suivante dans une invite de commandes de niveau élevé :</span><span class="sxs-lookup"><span data-stu-id="a2983-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="a2983-130">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="a2983-131">Pour supprimer net.tcp de la liste des protocoles actifs</span><span class="sxs-lookup"><span data-stu-id="a2983-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1. <span data-ttu-id="a2983-132">Pour supprimer net.tcp de la liste des protocoles actifs, exécutez la commande suivante dans une invite de commandes au niveau de l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2983-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a2983-133">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="a2983-134">Pour supprimer la liaison de site net.tcp</span><span class="sxs-lookup"><span data-stu-id="a2983-134">To remove the net.tcp site binding</span></span>  
  
1. <span data-ttu-id="a2983-135">Pour supprimer la liaison de site net.tcp, exécutez la commande suivante dans une fenêtre d’invite de commandes au niveau de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a2983-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a2983-136">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="a2983-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2983-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2983-137">See also</span></span>

- [<span data-ttu-id="a2983-138">Activation TCP</span><span class="sxs-lookup"><span data-stu-id="a2983-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="a2983-139">Activation MSMQ</span><span class="sxs-lookup"><span data-stu-id="a2983-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="a2983-140">Activation de NamedPipe</span><span class="sxs-lookup"><span data-stu-id="a2983-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="a2983-141">Fonctionnalités d’hébergement de Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="a2983-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
