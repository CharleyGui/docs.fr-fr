---
title: Utilisation de WorkflowIdentity et du versioning
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 1d31739c135dbb518f05c40ba802c782b6817bff
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855632"
---
# <a name="using-workflowidentity-and-versioning"></a>Utilisation de WorkflowIdentity et du versioning

<xref:System.Activities.WorkflowIdentity> permet aux développeurs d'applications de workflow d'associer un nom et un <xref:System.Version> à une définition de workflow, et d'associer ces informations à une instance persistante de workflow. Ces informations d'identité peuvent être utilisées par les développeurs d'applications de workflow pour activer des scénarios tels que l'exécution côte à côte de plusieurs versions d'une définition de workflow, et fournir la base d'autres fonctionnalités telles que la mise à jour dynamique. Cette rubrique fournit une vue d'ensemble de l'utilisation de <xref:System.Activities.WorkflowIdentity> avec l'hébergement <xref:System.Activities.WorkflowApplication>. Pour plus d’informations sur l’exécution côte à côte de définitions de workflow dans un service de workflow, consultez [gestion des versions côte à côte dans WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Pour plus d’informations sur la mise à jour dynamique, consultez [mise à jour dynamique](dynamic-update.md).

## <a name="in-this-topic"></a>Dans cette rubrique

- [Utilisation de WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [Exécution côte à côte à l'aide de WorkflowIdentity](using-workflowidentity-and-versioning.md#SxS)

- [Mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Pour mettre à niveau le schéma de base de données](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a>Utilisation de WorkflowIdentity

Pour utiliser <xref:System.Activities.WorkflowIdentity>, créez une instance, configurez-la et associez-la à une instance <xref:System.Activities.WorkflowApplication>. Une instance <xref:System.Activities.WorkflowIdentity> contient trois informations d'identification. <xref:System.Activities.WorkflowIdentity.Name%2A> et <xref:System.Activities.WorkflowIdentity.Version%2A> contiennent un nom et un <xref:System.Version> et sont obligatoire, et <xref:System.Activities.WorkflowIdentity.Package%2A> est facultatif et peut être utilisé pour spécifier une chaîne supplémentaire contenant des informations telles que le nom de l'assembly ou d'autres informations souhaitées. <xref:System.Activities.WorkflowIdentity> est unique si l'une de ses trois propriétés est différente d'un autre <xref:System.Activities.WorkflowIdentity>.

> [!IMPORTANT]
> Un <xref:System.Activities.WorkflowIdentity> ne devrait contenir aucune information d'identification personnelle (PII). Les informations relatives au <xref:System.Activities.WorkflowIdentity> utilisées pour créer une instance sont émises vers n'importe quel service de suivi configuré sur plusieurs points du cycle de vie du workflow différents par le runtime. Le suivi WF ne dispose pas d'un mécanisme de masquage des informations PII (données utilisateur sensibles). Par conséquent, une instance <xref:System.Activities.WorkflowIdentity> ne doit contenir aucune donnée PII, car elle est émise par le runtime dans les enregistrements de suivi et peut être vue par n'importe quelle personne qui dispose d'un accès permettant d'afficher les enregistrements de suivi.

Dans l'exemple suivant, un <xref:System.Activities.WorkflowIdentity> est créé et associé à une instance d'un workflow créée à l'aide d'une définition de workflow `MortgageWorkflow`.

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

Lors du rechargement et de la reprise d'un workflow, un <xref:System.Activities.WorkflowIdentity>, configuré pour correspondre à <xref:System.Activities.WorkflowIdentity> de l'instance persistante de workflow doit être utilisé.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

Si <xref:System.Activities.WorkflowIdentity> utilisé pour recharger l'instance du workflow ne correspond pas au <xref:System.Activities.WorkflowIdentity> persistant, une exception <xref:System.Activities.VersionMismatchException> est levée. Dans l'exemple suivant, une tentative de chargement est faite sur l'instance `MortgageWorkflow` qui a été rendue persistante dans l'exemple précédent. Cette tentative de chargement est effectuée à l'aide de <xref:System.Activities.WorkflowIdentity> configuré pour une version plus récente du workflow d'emprunts qui ne correspond pas à l'instance persistante.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Lorsque le code précédent est exécuté, l'exception <xref:System.Activities.VersionMismatchException> suivante est levée.

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a>Exécution côte à côte à l’aide de WorkflowIdentity

<xref:System.Activities.WorkflowIdentity> peut être utilisé pour faciliter l'exécution de plusieurs versions d'un workflow côte à côte. Un scénario courant modifie les besoins de l'entreprise sur un workflow de longue durée. De nombreuses instances d'un workflow peuvent s'exécuter lorsqu'une version mise à jour est déployée. L'application hôte peut être configurée pour utiliser la définition mise à jour de workflow lors du démarrage de nouvelles instances, et il est de la responsabilité de l'application hôte de fournir la définition correcte de workflow lors de la reprise des instances. <xref:System.Activities.WorkflowIdentity> peut être utilisé pour identifier et fournir la définition correspondante de workflow lors de la reprise des instances de workflow.

Pour récupérer le <xref:System.Activities.WorkflowIdentity> d'une instance persistante de workflow, la méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> est utilisée. La méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> prend le <xref:System.Activities.WorkflowApplication.Id%2A> de l'instance persistante de workflow et le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui contient l'instance rendue persistante et retourne un <xref:System.Activities.WorkflowApplicationInstance>. Un <xref:System.Activities.WorkflowApplicationInstance> contient des informations sur une instance persistante de workflow, y compris son <xref:System.Activities.WorkflowIdentity> associé. Ce <xref:System.Activities.WorkflowIdentity> associé peut être utilisé par l'hôte pour fournir la définition correcte de workflow lors du chargement et de la reprise de l'instance de workflow.

> [!NOTE]
> Un <xref:System.Activities.WorkflowIdentity> null est valide, et peut être utilisé par l'hôte pour mapper les instances qui ont été rendues persistantes sans <xref:System.Activities.WorkflowIdentity> associé à la définition appropriée de workflow. Ce scénario peut se produire lorsqu’une application de workflow n’a pas été initialement écrite avec le contrôle de version de workflow, ou lorsqu’une application est mise à niveau à partir de .NET Framework 4. Pour plus d’informations, consultez [mise à niveau de bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

Dans l’exemple suivant `Dictionary<WorkflowIdentity, Activity>` , un est utilisé pour associer <xref:System.Activities.WorkflowIdentity> des instances à leurs définitions de workflow correspondantes, et un flux de travail est démarré à l’aide de la `MortgageWorkflow` définition de workflow, qui est associée au `identityV1` <xref:System.Activities.WorkflowIdentity> .

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

Dans l'exemple suivant, les informations sur l'instance persistante de workflow de l'exemple précédent sont récupérées en appelant <xref:System.Activities.WorkflowApplication.GetInstance%2A>, et les informations <xref:System.Activities.WorkflowIdentity> persistantes sont utilisées pour récupérer la définition correspondante de workflow. Ces informations sont utilisées pour configurer <xref:System.Activities.WorkflowApplication>, puis le workflow est chargé. Étant donné que la surcharge <xref:System.Activities.WorkflowApplication.Load%2A> qui prend <xref:System.Activities.WorkflowApplicationInstance> est utilisée, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui a été configuré sur <xref:System.Activities.WorkflowApplicationInstance> est utilisé par <xref:System.Activities.WorkflowApplication> et par conséquent sa propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> n'a pas besoin d'être configurée.

> [!NOTE]
> Si la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> est définie, elle doit être définie avec la même instance <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que celle utilisée par <xref:System.Activities.WorkflowApplicationInstance>, sinon une exception <xref:System.ArgumentException> sera levée avec le message suivant : `The instance is configured with a different InstanceStore than this WorkflowApplication.`.

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a>Mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow

Un script de base de données SqlWorkflowInstanceStoreSchemaUpgrade. SQL est fourni pour mettre à niveau les bases de données de persistance créées à l’aide des scripts de base de données .NET Framework 4. Ce script met à jour les bases de données pour prendre en charge les nouvelles fonctionnalités de contrôle de version introduites dans .NET Framework 4,5. Des valeurs de versioning par défaut sont attribuées à toutes les instances persistantes de workflow dans les bases de données et ces instances peuvent ensuite participer côte à côte à l'exécution et à la mise à jour dynamique.

Si une application de flux de travail .NET Framework 4,5 tente d’effectuer des opérations de persistance qui utilisent les nouvelles fonctionnalités de contrôle de version sur une base de données de persistance qui n’a pas été mise à niveau à l’aide du script fourni, une <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> exception est levée avec un message similaire au message suivant.

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a>Pour mettre à niveau le schéma de base de données

1. Ouvrez SQL Server Management Studio et connectez-vous au serveur de base de données de persistance, par exemple **.\SQLEXPRESS**.

2. Dans le menu **fichier** , choisissez **ouvrir**, **fichier** . Accédez au dossier suivant : `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`

3. Sélectionnez **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** , puis cliquez sur **ouvrir**.

4. Sélectionnez le nom de la base de données de persistance dans la liste déroulante **bases de données disponibles** .

5. Choisissez **exécuter** dans le menu **requête** .

Lorsque la requête est terminée, le schéma de base de données est mis à niveau, et si vous le souhaitez, vous pouvez afficher l'identité du workflow par défaut affectée aux instances persistantes de workflow. Développez votre base de données de persistance dans le nœud **bases de données** de l' **Explorateur d’objets**, puis développez le nœud **vues** . Cliquez avec le bouton droit sur **System. Activities. DurableInstancing. instances** et choisissez **Sélectionner les 1000 premières lignes**. Faites défiler jusqu’à la fin des colonnes et Notez qu’il y a six colonnes supplémentaires ajoutées à la vue : **IdentityName**, **IdentityPackage**, **Build**, **major**, **Minor**et **Revision**. Les flux de travail persistants ont une valeur **null** pour ces champs, qui représente une identité de workflow null.
