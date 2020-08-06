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
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="40e20-102">Utilisation de WorkflowIdentity et du versioning</span><span class="sxs-lookup"><span data-stu-id="40e20-102">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="40e20-103"><xref:System.Activities.WorkflowIdentity> permet aux développeurs d'applications de workflow d'associer un nom et un <xref:System.Version> à une définition de workflow, et d'associer ces informations à une instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="40e20-104">Ces informations d'identité peuvent être utilisées par les développeurs d'applications de workflow pour activer des scénarios tels que l'exécution côte à côte de plusieurs versions d'une définition de workflow, et fournir la base d'autres fonctionnalités telles que la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="40e20-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="40e20-105">Cette rubrique fournit une vue d'ensemble de l'utilisation de <xref:System.Activities.WorkflowIdentity> avec l'hébergement <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="40e20-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="40e20-106">Pour plus d’informations sur l’exécution côte à côte de définitions de workflow dans un service de workflow, consultez [gestion des versions côte à côte dans WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="40e20-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="40e20-107">Pour plus d’informations sur la mise à jour dynamique, consultez [mise à jour dynamique](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="40e20-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="40e20-108">Dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="40e20-108">In this topic</span></span>

- [<span data-ttu-id="40e20-109">Utilisation de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="40e20-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="40e20-110">Exécution côte à côte à l'aide de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="40e20-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="40e20-111">Mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow</span><span class="sxs-lookup"><span data-stu-id="40e20-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="40e20-112">Pour mettre à niveau le schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="40e20-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a><span data-ttu-id="40e20-113">Utilisation de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="40e20-113">Using WorkflowIdentity</span></span>

<span data-ttu-id="40e20-114">Pour utiliser <xref:System.Activities.WorkflowIdentity>, créez une instance, configurez-la et associez-la à une instance <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="40e20-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="40e20-115">Une instance <xref:System.Activities.WorkflowIdentity> contient trois informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="40e20-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="40e20-116"><xref:System.Activities.WorkflowIdentity.Name%2A> et <xref:System.Activities.WorkflowIdentity.Version%2A> contiennent un nom et un <xref:System.Version> et sont obligatoire, et <xref:System.Activities.WorkflowIdentity.Package%2A> est facultatif et peut être utilisé pour spécifier une chaîne supplémentaire contenant des informations telles que le nom de l'assembly ou d'autres informations souhaitées.</span><span class="sxs-lookup"><span data-stu-id="40e20-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="40e20-117"><xref:System.Activities.WorkflowIdentity> est unique si l'une de ses trois propriétés est différente d'un autre <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="40e20-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40e20-118">Un <xref:System.Activities.WorkflowIdentity> ne devrait contenir aucune information d'identification personnelle (PII).</span><span class="sxs-lookup"><span data-stu-id="40e20-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="40e20-119">Les informations relatives au <xref:System.Activities.WorkflowIdentity> utilisées pour créer une instance sont émises vers n'importe quel service de suivi configuré sur plusieurs points du cycle de vie du workflow différents par le runtime.</span><span class="sxs-lookup"><span data-stu-id="40e20-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="40e20-120">Le suivi WF ne dispose pas d'un mécanisme de masquage des informations PII (données utilisateur sensibles).</span><span class="sxs-lookup"><span data-stu-id="40e20-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="40e20-121">Par conséquent, une instance <xref:System.Activities.WorkflowIdentity> ne doit contenir aucune donnée PII, car elle est émise par le runtime dans les enregistrements de suivi et peut être vue par n'importe quelle personne qui dispose d'un accès permettant d'afficher les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="40e20-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="40e20-122">Dans l'exemple suivant, un <xref:System.Activities.WorkflowIdentity> est créé et associé à une instance d'un workflow créée à l'aide d'une définition de workflow `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="40e20-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

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

<span data-ttu-id="40e20-123">Lors du rechargement et de la reprise d'un workflow, un <xref:System.Activities.WorkflowIdentity>, configuré pour correspondre à <xref:System.Activities.WorkflowIdentity> de l'instance persistante de workflow doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="40e20-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="40e20-124">Si <xref:System.Activities.WorkflowIdentity> utilisé pour recharger l'instance du workflow ne correspond pas au <xref:System.Activities.WorkflowIdentity> persistant, une exception <xref:System.Activities.VersionMismatchException> est levée.</span><span class="sxs-lookup"><span data-stu-id="40e20-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="40e20-125">Dans l'exemple suivant, une tentative de chargement est faite sur l'instance `MortgageWorkflow` qui a été rendue persistante dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="40e20-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="40e20-126">Cette tentative de chargement est effectuée à l'aide de <xref:System.Activities.WorkflowIdentity> configuré pour une version plus récente du workflow d'emprunts qui ne correspond pas à l'instance persistante.</span><span class="sxs-lookup"><span data-stu-id="40e20-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="40e20-127">Lorsque le code précédent est exécuté, l'exception <xref:System.Activities.VersionMismatchException> suivante est levée.</span><span class="sxs-lookup"><span data-stu-id="40e20-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a><span data-ttu-id="40e20-128">Exécution côte à côte à l’aide de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="40e20-128">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="40e20-129"><xref:System.Activities.WorkflowIdentity> peut être utilisé pour faciliter l'exécution de plusieurs versions d'un workflow côte à côte.</span><span class="sxs-lookup"><span data-stu-id="40e20-129"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="40e20-130">Un scénario courant modifie les besoins de l'entreprise sur un workflow de longue durée.</span><span class="sxs-lookup"><span data-stu-id="40e20-130">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="40e20-131">De nombreuses instances d'un workflow peuvent s'exécuter lorsqu'une version mise à jour est déployée.</span><span class="sxs-lookup"><span data-stu-id="40e20-131">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="40e20-132">L'application hôte peut être configurée pour utiliser la définition mise à jour de workflow lors du démarrage de nouvelles instances, et il est de la responsabilité de l'application hôte de fournir la définition correcte de workflow lors de la reprise des instances.</span><span class="sxs-lookup"><span data-stu-id="40e20-132">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="40e20-133"><xref:System.Activities.WorkflowIdentity> peut être utilisé pour identifier et fournir la définition correspondante de workflow lors de la reprise des instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-133"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="40e20-134">Pour récupérer le <xref:System.Activities.WorkflowIdentity> d'une instance persistante de workflow, la méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="40e20-134">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="40e20-135">La méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> prend le <xref:System.Activities.WorkflowApplication.Id%2A> de l'instance persistante de workflow et le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui contient l'instance rendue persistante et retourne un <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="40e20-135">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="40e20-136">Un <xref:System.Activities.WorkflowApplicationInstance> contient des informations sur une instance persistante de workflow, y compris son <xref:System.Activities.WorkflowIdentity> associé.</span><span class="sxs-lookup"><span data-stu-id="40e20-136">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="40e20-137">Ce <xref:System.Activities.WorkflowIdentity> associé peut être utilisé par l'hôte pour fournir la définition correcte de workflow lors du chargement et de la reprise de l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-137">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="40e20-138">Un <xref:System.Activities.WorkflowIdentity> null est valide, et peut être utilisé par l'hôte pour mapper les instances qui ont été rendues persistantes sans <xref:System.Activities.WorkflowIdentity> associé à la définition appropriée de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-138">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="40e20-139">Ce scénario peut se produire lorsqu’une application de workflow n’a pas été initialement écrite avec le contrôle de version de workflow, ou lorsqu’une application est mise à niveau à partir de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="40e20-139">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="40e20-140">Pour plus d’informations, consultez [mise à niveau de bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="40e20-140">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="40e20-141">Dans l’exemple suivant `Dictionary<WorkflowIdentity, Activity>` , un est utilisé pour associer <xref:System.Activities.WorkflowIdentity> des instances à leurs définitions de workflow correspondantes, et un flux de travail est démarré à l’aide de la `MortgageWorkflow` définition de workflow, qui est associée au `identityV1` <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="40e20-141">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

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

<span data-ttu-id="40e20-142">Dans l'exemple suivant, les informations sur l'instance persistante de workflow de l'exemple précédent sont récupérées en appelant <xref:System.Activities.WorkflowApplication.GetInstance%2A>, et les informations <xref:System.Activities.WorkflowIdentity> persistantes sont utilisées pour récupérer la définition correspondante de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-142">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="40e20-143">Ces informations sont utilisées pour configurer <xref:System.Activities.WorkflowApplication>, puis le workflow est chargé.</span><span class="sxs-lookup"><span data-stu-id="40e20-143">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="40e20-144">Étant donné que la surcharge <xref:System.Activities.WorkflowApplication.Load%2A> qui prend <xref:System.Activities.WorkflowApplicationInstance> est utilisée, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui a été configuré sur <xref:System.Activities.WorkflowApplicationInstance> est utilisé par <xref:System.Activities.WorkflowApplication> et par conséquent sa propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> n'a pas besoin d'être configurée.</span><span class="sxs-lookup"><span data-stu-id="40e20-144">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="40e20-145">Si la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> est définie, elle doit être définie avec la même instance <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que celle utilisée par <xref:System.Activities.WorkflowApplicationInstance>, sinon une exception <xref:System.ArgumentException> sera levée avec le message suivant : `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="40e20-145">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

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

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="40e20-146">Mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow</span><span class="sxs-lookup"><span data-stu-id="40e20-146">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="40e20-147">Un script de base de données SqlWorkflowInstanceStoreSchemaUpgrade. SQL est fourni pour mettre à niveau les bases de données de persistance créées à l’aide des scripts de base de données .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="40e20-147">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="40e20-148">Ce script met à jour les bases de données pour prendre en charge les nouvelles fonctionnalités de contrôle de version introduites dans .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="40e20-148">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="40e20-149">Des valeurs de versioning par défaut sont attribuées à toutes les instances persistantes de workflow dans les bases de données et ces instances peuvent ensuite participer côte à côte à l'exécution et à la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="40e20-149">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="40e20-150">Si une application de flux de travail .NET Framework 4,5 tente d’effectuer des opérations de persistance qui utilisent les nouvelles fonctionnalités de contrôle de version sur une base de données de persistance qui n’a pas été mise à niveau à l’aide du script fourni, une <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> exception est levée avec un message similaire au message suivant.</span><span class="sxs-lookup"><span data-stu-id="40e20-150">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a><span data-ttu-id="40e20-151">Pour mettre à niveau le schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="40e20-151">To upgrade the database schema</span></span>

1. <span data-ttu-id="40e20-152">Ouvrez SQL Server Management Studio et connectez-vous au serveur de base de données de persistance, par exemple **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="40e20-152">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="40e20-153">Dans le menu **fichier** , choisissez **ouvrir**, **fichier** .</span><span class="sxs-lookup"><span data-stu-id="40e20-153">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="40e20-154">Accédez au dossier suivant : `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="40e20-154">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="40e20-155">Sélectionnez **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** , puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="40e20-155">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="40e20-156">Sélectionnez le nom de la base de données de persistance dans la liste déroulante **bases de données disponibles** .</span><span class="sxs-lookup"><span data-stu-id="40e20-156">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="40e20-157">Choisissez **exécuter** dans le menu **requête** .</span><span class="sxs-lookup"><span data-stu-id="40e20-157">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="40e20-158">Lorsque la requête est terminée, le schéma de base de données est mis à niveau, et si vous le souhaitez, vous pouvez afficher l'identité du workflow par défaut affectée aux instances persistantes de workflow.</span><span class="sxs-lookup"><span data-stu-id="40e20-158">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="40e20-159">Développez votre base de données de persistance dans le nœud **bases de données** de l' **Explorateur d’objets**, puis développez le nœud **vues** .</span><span class="sxs-lookup"><span data-stu-id="40e20-159">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="40e20-160">Cliquez avec le bouton droit sur **System. Activities. DurableInstancing. instances** et choisissez **Sélectionner les 1000 premières lignes**.</span><span class="sxs-lookup"><span data-stu-id="40e20-160">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="40e20-161">Faites défiler jusqu’à la fin des colonnes et Notez qu’il y a six colonnes supplémentaires ajoutées à la vue : **IdentityName**, **IdentityPackage**, **Build**, **major**, **Minor**et **Revision**.</span><span class="sxs-lookup"><span data-stu-id="40e20-161">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="40e20-162">Les flux de travail persistants ont une valeur **null** pour ces champs, qui représente une identité de workflow null.</span><span class="sxs-lookup"><span data-stu-id="40e20-162">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
