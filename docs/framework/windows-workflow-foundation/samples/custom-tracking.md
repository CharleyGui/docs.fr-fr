---
title: Suivi personnalisé
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 9a2ad2004c47ce76dcc35baf4ca28aa174409581
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094655"
---
# <a name="custom-tracking"></a>Suivi personnalisé
Cet exemple montre comment créer un participant de suivi personnalisé et écrire le contenu des données de suivi sur la console. De plus, il montre comment émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> remplis avec des données définies par l'utilisateur. Le participant de suivi basé sur la console filtre les objets <xref:System.Activities.Tracking.TrackingRecord> émis par le workflow à l'aide d'un objet de modèle de suivi créé dans le code.

## <a name="sample-details"></a>Détails de l'exemple
 Windows Workflow Foundation (WF) fournit une infrastructure de suivi pour suivre l’exécution d’une instance de Workflow. Le runtime de suivi implémente une instance de workflow pour émettre des événements liés au cycle de vie du workflow, des événements des activités de workflow et des événements de suivi personnalisé. Le tableau suivant détaille les composants principaux de l'infrastructure de suivi.

|Composant|Description|
|---------------|-----------------|
|Runtime de suivi|Fournit l'infrastructure permettant d'émettre des enregistrements de suivi.|
|Participants de suivi|Consomme les enregistrements de suivi. .NET Framework 4 est fourni avec un participant de suivi qui écrit des enregistrements de suivi en tant qu’événements de Suivi d’v nements pour Windows (ETW).|
|Modèle de suivi|Mécanisme de filtrage qui permet à un participant de suivi de s'abonner à un sous-ensemble des enregistrements de suivi émis à partir d'une instance de workflow.|

 Le tableau suivant détaille les enregistrements de suivi que l'exécution de workflow émet.

|Enregistrement de suivi|Description|
|---------------------|-----------------|
|Enregistrements de suivi d'instance du workflow.|Décrit le cycle de vie de l'instance de workflow. Par exemple, un enregistrement d'instance est émis lorsque le workflow démarre ou se termine.|
|Enregistrements de suivi d'état d'activité.|Détaille l'exécution de l'activité. Ces enregistrements indiquent l'état d'une activité de workflow, par exemple lorsqu'une activité est planifiée, lorsque l'activité se termine ou lorsqu'une erreur est générée.|
|Enregistrement de reprise de signet.|Émis chaque fois qu'un signet au sein d'une instance de workflow est repris.|
|Enregistrements de suivi personnalisé.|Un auteur de workflow peut créer des enregistrements de suivi personnalisé et les émettre dans l'activité personnalisée.|

 Le participant de suivi s'abonne à un sous-ensemble des objets <xref:System.Activities.Tracking.TrackingRecord> émis à l'aide de modèles de suivi. Un modèle de suivi contient des requêtes de suivi qui permettent de s'abonner à un type d'enregistrement de suivi particulier. Les modèles de suivi peuvent être spécifiés dans le code ou dans la configuration.

### <a name="custom-tracking-participant"></a>Participant de suivi personnalisé
 L’API de participant de suivi permet l’extension du runtime de suivi avec un participant de suivi fourni par l’utilisateur, qui peut inclure une logique personnalisée permettant de gérer les objets <xref:System.Activities.Tracking.TrackingRecord> émis par le runtime de workflow.

 Pour écrire un participant de suivi, l'utilisateur doit implémenter <xref:System.Activities.Tracking.TrackingParticipant>. Plus précisément, la méthode <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> doit être implémentée par le participant personnalisé. Cette méthode est appelée lorsqu'un <xref:System.Activities.Tracking.TrackingRecord> est émis par le runtime de workflow.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Le participant de suivi complet est implémenté dans le fichier ConsoleTrackingParticipant.cs. L’exemple de code suivant est la méthode <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> pour le participant de suivi personnalisé.

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

 L'exemple de code suivant ajoute le participant de console au demandeur de workflow.

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

### <a name="emitting-custom-tracking-records"></a>Émission d'enregistrements de suivi personnalisé
 Cet exemple illustre également la possibilité d'émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> à partir d'une activité de workflow personnalisée :

- Les objets <xref:System.Activities.Tracking.CustomTrackingRecord> sont créés et remplis avec les données définies par l'utilisateur qui doivent être émises avec l'enregistrement.

- Le <xref:System.Activities.Tracking.CustomTrackingRecord> est émis en appelant la méthode Track du <xref:System.Activities.ActivityContext>.

 L'exemple suivant montre comment émettre des objets <xref:System.Activities.Tracking.CustomTrackingRecord> dans une activité personnalisée.

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

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier solution CustomTrackingSample. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur Ctrl+F5.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de surveillance AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
