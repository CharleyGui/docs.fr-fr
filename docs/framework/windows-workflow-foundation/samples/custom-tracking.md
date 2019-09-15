---
title: Suivi personnalisé
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 32abf1dc4c9607b4a86f836fa2c759af1dbf1b69
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989412"
---
# <a name="custom-tracking"></a><span data-ttu-id="ecdef-102">Suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="ecdef-102">Custom Tracking</span></span>
<span data-ttu-id="ecdef-103">Cet exemple montre comment créer un participant de suivi personnalisé et écrire le contenu des données de suivi sur la console.</span><span class="sxs-lookup"><span data-stu-id="ecdef-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="ecdef-104">De plus, il montre comment émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> remplis avec des données définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ecdef-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="ecdef-105">Le participant de suivi basé sur la console filtre les objets <xref:System.Activities.Tracking.TrackingRecord> émis par le workflow à l'aide d'un objet de modèle de suivi créé dans le code.</span><span class="sxs-lookup"><span data-stu-id="ecdef-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="ecdef-106">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ecdef-106">Sample Details</span></span>
 <span data-ttu-id="ecdef-107">Windows Workflow Foundation (WF) fournit une infrastructure de suivi pour suivre l’exécution d’une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="ecdef-108">Le runtime de suivi implémente une instance de workflow pour émettre des événements liés au cycle de vie du workflow, des événements des activités de workflow et des événements de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ecdef-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="ecdef-109">Le tableau suivant détaille les composants principaux de l'infrastructure de suivi.</span><span class="sxs-lookup"><span data-stu-id="ecdef-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="ecdef-110">Composant</span><span class="sxs-lookup"><span data-stu-id="ecdef-110">Component</span></span>|<span data-ttu-id="ecdef-111">Description</span><span class="sxs-lookup"><span data-stu-id="ecdef-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ecdef-112">Runtime de suivi</span><span class="sxs-lookup"><span data-stu-id="ecdef-112">Tracking runtime</span></span>|<span data-ttu-id="ecdef-113">Fournit l'infrastructure permettant d'émettre des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ecdef-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="ecdef-114">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="ecdef-114">Tracking participants</span></span>|<span data-ttu-id="ecdef-115">Consomme les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ecdef-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] <span data-ttu-id="ecdef-116">est fourni avec un participant de suivi qui écrit les enregistrements de suivi sous la forme d'événements Suivi d'événements pour Windows (ETW, Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="ecdef-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="ecdef-117">Modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="ecdef-117">Tracking profile</span></span>|<span data-ttu-id="ecdef-118">Mécanisme de filtrage qui permet à un participant de suivi de s'abonner à un sous-ensemble des enregistrements de suivi émis à partir d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="ecdef-119">Le tableau suivant détaille les enregistrements de suivi que l'exécution de workflow émet.</span><span class="sxs-lookup"><span data-stu-id="ecdef-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="ecdef-120">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="ecdef-120">Tracking Record</span></span>|<span data-ttu-id="ecdef-121">Description</span><span class="sxs-lookup"><span data-stu-id="ecdef-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="ecdef-122">Enregistrements de suivi d'instance du workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="ecdef-123">Décrit le cycle de vie de l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="ecdef-124">Par exemple, un enregistrement d'instance est émis lorsque le workflow démarre ou se termine.</span><span class="sxs-lookup"><span data-stu-id="ecdef-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="ecdef-125">Enregistrements de suivi d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="ecdef-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="ecdef-126">Détaille l'exécution de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ecdef-126">Details activity execution.</span></span> <span data-ttu-id="ecdef-127">Ces enregistrements indiquent l'état d'une activité de workflow, par exemple lorsqu'une activité est planifiée, lorsque l'activité se termine ou lorsqu'une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="ecdef-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="ecdef-128">Enregistrement de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="ecdef-128">Bookmark resumption record.</span></span>|<span data-ttu-id="ecdef-129">Émis chaque fois qu'un signet au sein d'une instance de workflow est repris.</span><span class="sxs-lookup"><span data-stu-id="ecdef-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="ecdef-130">Enregistrements de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ecdef-130">Custom Tracking Records.</span></span>|<span data-ttu-id="ecdef-131">Un auteur de workflow peut créer des enregistrements de suivi personnalisé et les émettre dans l'activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ecdef-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="ecdef-132">Le participant de suivi s'abonne à un sous-ensemble des objets <xref:System.Activities.Tracking.TrackingRecord> émis à l'aide de modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="ecdef-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="ecdef-133">Un modèle de suivi contient des requêtes de suivi qui permettent de s'abonner à un type d'enregistrement de suivi particulier.</span><span class="sxs-lookup"><span data-stu-id="ecdef-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="ecdef-134">Les modèles de suivi peuvent être spécifiés dans le code ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ecdef-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="ecdef-135">Participant de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="ecdef-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="ecdef-136">L’API de participant de suivi permet l’extension du runtime de suivi avec un participant de suivi fourni par l’utilisateur, qui peut inclure une logique personnalisée permettant de gérer les objets <xref:System.Activities.Tracking.TrackingRecord> émis par le runtime de workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="ecdef-137">Pour écrire un participant de suivi, l'utilisateur doit implémenter <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="ecdef-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="ecdef-138">Plus précisément, la méthode <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> doit être implémentée par le participant personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ecdef-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="ecdef-139">Cette méthode est appelée lorsqu'un <xref:System.Activities.Tracking.TrackingRecord> est émis par le runtime de workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="ecdef-140">Le participant de suivi complet est implémenté dans le fichier ConsoleTrackingParticipant.cs.</span><span class="sxs-lookup"><span data-stu-id="ecdef-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="ecdef-141">L’exemple de code suivant est <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> la méthode pour le participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ecdef-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="ecdef-142">L'exemple de code suivant ajoute le participant de console au demandeur de workflow.</span><span class="sxs-lookup"><span data-stu-id="ecdef-142">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="ecdef-143">Émission d'enregistrements de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="ecdef-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="ecdef-144">Cet exemple illustre également la possibilité d'émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> à partir d'une activité de workflow personnalisée :</span><span class="sxs-lookup"><span data-stu-id="ecdef-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="ecdef-145">Les objets <xref:System.Activities.Tracking.CustomTrackingRecord> sont créés et remplis avec les données définies par l'utilisateur qui doivent être émises avec l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ecdef-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="ecdef-146">Est émis en appelant la méthode Track <xref:System.Activities.ActivityContext>de. <xref:System.Activities.Tracking.CustomTrackingRecord></span><span class="sxs-lookup"><span data-stu-id="ecdef-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="ecdef-147">L'exemple suivant montre comment émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> dans une activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ecdef-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="ecdef-148">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="ecdef-148">To use this sample</span></span>

1. <span data-ttu-id="ecdef-149">À l’aide de Visual Studio 2010, ouvrez le fichier solution CustomTrackingSample. sln.</span><span class="sxs-lookup"><span data-stu-id="ecdef-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="ecdef-150">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="ecdef-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ecdef-151">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="ecdef-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecdef-152">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ecdef-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ecdef-153">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ecdef-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ecdef-154">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="ecdef-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecdef-155">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ecdef-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="ecdef-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecdef-156">See also</span></span>

- [<span data-ttu-id="ecdef-157">Exemples de surveillance AppFabric</span><span class="sxs-lookup"><span data-stu-id="ecdef-157">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
