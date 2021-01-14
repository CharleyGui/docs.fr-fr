---
title: Mise à jour dynamique
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: cb4b63a67aa6e9033b227198e2ecc2b1b80db927
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190154"
---
# <a name="dynamic-update"></a>Mise à jour dynamique

La mise à jour dynamique fournit un mécanisme pour permettre aux développeurs d'applications de workflow de mettre à jour la définition de workflow d'une instance de workflow persistante. Il peut s'agir d'une résolution de bogue, de nouvelles spécifications ou de l'adaptation à des modifications inattendues. Cette rubrique fournit une vue d’ensemble de la fonctionnalité de mise à jour dynamique introduite dans .NET Framework 4,5.

## <a name="dynamic-update"></a>Mise à jour dynamique

Pour appliquer les mises à jour dynamiques à une instance de workflow persistante, un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui contient les instructions du runtime qui décrivent comment modifier l'instance persistante de workflow est créé pour refléter les modifications souhaitées. Une fois la mise à jour de la carte créée, elle est appliquée aux instances de workflow persistantes souhaitées. Une fois la mise à jour dynamique appliquée, l'instance de workflow peut reprendre à l'aide de la nouvelle définition de workflow mise à jour. Quatre étapes sont requises pour créer et appliquer la mise à jour d'une carte.

1. [Préparer la définition de workflow pour la mise à jour dynamique](dynamic-update.md#Prepare)

2. [Mettre à jour la définition de workflow pour refléter les modifications souhaitées](dynamic-update.md#Update)

3. [Créer la mise à jour de la carte](dynamic-update.md#Create)

4. [Appliquer la mise à jour de la carte aux instances de workflow persistantes souhaitées](dynamic-update.md#Apply)

> [!NOTE]
> Notez que les étapes 1 à 3, qui couvrent la conception de la mise à jour de la carte, peuvent être effectuées indépendamment de la mise à jour. Un scénario courant dans lequel le développeur de workflow crée la carte de mise à jour hors connexion, puis un administrateur appliquera la mise à jour ultérieurement.

Cette rubrique fournit une vue d'ensemble du processus de mise à jour dynamique pour ajouter une nouvelle activité à une instance persistante d'un workflow XAML compilé.

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> Préparer la définition de workflow pour la mise à jour dynamique

La première étape du processus de mise à jour dynamique consiste à développer la définition de workflow souhaitée pour la mise à jour. Pour ce faire, il suffit d'appeler la méthode <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> et de passer la définition de workflow à modifier. Cette méthode valide et parcourt l'arborescence de workflow pour identifier tous les objets, tels que les activités et les variables publiques qui doivent être référencées de sorte qu'elles puissent être comparées ultérieurement à la définition modifiée de workflow. Une fois cette opération terminée, l’arborescence de workflow est clonée et attachée à la définition de workflow d’origine. Lorsque la mise à jour de la carte est créée, la version mise à jour de la définition du workflow est comparée à la définition de workflow d'origine et la mise à jour de la carte est générée selon les différences.

Pour préparer un workflow XAML pour la mise à jour dynamique, il peut être chargé dans un <xref:System.Activities.ActivityBuilder>, puis le <xref:System.Activities.ActivityBuilder> est passé dans <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.

> [!NOTE]
> Pour plus d’informations sur l’utilisation de workflows sérialisés et <xref:System.Activities.ActivityBuilder> , consultez [sérialisation de workflows et d’activités vers et à partir de XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

Dans l'exemple suivant, une définition de `MortgageWorkflow` (composée de <xref:System.Activities.Statements.Sequence> avec plusieurs activités enfants) est chargée dans <xref:System.Activities.ActivityBuilder>, puis élaborée pour la mise à jour dynamique. Après le retour de la méthode, <xref:System.Activities.ActivityBuilder> contient la définition de workflow d'origine ainsi qu'une copie.

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> Mettre à jour la définition de workflow pour refléter les modifications souhaitées

Une fois que la définition de workflow a été élaborée pour la mise à jour, les modifications souhaitées peuvent être apportées. Vous pouvez ajouter ou supprimer des activités, ajouter, déplacer ou supprimer des variables publiques, ajouter ou supprimer des arguments et apporter des modifications à la signature des délégués d’activité. Vous ne pouvez pas supprimer une activité en cours d'exécution ou modifier la signature d'un délégué en cours d'exécution. Ces modifications peuvent être effectuées à l'aide du code, ou dans un concepteur de workflow réhébergé. Dans l'exemple suivant, une activité `VerifyAppraisal` personnalisée est ajoutée à la séquence qui constitue le corps de `MortgageWorkflow` à partir de l'exemple précédent.

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="create-the-update-map"></a><a name="Create"></a> Créer la carte de mise à jour

Une fois que la définition de workflow élaborée pour la mise à jour a été modifiée, la mise à jour de la carte peut être créée. Pour créer une mise à jour de carte dynamique, la méthode <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> est appelée. Retourne un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui contient les informations dont le runtime a besoin pour modifier une instance persistante de workflow de sorte qu'elle puisse être chargée et reprise avec la nouvelle définition de workflow. Dans l'exemple suivant, une carte dynamique est créée pour la définition modifiée de `MortgageWorkflow` de l'exemple précédent.

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

Cette mise à jour de la carte peut être utilisée immédiatement pour modifier les instances de workflow persistantes, ou elle peut être enregistrée et les mises à jour appliquées ultérieurement. Une méthode pour enregistrer la mise à jour de la carte consiste à la sérialiser dans un fichier, comme indiqué dans l'exemple suivant.

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

Lorsque <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> retourne, la définition clonée de workflow et d'autres informations de mise à jour dynamique qui ont été ajoutées dans l'appel à <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> sont supprimées, et la définition modifiée de workflow est prête à être enregistrée afin qu'elle puisse être utilisée ultérieurement en reprenant les instances de workflow mises à jour. Dans l'exemple suivant, la définition modifiée de workflow est enregistrée dans `MortgageWorkflow_v1.1.xaml`.

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> Appliquer la mise à jour de la carte aux instances de workflow persistantes souhaitées

L'application de la mise à jour de la carte peut être effectuée à tout moment après sa création. Elle peut être effectuée immédiatement à l'aide de l'instance <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui a été retournée par <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ou elle peut être effectuée ultérieurement en utilisant une copie stockée de la mise à jour de la carte. Pour mettre à jour une instance du workflow, chargez-la dans <xref:System.Activities.WorkflowApplicationInstance> à l'aide de <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Ensuite, créez un <xref:System.Activities.WorkflowApplication> en utilisant la définition de workflow mise à jour et le <xref:System.Activities.WorkflowIdentity> souhaité. Ce <xref:System.Activities.WorkflowIdentity> peut être différent de celui qui a été utilisé pour rendre persistant le workflow d'origine, et est généralement utilisé pour indiquer que l'instance persistante a été modifiée. Une fois que <xref:System.Activities.WorkflowApplication> est créé, il est chargé à l'aide de la surcharge de <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> qui prend un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, puis déchargé avec un appel à <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. Cela applique la mise à jour dynamique et rend persistante l'instance mise à jour de workflow.

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a>Reprendre une instance mise à jour de workflow

Une fois la mise à jour dynamique appliquée, l'instance de workflow peut reprendre. Notez que la nouvelle définition mise à jour et <xref:System.Activities.WorkflowIdentity> doivent être utilisés.

> [!NOTE]
> Pour plus d’informations sur l’utilisation de <xref:System.Activities.WorkflowApplication> et de <xref:System.Activities.WorkflowIdentity> , consultez [utilisation de WorkflowIdentity et de la gestion des versions](using-workflowidentity-and-versioning.md).

Dans l'exemple suivant, le workflow `MortgageWorkflow_v1.1.xaml` de l'exemple précédent a été compilé, et est chargé et repris à l'aide de la définition mise à jour de workflow.

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```
