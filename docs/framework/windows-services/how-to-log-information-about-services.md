---
title: 'Procédure : enregistrer des informations relatives aux services'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: 1ffc698910fe722fe761c62b87b059068d5f243f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935519"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="4f1b9-102">Procédure : enregistrer des informations relatives aux services</span><span class="sxs-lookup"><span data-stu-id="4f1b9-102">How to: Log Information About Services</span></span>
<span data-ttu-id="4f1b9-103">Par défaut, tous les projets de service Windows ont la possibilité d’interagir avec le journal d’événements des applications et d’y écrire des informations et des exceptions.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="4f1b9-104">Vous utilisez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour indiquer si vous souhaitez cette fonctionnalité dans votre application.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="4f1b9-105">Par défaut, la journalisation est activée pour tout service que vous créez avec le modèle de projet de service Windows.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="4f1b9-106">Vous pouvez utiliser un formulaire statique de la classe <xref:System.Diagnostics.EventLog> pour écrire des informations de service dans un journal sans avoir à créer une instance d’un composant <xref:System.Diagnostics.EventLog> ou inscrire manuellement une source.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="4f1b9-107">Le programme d’installation de votre service inscrit automatiquement chaque service de votre projet comme source valide d’événements dans le journal des applications sur l’ordinateur où le service est installé, quand la journalisation est activée.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="4f1b9-108">Le service enregistre des informations chaque fois que le service est démarré, arrêté, suspendu, repris, installé ou désinstallé.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="4f1b9-109">Il enregistre également tous les échecs qui se produisent.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-109">It also logs any failures that occur.</span></span> <span data-ttu-id="4f1b9-110">Vous n’avez pas besoin d’écrire du code pour écrire des entrées dans le journal quand vous utilisez le comportement par défaut. Le service le gère pour vous automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="4f1b9-111">Si vous souhaitez écrire dans un journal d’événements autre que le journal des applications, vous devez définir la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> sur `false`, créer votre propre journal d’événements personnalisé dans le code de vos services et inscrire votre service en tant que source valide d’entrées de ce journal.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="4f1b9-112">Vous devez ensuite écrire le code nécessaire pour enregistrer des entrées dans le journal chaque fois qu’une action qui vous intéresse se produit.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f1b9-113">Si vous utilisez un journal d’événements personnalisé et configurez votre application de service pour qu’elle écrive dans ce journal, vous ne devez pas tenter d’accéder au journal d’événements avant de définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> du service dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="4f1b9-114">Le journal des événements a besoin de la valeur de cette propriété pour inscrire votre service en tant que source d’événements valide.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="4f1b9-115">Pour activer la journalisation des événements par défaut pour votre service</span><span class="sxs-lookup"><span data-stu-id="4f1b9-115">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="4f1b9-116">Définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour votre composant sur `true`.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f1b9-117">Par défaut, cette propriété est définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="4f1b9-118">Vous n’avez pas besoin de la définir explicitement, sauf si vous générez un traitement plus complexe, comme l’évaluation d’une condition, puis que vous définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> en fonction du résultat de cette condition.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="4f1b9-119">Pour désactiver la journalisation des événements pour votre service</span><span class="sxs-lookup"><span data-stu-id="4f1b9-119">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="4f1b9-120">Définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour votre composant sur `false`.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="4f1b9-121">Pour configurer l’enregistrement dans un journal personnalisé</span><span class="sxs-lookup"><span data-stu-id="4f1b9-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="4f1b9-122">Affectez à la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f1b9-123">Vous devez définir <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> sur false pour utiliser un journal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="4f1b9-124">Configurez une instance d’un composant <xref:System.Diagnostics.EventLog> dans votre application de service Windows.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="4f1b9-125">Créez un journal personnalisé en appelant la méthode <xref:System.Diagnostics.EventLog.CreateEventSource%2A> et en spécifiant la chaîne source et le nom du fichier journal que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="4f1b9-126">Définissez la propriété <xref:System.Diagnostics.EventLog.Source%2A> dans l’instance du composant <xref:System.Diagnostics.EventLog> sur la chaîne source que vous avez créée à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="4f1b9-127">Écrivez vos entrées en accédant à la méthode <xref:System.Diagnostics.EventLog.WriteEntry%2A> dans l’instance du composant <xref:System.Diagnostics.EventLog> .</span><span class="sxs-lookup"><span data-stu-id="4f1b9-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="4f1b9-128">Le code suivant montre comment configurer l’enregistrement dans un journal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f1b9-129">Dans cet exemple de code, une instance d’un composant <xref:System.Diagnostics.EventLog> est appelée `eventLog1` (`EventLog1` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4f1b9-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="4f1b9-130">Si vous avez créé une instance avec un autre nom à l’étape 2, modifiez le code en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4f1b9-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4f1b9-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f1b9-131">See also</span></span>

- [<span data-ttu-id="4f1b9-132">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="4f1b9-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
