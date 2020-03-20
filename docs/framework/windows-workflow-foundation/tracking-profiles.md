---
title: Modèles de suivi
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9723b8fbb0bb8f24e8c9544d8bac8252b2fc763a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182730"
---
# <a name="tracking-profiles"></a><span data-ttu-id="cd211-102">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="cd211-102">Tracking Profiles</span></span>

<span data-ttu-id="cd211-103">Les profils de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="cd211-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="cd211-104">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="cd211-104">Tracking Profiles</span></span>

<span data-ttu-id="cd211-105">Les modèles de suivi sont utilisés pour indiquer les informations suivi émises pour une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="cd211-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="cd211-106">Si aucun profil n'est spécifié, tous les événements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="cd211-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="cd211-107">Si un profil est spécifié, les événements de suivi spécifiés dans le profil seront émis.</span><span class="sxs-lookup"><span data-stu-id="cd211-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="cd211-108">Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="cd211-109">Inversement, vous pouvez créer un profil très détaillé dont les événements résultants sont assez riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="cd211-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="cd211-110">Les profils de suivi se manifestent sous forme d’éléments XML dans un fichier de configuration cadre .NET standard ou spécifiés dans le code.</span><span class="sxs-lookup"><span data-stu-id="cd211-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="cd211-111">L'exemple suivant illustre un modèle de suivi [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] dans un fichier de configuration qui permet à un participant au suivi de s'abonner aux événements de flux de travail `Started` et `Completed`.</span><span class="sxs-lookup"><span data-stu-id="cd211-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

<span data-ttu-id="cd211-112">L'exemple suivant illustre le modèle de suivi équivalent créé à l'aide du code.</span><span class="sxs-lookup"><span data-stu-id="cd211-112">The following example shows the equivalent tracking profile created using code.</span></span>

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

<span data-ttu-id="cd211-113">Les enregistrements de suivi sont filtrés en mode de visibilité à l'aide de l'attribut <xref:System.Activities.Tracking.ImplementationVisibility> dans un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd211-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="cd211-114">Une activité composite est une activité de niveau supérieur qui contient d'autres activités qui forment son implémentation.</span><span class="sxs-lookup"><span data-stu-id="cd211-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="cd211-115">Le mode de visibilité spécifie les enregistrements de suivi émis à partir d'activités composites dans une activité de flux de travail, afin de définir si les activités qui forment l'implémentation sont suivies.</span><span class="sxs-lookup"><span data-stu-id="cd211-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="cd211-116">Le mode de visibilité s'applique au niveau du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd211-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="cd211-117">Les requêtes dans le modèle de suivi contrôlent le filtrage des enregistrements de suivi pour chaque activité d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="cd211-118">Pour plus d’informations, consultez la section **Tracking Profile Query Types** dans ce document.</span><span class="sxs-lookup"><span data-stu-id="cd211-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="cd211-119">Les deux modes de visibilité spécifiés par l'attribut `implementationVisibility` dans le modèle de suivi sont `RootScope` et `All`.</span><span class="sxs-lookup"><span data-stu-id="cd211-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="cd211-120">Le mode `RootScope` supprime les enregistrements de suivi pour les activités qui forment l'implémentation d'une activité, dans le cas où une activité composite n'est pas la racine d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="cd211-121">Cela implique que, lorsqu'une activité implémentée à l'aide d'autres activités est ajoutée à un flux de travail et que l'attribut `implementationVisibility` est défini sur RootScope, seule l'activité de niveau supérieur dans cette activité composite est suivie.</span><span class="sxs-lookup"><span data-stu-id="cd211-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="cd211-122">Si une activité est la racine du flux de travail, l'implémentation de cette activité est le flux de travail lui-même et les enregistrements de suivi sont émis pour les activités qui forment l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="cd211-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="cd211-123">Le mode All permet d'émettre tous les enregistrements de suivi pour l'activité racine et l'ensemble de ses activités composites.</span><span class="sxs-lookup"><span data-stu-id="cd211-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="cd211-124">Supposons, par exemple, que *MyActivity* soit une activité composite dont la mise en œuvre contient deux activités, *Activité1* et *Activité2*.</span><span class="sxs-lookup"><span data-stu-id="cd211-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="cd211-125">Lorsque cette activité est ajoutée à un flux de travail `implementationVisibility` et `RootScope`le suivi est activé avec un profil de suivi avec défini à , les enregistrements de suivi sont émis uniquement pour *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="cd211-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="cd211-126">Cependant, aucun enregistrement n’est émis pour les activités *Activité1* et *Activité2*.</span><span class="sxs-lookup"><span data-stu-id="cd211-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="cd211-127">Toutefois, si `implementationVisibility` l’attribut pour le `All`profil de suivi est défini, puis les dossiers de suivi sont émis non seulement pour *MyActivity*, mais aussi pour les activités *Activity1* et *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="cd211-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="cd211-128">L'indicateur `implementationVisibility` s'applique aux types d'enregistrements de suivi suivants :</span><span class="sxs-lookup"><span data-stu-id="cd211-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="cd211-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="cd211-129">ActivityStateRecord</span></span>

- <span data-ttu-id="cd211-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="cd211-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="cd211-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="cd211-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="cd211-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="cd211-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="cd211-133">Les enregistrements de suivi CustomTrackingRecord émis à partir de l'implémentation d'une activité ne sont pas éliminés par filtrage par le paramètre implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="cd211-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="cd211-134">Dans le code, la fonctionnalité `implementationVisibility` du modèle de suivi est spécifiée comme suit : <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>.</span><span class="sxs-lookup"><span data-stu-id="cd211-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="cd211-135">Dans un fichier de configuration, la fonctionnalité `implementationVisibility` du modèle de suivi est spécifiée comme suit : <xref:System.Activities.Tracking.ImplementationVisibility.All>.</span><span class="sxs-lookup"><span data-stu-id="cd211-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

<span data-ttu-id="cd211-136">Le paramètre `ImplementationVisibility` du modèle de suivi est facultatif.</span><span class="sxs-lookup"><span data-stu-id="cd211-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="cd211-137">Par défaut, sa valeur est définie sur `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="cd211-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="cd211-138">De plus, les valeurs de cet attribut sont sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="cd211-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="cd211-139">Types de requêtes de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="cd211-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="cd211-140">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="cd211-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="cd211-141">Plusieurs types de requêtes vous permettent de vous abonner à différentes classes d'objets <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="cd211-142">Les profils de suivi peuvent être spécifiés dans la configuration ou via le code.</span><span class="sxs-lookup"><span data-stu-id="cd211-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="cd211-143">Voici les types de requêtes les plus communs :</span><span class="sxs-lookup"><span data-stu-id="cd211-143">Here are the most common query types:</span></span>

- <span data-ttu-id="cd211-144">Objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> - Permet de suivre les changements dans le cycle de vie de l'instance de flux de travail comme les événements `Started` et `Completed` montrés précédemment.</span><span class="sxs-lookup"><span data-stu-id="cd211-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="cd211-145">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="cd211-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="cd211-146">Les états auxquels vous pouvez vous abonner sont spécifiés dans la classe <xref:System.Activities.Tracking.WorkflowInstanceStates>.</span><span class="sxs-lookup"><span data-stu-id="cd211-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="cd211-147">L'exemple suivant indique la configuration ou le code servant à s'abonner aux enregistrements de suivi de flux de travail au niveau de l'instance, pour l'état de l'instance `Started`, à l'aide de l'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery>.</span><span class="sxs-lookup"><span data-stu-id="cd211-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <span data-ttu-id="cd211-148">Objet <xref:System.Activities.Tracking.ActivityStateQuery> - Permet de suivre les changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="cd211-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cd211-149">Par exemple, vous pouvez garder une trace de chaque fois que l’activité « Envoyer un e-mail » se termine dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cd211-150">Cette requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.ActivityStateRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="cd211-151">Les états disponibles auxquels s'abonner sont spécifiés dans l'objet <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="cd211-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="cd211-152">L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements de suivi d'état d'activité qui utilisent l'objet <xref:System.Activities.Tracking.ActivityStateQuery> pour l'activité `SendEmailActivity`.</span><span class="sxs-lookup"><span data-stu-id="cd211-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > <span data-ttu-id="cd211-153">Si plusieurs éléments activityStateQuery ont le même nom, seuls les états dans le dernier élément sont utilisés dans le modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd211-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="cd211-154">Objet <xref:System.Activities.Tracking.ActivityScheduledQuery> - Cette requête vous permet de suivre une activité devant être exécutée par une activité parente.</span><span class="sxs-lookup"><span data-stu-id="cd211-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cd211-155">La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.ActivityScheduledRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="cd211-156">L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à l'activité enfant `SendEmailActivity` en cours de planification, à l'aide de l'objet <xref:System.Activities.Tracking.ActivityScheduledQuery>.</span><span class="sxs-lookup"><span data-stu-id="cd211-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="cd211-157">Objet <xref:System.Activities.Tracking.FaultPropagationQuery> - Permet de suivre la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="cd211-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="cd211-158">La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="cd211-159">L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à la propagation d'erreur à l'aide de l'objet <xref:System.Activities.Tracking.FaultPropagationQuery>.</span><span class="sxs-lookup"><span data-stu-id="cd211-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <span data-ttu-id="cd211-160">Objet <xref:System.Activities.Tracking.CancelRequestedQuery> - Permet de suivre les demandes d'annulation d'une activité enfant par l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="cd211-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cd211-161">La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.CancelRequestedRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="cd211-162">La configuration et le code utilisés pour <xref:System.Activities.Tracking.CancelRequestedQuery> s’abonner aux enregistrements liés à l’annulation d’activité à l’aide sont indiqués dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cd211-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="cd211-163">Objet <xref:System.Activities.Tracking.CustomTrackingQuery> - Permet de suivre les événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="cd211-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="cd211-164">La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.CustomTrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="cd211-165">L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés aux enregistrements de suivi personnalisé à l'aide de l'objet <xref:System.Activities.Tracking.CustomTrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="cd211-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="cd211-166">Objet <xref:System.Activities.Tracking.BookmarkResumptionQuery> - Permet de suivre la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cd211-167">Cette requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.BookmarkResumptionRecord>.</span><span class="sxs-lookup"><span data-stu-id="cd211-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="cd211-168">L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à la reprise de signet à l'aide de l'objet <xref:System.Activities.Tracking.BookmarkResumptionQuery>.</span><span class="sxs-lookup"><span data-stu-id="cd211-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a><span data-ttu-id="cd211-169">Annotations</span><span class="sxs-lookup"><span data-stu-id="cd211-169">Annotations</span></span>

<span data-ttu-id="cd211-170">Grâce aux annotations, vous pouvez baliser arbitrairement des enregistrements de suivi avec une valeur configurable après la génération.</span><span class="sxs-lookup"><span data-stu-id="cd211-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="cd211-171">Par exemple, vous pouvez vouloir que plusieurs enregistrements de suivi sur plusieurs flux de travail soient étiquetés avec "Mail Server" -"Mail Server1".</span><span class="sxs-lookup"><span data-stu-id="cd211-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="cd211-172">Lors de l’interrogation ultérieure d’enregistrements de suivi, cela facilite la recherche de tous les enregistrements ayant cette étiquette.</span><span class="sxs-lookup"><span data-stu-id="cd211-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="cd211-173">Pour ce faire, une annotation est ajoutée à une requête de suivi comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cd211-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="cd211-174">Création d'un modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="cd211-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="cd211-175">Les éléments de requête de suivi sont utilisés pour créer [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] un profil de suivi à l’aide d’un fichier de configuration XML ou d’un code.</span><span class="sxs-lookup"><span data-stu-id="cd211-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="cd211-176">Voici un exemple de modèle de suivi créé à l'aide d'un fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="cd211-176">Here is an example of a tracking profile created using a configuration file.</span></span>

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> <span data-ttu-id="cd211-177">Pour un WF utilisant l'hôte du service de flux de travail, le modèle de suivi est généralement créé à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cd211-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="cd211-178">Mais il peut également être créé avec le code, à l'aide de l'API de modèle de suivi et de requête de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd211-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="cd211-179">Un profil configuré en tant que fichier de configuration XML est appliqué à un participant au suivi à l’aide d’une extension de comportement.</span><span class="sxs-lookup"><span data-stu-id="cd211-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="cd211-180">Ceci est ajouté à un WorkflowServiceHost tel que décrit dans la section ultérieure [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="cd211-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="cd211-181">Les paramètres de configuration du modèle de suivi déterminent les commentaires des enregistrements de suivi émis par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="cd211-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="cd211-182">Un participant au suivi s'abonne à des enregistrements de suivi en ajoutant des requêtes à un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd211-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="cd211-183">Pour s’abonner à tous les enregistrements de suivi, le profil de suivi doit spécifier toutes les requêtes de suivi en utilisant "\*dans les champs de nom dans chacune des requêtes.</span><span class="sxs-lookup"><span data-stu-id="cd211-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="cd211-184">Voici quelques exemples communs de profils de suivi :</span><span class="sxs-lookup"><span data-stu-id="cd211-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="cd211-185">Modèle de suivi permettant d'obtenir les enregistrements et les erreurs de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd211-185">A tracking profile to obtain workflow instance records and faults.</span></span>

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- <span data-ttu-id="cd211-186">Modèle de suivi permettant d'obtenir tous les enregistrements de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cd211-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="cd211-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd211-187">See also</span></span>

- [<span data-ttu-id="cd211-188">Suivi SQL</span><span class="sxs-lookup"><span data-stu-id="cd211-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="cd211-189">[Surveillance du tissu de l’application Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cd211-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="cd211-190">[Surveillance des applications avec le tissu d’application](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cd211-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
