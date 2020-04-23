---
title: 'Comment : démarrer des services'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 75fd3aba88bdffbe536ad5dab14996913d0a9d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053568"
---
# <a name="how-to-start-services"></a><span data-ttu-id="e2056-102">Comment : démarrer des services</span><span class="sxs-lookup"><span data-stu-id="e2056-102">How to: Start Services</span></span>

<span data-ttu-id="e2056-103">Une fois qu’un service est installé, il doit être démarré.</span><span class="sxs-lookup"><span data-stu-id="e2056-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="e2056-104">Le démarrage appelle la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> sur la classe de service.</span><span class="sxs-lookup"><span data-stu-id="e2056-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="e2056-105">En règle générale, la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> définit le travail utile effectué par le service.</span><span class="sxs-lookup"><span data-stu-id="e2056-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="e2056-106">Une fois un service démarré, il reste actif jusqu’à ce qu’il soit suspendu ou arrêté.</span><span class="sxs-lookup"><span data-stu-id="e2056-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="e2056-107">Vous pouvez configurer un service pour qu’il démarre automatiquement ou manuellement.</span><span class="sxs-lookup"><span data-stu-id="e2056-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="e2056-108">Un service à démarrage automatique démarre quand l’ordinateur sur lequel il est installé est mis en marche pour la première fois ou redémarré.</span><span class="sxs-lookup"><span data-stu-id="e2056-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="e2056-109">Un service à démarrage manuel doit être démarré par un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2056-109">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="e2056-110">Par défaut, les services créés avec Visual Studio sont définis pour démarrer manuellement.</span><span class="sxs-lookup"><span data-stu-id="e2056-110">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="e2056-111">Vous pouvez démarrer manuellement un service de plusieurs façons : à partir de **l’Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services** ou à partir du code à l’aide d’un composant appelé <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="e2056-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="e2056-112">Pour indiquer si un service doit être démarré manuellement ou automatiquement, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> sur la classe <xref:System.ServiceProcess.ServiceInstaller>.</span><span class="sxs-lookup"><span data-stu-id="e2056-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="e2056-113">Pour spécifier comment un service doit démarrer</span><span class="sxs-lookup"><span data-stu-id="e2056-113">To specify how a service should start</span></span>

1. <span data-ttu-id="e2056-114">Après avoir créé votre service, ajoutez les programmes d’installation nécessaires à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e2056-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="e2056-115">Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="e2056-115">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="e2056-116">Dans le concepteur, cliquez sur le programme d’installation du service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e2056-116">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="e2056-117">Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> avec l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e2056-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="e2056-118">Pour que votre service s’installe</span><span class="sxs-lookup"><span data-stu-id="e2056-118">To have your service install</span></span>|<span data-ttu-id="e2056-119">Définissez cette valeur</span><span class="sxs-lookup"><span data-stu-id="e2056-119">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="e2056-120">Quand l’ordinateur redémarre</span><span class="sxs-lookup"><span data-stu-id="e2056-120">When the computer is restarted</span></span>|<span data-ttu-id="e2056-121">**Automatique**</span><span class="sxs-lookup"><span data-stu-id="e2056-121">**Automatic**</span></span>|
    |<span data-ttu-id="e2056-122">Quand une action explicite de l’utilisateur démarre le service</span><span class="sxs-lookup"><span data-stu-id="e2056-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="e2056-123">**Manuel**</span><span class="sxs-lookup"><span data-stu-id="e2056-123">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="e2056-124">Pour que votre service ne démarre pas, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> avec la valeur **Disabled**.</span><span class="sxs-lookup"><span data-stu-id="e2056-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="e2056-125">Procédez de la sorte si vous prévoyez de redémarrer un serveur plusieurs fois. Le fait de ne pas démarrer les services habituels vous fera gagner du temps.</span><span class="sxs-lookup"><span data-stu-id="e2056-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2056-126">Ces propriétés, ainsi que d’autres, peuvent être modifiées après l’installation du service.</span><span class="sxs-lookup"><span data-stu-id="e2056-126">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="e2056-127">Vous pouvez démarrer un service dont le processus <xref:System.ServiceProcess.ServiceInstaller.StartType%2A>a la valeur **Manual** de plusieurs façons : à partir de **l’Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services Windows** ou à partir du code.</span><span class="sxs-lookup"><span data-stu-id="e2056-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="e2056-128">Il est important de noter que ces méthodes ne démarrent pas toutes le service dans le contexte du **Gestionnaire de contrôle des services**. En effet, **l’Explorateur de serveurs** et les méthodes de démarrage du service par programmation manipulent le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="e2056-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="e2056-129">Pour démarrer manuellement un service à partir de l’Explorateur de serveurs</span><span class="sxs-lookup"><span data-stu-id="e2056-129">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="e2056-130">Dans **l’Explorateur de serveurs**, ajoutez le serveur désiré s’il n’est pas déjà répertorié.</span><span class="sxs-lookup"><span data-stu-id="e2056-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="e2056-131">Pour plus d’informations, consultez Guide pratique pour accéder à l’Explorateur de serveurs/bases de données et l’initialiser.</span><span class="sxs-lookup"><span data-stu-id="e2056-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="e2056-132">Développez le nœud **Services**, puis recherchez le service à démarrer.</span><span class="sxs-lookup"><span data-stu-id="e2056-132">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="e2056-133">Cliquez avec le bouton droit sur le nom du service, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="e2056-133">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="e2056-134">Pour démarrer manuellement un service à partir du Gestionnaire de contrôle des services</span><span class="sxs-lookup"><span data-stu-id="e2056-134">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="e2056-135">Effectuez l’une des procédures suivantes pour ouvrir le **Gestionnaire de contrôle des services** :</span><span class="sxs-lookup"><span data-stu-id="e2056-135">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="e2056-136">Dans Windows XP et Windows 2000 Professionnel, cliquez avec le bouton droit sur **Poste de travail** sur le Bureau, puis cliquez sur **Gérer**.</span><span class="sxs-lookup"><span data-stu-id="e2056-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="e2056-137">Dans la boîte de dialogue qui s’affiche, développez le nœud **Services et applications**.</span><span class="sxs-lookup"><span data-stu-id="e2056-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="e2056-138">\- ou -</span><span class="sxs-lookup"><span data-stu-id="e2056-138">\- or -</span></span>

    - <span data-ttu-id="e2056-139">Dans Windows Server 2003 et Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **Programmes**, puis cliquez sur **Outils d’administration** et sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="e2056-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="e2056-140">Dans Windows NT version 4.0, vous pouvez ouvrir cette boîte de dialogue à partir du **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="e2056-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="e2056-141">Votre service doit maintenant être répertorié dans la section **Services** de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e2056-141">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="e2056-142">Sélectionnez votre service dans la liste, cliquez dessus avec le bouton droit, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="e2056-142">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="e2056-143">Pour démarrer manuellement un service à partir du code</span><span class="sxs-lookup"><span data-stu-id="e2056-143">To manually start a service from code</span></span>

1. <span data-ttu-id="e2056-144">Créez une instance de la classe <xref:System.ServiceProcess.ServiceController> et configurez-la pour interagir avec le service à administrer.</span><span class="sxs-lookup"><span data-stu-id="e2056-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="e2056-145">Appelez la méthode <xref:System.ServiceProcess.ServiceController.Start%2A> pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="e2056-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2056-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2056-146">See also</span></span>

- [<span data-ttu-id="e2056-147">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="e2056-147">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="e2056-148">Guide pratique pour créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="e2056-148">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="e2056-149">Comment : ajouter des programmes d'installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="e2056-149">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
