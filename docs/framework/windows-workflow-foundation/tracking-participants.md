---
title: Participants de suivi
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 9455524da4451bf904d8449412e8f625542a1635
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551450"
---
# <a name="tracking-participants"></a><span data-ttu-id="444de-102">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="444de-102">Tracking Participants</span></span>
<span data-ttu-id="444de-103">Les participants de traçage sont des points d'extensibilité qui permettent à un développeur de workflow d'accéder aux objets <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> et de les traiter.</span><span class="sxs-lookup"><span data-stu-id="444de-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="444de-104">inclut un participant de trace standard qui écrit des enregistrements de suivi en tant qu'événements de suivi d'événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="444de-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="444de-105">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="444de-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="444de-106">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="444de-106">Tracking Participants</span></span>  
 <span data-ttu-id="444de-107">L'infrastructure de suivi permet l'application d'un filtre sur les enregistrements de suivi sortants pour permettre à un participant de s'abonner à un sous-ensemble des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="444de-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="444de-108">L'application d'un filtre s'effectue par l'intermédiaire d'un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="444de-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="444de-109">Windows Workflow Foundation (WF) dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fournit un participant de suivi qui écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="444de-110">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="444de-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="444de-111">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="444de-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="444de-112">L'exemple du Kit de développement logiciel pour le suivi ETW constitue un bon moyen de se familiariser avec le suivi WF à l'aide du participant de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="444de-113">Participant de suivi ETW</span><span class="sxs-lookup"><span data-stu-id="444de-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="444de-114">inclut un participant de suivi ETW qui écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="444de-115">Cette opération est effectuée de façon très efficace avec un impact minimal sur les performances de l'application ou sur le débit du serveur.</span><span class="sxs-lookup"><span data-stu-id="444de-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="444de-116">L'un des avantages de l'utilisation du participant de suivi ETW standard est que les enregistrements de suivi qu'il reçoit peuvent être affichés avec l'autre application et les journaux système dans l'observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="444de-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="444de-117">Le participant de suivi ETW standard est configuré dans le fichier Web.config comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="444de-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="444de-118">Si un nom `trackingProfile` n'est pas spécifié, par exemple seulement `<etwTracking/>` ou `<etwTracking profileName=""/>`, le modèle de suivi par défaut installé avec [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dans le fichier Machine.config est utilisé.</span><span class="sxs-lookup"><span data-stu-id="444de-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="444de-119">Dans le fichier Machine.config, le modèle de suivi par défaut s'abonne aux enregistrements et aux erreurs de l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="444de-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="444de-120">Dans ETW, les événements sont écrits dans la session ETW via un ID de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="444de-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="444de-121">L'ID de fournisseur que le participant de suivi ETW utilise pour écrire les enregistrements de suivi dans ETW est défini dans la section de diagnostic du fichier Web.config (sous `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="444de-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="444de-122">Par défaut, le participant de suivi ETW utilise un ID de fournisseur par défaut si aucun ID n'a pas été spécifié, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="444de-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="444de-123">L'illustration suivante montre le flux des données de suivi via le participant de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="444de-124">Une fois que les données de suivi ont atteint la session ETW, il est possible d'y accéder de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="444de-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="444de-125">L'observateur d'événements, un outil Windows courant utilisé pour l'affichage des journaux et des suivis provenant d'applications et de services constitue l'un des moyens les plus pratiques pour accéder à ces événements.</span><span class="sxs-lookup"><span data-stu-id="444de-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![L’acheminement des données de suivi via le fournisseur de suivi ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="444de-127">Données d'événement des participants de suivi</span><span class="sxs-lookup"><span data-stu-id="444de-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="444de-128">Un participant de suivi sérialise les données d'événement ayant fait l'objet d'un suivi dans une session ETW sous la forme d'un événement par enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="444de-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="444de-129">Un événement est identifié à l'aide d'un ID compris entre 100 et 199.</span><span class="sxs-lookup"><span data-stu-id="444de-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="444de-130">Pour obtenir les définitions des enregistrements d’événement de suivi émis par un participant de suivi, consultez la rubrique de référence sur les [événements](tracking-events-reference.md) de suivi.</span><span class="sxs-lookup"><span data-stu-id="444de-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="444de-131">La taille d'un événement ETW est limitée par la taille de la mémoire tampon ETW, ou par la charge utile maximale pour un événement ETW, selon la valeur la plus petite.</span><span class="sxs-lookup"><span data-stu-id="444de-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="444de-132">Si la taille de l'événement dépasse l'une ou l'autre de ces limites ETW, l'événement est tronqué et son contenu supprimé de façon arbitraire.</span><span class="sxs-lookup"><span data-stu-id="444de-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="444de-133">Les variables, arguments, annotations et données personnalisées ne sont pas supprimés de manière sélective.</span><span class="sxs-lookup"><span data-stu-id="444de-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="444de-134">Dans le cas de troncation, tous ces éléments sont tronqués indépendamment de la valeur à l'origine du dépassement de la limite ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="444de-135">Les données supprimées sont remplacées par `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="444de-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="444de-136">Les types complexes dans les variables, les arguments et les éléments de données personnalisés sont sérialisés dans l’enregistrement d’événement ETW à l’aide de la <xref:System.Runtime.Serialization.NetDataContractSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="444de-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="444de-137">Cette classe inclut les informations de type CLR dans le flux XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="444de-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="444de-138">La troncation des données de charge utile en raison de limites ETW peut provoquer l'envoi d'enregistrements de suivi en double à une session ETW.</span><span class="sxs-lookup"><span data-stu-id="444de-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="444de-139">Cela peut se produire si plusieurs sessions écoutent les événements et si ces sessions ont des limites de charge utile différentes pour les événements.</span><span class="sxs-lookup"><span data-stu-id="444de-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="444de-140">Pour la session ayant la limite inférieure, l'événement peut être tronqué.</span><span class="sxs-lookup"><span data-stu-id="444de-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="444de-141">Le participant de suivi ETW ne connaît pas le nombre de sessions qui écoutent les événements ; si un événement est tronqué pour une session, le participant ETW essaie à nouveau d'envoyer l'événement.</span><span class="sxs-lookup"><span data-stu-id="444de-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="444de-142">Dans ce cas, la session configurée pour accepter une charge utile plus importante recevra l'événement deux fois (l'événement non tronqué et l'événement tronqué).</span><span class="sxs-lookup"><span data-stu-id="444de-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="444de-143">La duplication peut être évitée en configurant toutes les sessions ETW avec les mêmes limites de taille de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="444de-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="444de-144">Accès aux données de suivi d'un participant ETW dans l'observateur d'événements</span><span class="sxs-lookup"><span data-stu-id="444de-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="444de-145">Les événements écrits dans une session ETW par le participant de suivi ETW sont accessibles par le biais de l'observateur d'événements (lors de l'utilisation de l'ID de fournisseur par défaut).</span><span class="sxs-lookup"><span data-stu-id="444de-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="444de-146">Cela permet d'afficher rapidement les enregistrements de suivi émis par le workflow.</span><span class="sxs-lookup"><span data-stu-id="444de-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="444de-147">Les événements d'enregistrement de suivi émis vers une session ETW utilisent des ID d'événement compris entre 100 et 199.</span><span class="sxs-lookup"><span data-stu-id="444de-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="444de-148">Pour activer l'affichage des enregistrements de suivi dans l'observateur d'événements</span><span class="sxs-lookup"><span data-stu-id="444de-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="444de-149">Démarrez l'observateur d'événements (EVENTVWR.EXE).</span><span class="sxs-lookup"><span data-stu-id="444de-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="444de-150">Sélectionnez **Observateur d’événements, journaux des applications et des services, Microsoft, Windows, serveur d’applications-applications**.</span><span class="sxs-lookup"><span data-stu-id="444de-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="444de-151">Cliquez avec le bouton droit et vérifiez que **afficher, afficher les journaux d’analyse et de débogage** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="444de-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="444de-152">Si tel n'est pas le cas, activez cette case à cocher de façon à ce que la coche apparaisse en regard de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="444de-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="444de-153">Les journaux d' **analyse**, de **performances**et de **débogage** s’affichent.</span><span class="sxs-lookup"><span data-stu-id="444de-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="444de-154">Cliquez avec le bouton droit sur le journal d' **analyse** , puis sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="444de-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="444de-155">Le journal existera dans le fichier %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl.</span><span class="sxs-lookup"><span data-stu-id="444de-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="444de-156">Participant de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="444de-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="444de-157">L’API de participant de suivi permet l’extension de l’exécution du suivi avec un participant de suivi fourni par l’utilisateur, qui peut inclure une logique personnalisée permettant de gérer les enregistrements de suivi émis par l’exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="444de-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="444de-158">Pour écrire un participant de suivi personnalisé, le développeur doit implémenter la méthode `Track` sur la classe <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="444de-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="444de-159">Cette méthode est appelée lorsqu'un enregistrement de suivi est émis par l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="444de-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="444de-160">Les participants de suivi dérivent de la classe <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="444de-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="444de-161">Le <xref:System.Activities.Tracking.EtwTrackingParticipant> fourni par le système émet un événement de suivi des événements pour Windows pour chaque enregistrement de suivi reçu.</span><span class="sxs-lookup"><span data-stu-id="444de-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="444de-162">Pour créer un participant de suivi personnalisé, une classe qui dérive de <xref:System.Activities.Tracking.TrackingParticipant> est créée.</span><span class="sxs-lookup"><span data-stu-id="444de-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="444de-163">Pour fournir des fonctionnalités de suivi de base, substituez <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="444de-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="444de-164">La méthode <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> est appelée lorsqu'un enregistrement de suivi est transmis par l'exécution et qu'il peut être traité de la manière souhaitée.</span><span class="sxs-lookup"><span data-stu-id="444de-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="444de-165">Dans l'exemple suivant, une classe de participant de suivi personnalisé émettant tous les enregistrements de suivi vers la fenêtre de console est définie.</span><span class="sxs-lookup"><span data-stu-id="444de-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="444de-166">Vous pouvez également implémenter un objet <xref:System.Activities.Tracking.TrackingParticipant> qui traite les enregistrements de suivi de façon asynchrone à l'aide de ses méthodes `BeginTrack` et `EndTrack`.</span><span class="sxs-lookup"><span data-stu-id="444de-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="444de-167">Pour utiliser un participant de suivi particulier, enregistrez-le avec l'instance de workflow que vous souhaitez suivre, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="444de-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="444de-168">Dans l'exemple suivant, un workflow consistant en une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> est créé.</span><span class="sxs-lookup"><span data-stu-id="444de-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="444de-169">`ConsoleTrackingParticipant` est ajouté aux extensions et le workflow est appelé.</span><span class="sxs-lookup"><span data-stu-id="444de-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="444de-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="444de-170">See also</span></span>

- <span data-ttu-id="444de-171">[Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="444de-171">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="444de-172">[Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="444de-172">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
