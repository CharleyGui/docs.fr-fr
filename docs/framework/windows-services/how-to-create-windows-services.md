---
title: 'Comment : créer des services Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 514675b3c3ce1f6701dff571361df672fb520c6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053658"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="182ac-102">Comment : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="182ac-102">How to: Create Windows Services</span></span>
<span data-ttu-id="182ac-103">Quand vous créez un service, vous pouvez utiliser un modèle de projet Visual Studio appelé **Service Windows**.</span><span class="sxs-lookup"><span data-stu-id="182ac-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="182ac-104">Ce modèle accomplit automatiquement pour vous une grande part du travail : il référence les classes et les espaces de noms appropriés, définit l'héritage à partir de la classe de base des services et substitue les méthodes que vous êtes le plus susceptible de vouloir substituer.</span><span class="sxs-lookup"><span data-stu-id="182ac-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="182ac-105">Le modèle de projet Services Windows n'est pas disponible dans l'édition Express de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="182ac-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="182ac-106">Pour créer un service fonctionnel, vous devez, au minimum :</span><span class="sxs-lookup"><span data-stu-id="182ac-106">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="182ac-107">définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ;</span><span class="sxs-lookup"><span data-stu-id="182ac-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="182ac-108">ajouter les programmes d'installation nécessaires à votre application de service ;</span><span class="sxs-lookup"><span data-stu-id="182ac-108">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="182ac-109">substituer et spécifier le code des méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour personnaliser le comportement de votre service.</span><span class="sxs-lookup"><span data-stu-id="182ac-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="182ac-110">Pour créer une application de service Windows</span><span class="sxs-lookup"><span data-stu-id="182ac-110">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="182ac-111">Créez un projet **Service Windows**.</span><span class="sxs-lookup"><span data-stu-id="182ac-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="182ac-112">Pour savoir comment écrire un service sans avoir recours au modèle, consultez [Guide pratique pour écrire des services par programmation](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="182ac-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="182ac-113">Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pour votre service.</span><span class="sxs-lookup"><span data-stu-id="182ac-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="182ac-114">![Définissez la propriété ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="182ac-114">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="182ac-115">La valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> doit toujours correspondre au nom enregistré dans les classes Installer.</span><span class="sxs-lookup"><span data-stu-id="182ac-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="182ac-116">Si vous modifiez cette propriété, vous devez également mettre à jour la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> des classes Installer.</span><span class="sxs-lookup"><span data-stu-id="182ac-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="182ac-117">Définissez le fonctionnement de votre service à l'aide des propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="182ac-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="182ac-118">Propriété</span><span class="sxs-lookup"><span data-stu-id="182ac-118">Property</span></span>|<span data-ttu-id="182ac-119">Paramètre</span><span class="sxs-lookup"><span data-stu-id="182ac-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="182ac-120">`True` pour indiquer que le service acceptera des demandes d'arrêt ; `false` pour empêcher tout arrêt du service.</span><span class="sxs-lookup"><span data-stu-id="182ac-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="182ac-121">`True` pour indiquer que le service doit recevoir une notification en cas d'arrêt de l'ordinateur sur lequel il s'exécute, ce qui lui permet d'appeler la procédure <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="182ac-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="182ac-122">`True` pour indiquer que le service acceptera les demandes de suspension ou de redémarrage ; `false` pour empêcher une suspension et un redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="182ac-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="182ac-123">`True` pour indiquer que le service peut gérer la notification des changements apportés à l’état d’alimentation de l’ordinateur ; `false` pour empêcher le service d’être notifié de ces changements.</span><span class="sxs-lookup"><span data-stu-id="182ac-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="182ac-124">`True` pour écrire des entrées à caractère informatif dans le journal des événements de l'application lorsque votre service effectue une action ; `false` pour désactiver cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="182ac-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="182ac-125">Pour plus d’informations, consultez [Guide pratique pour enregistrer des informations relatives aux services](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="182ac-125">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="182ac-126">**Remarque :** Par défaut, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="182ac-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="182ac-127">Quand <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> a la valeur `false`, le **Gestionnaire de contrôle des services** désactive les options de menu correspondantes pour arrêter, suspendre ou poursuivre le service.</span><span class="sxs-lookup"><span data-stu-id="182ac-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="182ac-128">Accédez à l'éditeur de code et indiquez le traitement souhaité pour les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="182ac-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="182ac-129">Substituez toutes les autres méthodes pour lesquelles vous voulez définir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="182ac-129">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="182ac-130">Ajoutez les programmes d'installation nécessaires à votre application de service.</span><span class="sxs-lookup"><span data-stu-id="182ac-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="182ac-131">Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="182ac-131">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="182ac-132">Générez votre projet en sélectionnant **Générer la solution** dans le menu **Générer**.</span><span class="sxs-lookup"><span data-stu-id="182ac-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="182ac-133">N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.</span><span class="sxs-lookup"><span data-stu-id="182ac-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="182ac-134">Installez le service.</span><span class="sxs-lookup"><span data-stu-id="182ac-134">Install the service.</span></span> <span data-ttu-id="182ac-135">Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="182ac-135">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182ac-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="182ac-136">See also</span></span>

- [<span data-ttu-id="182ac-137">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="182ac-137">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="182ac-138">Guide pratique pour écrire les services par programmation</span><span class="sxs-lookup"><span data-stu-id="182ac-138">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="182ac-139">Comment : ajouter des programmes d'installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="182ac-139">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="182ac-140">Comment : enregistrer des informations relatives aux services</span><span class="sxs-lookup"><span data-stu-id="182ac-140">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="182ac-141">Guide pratique pour démarrer des services</span><span class="sxs-lookup"><span data-stu-id="182ac-141">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="182ac-142">Comment : spécifier le contexte de sécurité des services</span><span class="sxs-lookup"><span data-stu-id="182ac-142">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="182ac-143">Guide pratique pour installer et désinstaller des services</span><span class="sxs-lookup"><span data-stu-id="182ac-143">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="182ac-144">Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="182ac-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
