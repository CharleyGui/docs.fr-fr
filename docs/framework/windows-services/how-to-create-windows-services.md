---
title: 'Procédure : créer des services Windows'
description: Utilisez le modèle de projet de service Windows pour créer un service. Définissez la propriété ServiceName, créez des programmes d’installation et remplacez les méthodes OnStart et OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925772"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="8e3f7-104">Procédure : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="8e3f7-104">How to: Create Windows Services</span></span>
<span data-ttu-id="8e3f7-105">Quand vous créez un service, vous pouvez utiliser un modèle de projet Visual Studio appelé **Service Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="8e3f7-106">Ce modèle accomplit automatiquement pour vous une grande part du travail : il référence les classes et les espaces de noms appropriés, définit l'héritage à partir de la classe de base des services et substitue les méthodes que vous êtes le plus susceptible de vouloir substituer.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8e3f7-107">Le modèle de projet Services Windows n'est pas disponible dans l'édition Express de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="8e3f7-108">Pour créer un service fonctionnel, vous devez, au minimum :</span><span class="sxs-lookup"><span data-stu-id="8e3f7-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="8e3f7-109">définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ;</span><span class="sxs-lookup"><span data-stu-id="8e3f7-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="8e3f7-110">ajouter les programmes d'installation nécessaires à votre application de service ;</span><span class="sxs-lookup"><span data-stu-id="8e3f7-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="8e3f7-111">substituer et spécifier le code des méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour personnaliser le comportement de votre service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="8e3f7-112">Pour créer une application de service Windows</span><span class="sxs-lookup"><span data-stu-id="8e3f7-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="8e3f7-113">Créez un projet **Service Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e3f7-114">Pour savoir comment écrire un service sans avoir recours au modèle, consultez [Guide pratique pour écrire des services par programmation](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="8e3f7-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="8e3f7-115">Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pour votre service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="8e3f7-116">![Définissez la propriété ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="8e3f7-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e3f7-117">La valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> doit toujours correspondre au nom enregistré dans les classes Installer.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="8e3f7-118">Si vous modifiez cette propriété, vous devez également mettre à jour la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> des classes Installer.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="8e3f7-119">Définissez le fonctionnement de votre service à l'aide des propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="8e3f7-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="8e3f7-120">Property</span></span>|<span data-ttu-id="8e3f7-121">Paramètre</span><span class="sxs-lookup"><span data-stu-id="8e3f7-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="8e3f7-122">`True` pour indiquer que le service acceptera des demandes d'arrêt ; `false` pour empêcher tout arrêt du service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="8e3f7-123">`True` pour indiquer que le service doit recevoir une notification en cas d'arrêt de l'ordinateur sur lequel il s'exécute, ce qui lui permet d'appeler la procédure <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="8e3f7-124">`True` pour indiquer que le service acceptera les demandes de suspension ou de redémarrage ; `false` pour empêcher une suspension et un redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="8e3f7-125">`True` pour indiquer que le service peut gérer la notification des changements apportés à l’état d’alimentation de l’ordinateur ; `false` pour empêcher le service d’être notifié de ces changements.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="8e3f7-126">`True` pour écrire des entrées à caractère informatif dans le journal des événements de l'application lorsque votre service effectue une action ; `false` pour désactiver cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="8e3f7-127">Pour plus d’informations, consultez [Guide pratique pour enregistrer des informations relatives aux services](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e3f7-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="8e3f7-128">**Remarque :** Par défaut, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="8e3f7-129">Quand <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> a la valeur `false`, le **Gestionnaire de contrôle des services** désactive les options de menu correspondantes pour arrêter, suspendre ou poursuivre le service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="8e3f7-130">Accédez à l'éditeur de code et indiquez le traitement souhaité pour les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="8e3f7-131">Substituez toutes les autres méthodes pour lesquelles vous voulez définir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="8e3f7-132">Ajoutez les programmes d'installation nécessaires à votre application de service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="8e3f7-133">Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="8e3f7-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="8e3f7-134">Générez votre projet en sélectionnant **Générer la solution** dans le menu **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e3f7-135">N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="8e3f7-136">Installez le service.</span><span class="sxs-lookup"><span data-stu-id="8e3f7-136">Install the service.</span></span> <span data-ttu-id="8e3f7-137">Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e3f7-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3f7-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e3f7-138">See also</span></span>

- [<span data-ttu-id="8e3f7-139">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="8e3f7-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="8e3f7-140">Procédure : écrire les services par programmation</span><span class="sxs-lookup"><span data-stu-id="8e3f7-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="8e3f7-141">Procédure : ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="8e3f7-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="8e3f7-142">Procédure : enregistrer des informations relatives aux services</span><span class="sxs-lookup"><span data-stu-id="8e3f7-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="8e3f7-143">Procédure : démarrer des services</span><span class="sxs-lookup"><span data-stu-id="8e3f7-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="8e3f7-144">Procédure : spécifier le contexte de sécurité des services</span><span class="sxs-lookup"><span data-stu-id="8e3f7-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="8e3f7-145">Procédure : Installer et désinstaller des services</span><span class="sxs-lookup"><span data-stu-id="8e3f7-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="8e3f7-146">Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="8e3f7-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
