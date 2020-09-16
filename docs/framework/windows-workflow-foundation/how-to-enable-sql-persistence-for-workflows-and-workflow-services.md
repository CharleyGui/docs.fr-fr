---
title: 'Procédure : activer la persistance SQL pour les workflow et les services de workflow'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5bcd37a654db35ba6e8af1b15d6c132a090b0579
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547751"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="0d954-102">Procédure : activer la persistance SQL pour les workflow et les services de workflow</span><span class="sxs-lookup"><span data-stu-id="0d954-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="0d954-103">Cette rubrique décrit comment configurer la fonctionnalité de magasin d’instances de workflow SQL pour activer la persistance pour vos workflows et services de workflow à la fois par programmation et en utilisant un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d954-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="0d954-104">Windows Server AppFabric simplifie le processus de configuration de la persistance.</span><span class="sxs-lookup"><span data-stu-id="0d954-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="0d954-105">Pour plus d’informations, consultez Configuration de la [persistance d’application Fabric](/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="0d954-105">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="0d954-106">Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, créez une base de données que la fonctionnalité utilise pour rendre les instances de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="0d954-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="0d954-107">Le programme d'installation de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] copie les fichiers de script SQL associés à la fonctionnalité de magasin d'instances de workflow SQL dans le dossier %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="0d954-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="0d954-108">Exécutez ces fichiers de script sur une base de données SQL Server 2005 ou SQL Server 2008 que le magasin d'instances de workflow SQL doit utiliser pour rendre les instances de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="0d954-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="0d954-109">Exécutez d'abord le fichier SqlWorkflowInstanceStoreSchema.sql, puis le fichier SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="0d954-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="0d954-110">Pour nettoyer la base de données de persistance afin d'en avoir une nouvelle, exécutez les scripts dans %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN dans l'ordre suivant.</span><span class="sxs-lookup"><span data-stu-id="0d954-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="0d954-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="0d954-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="0d954-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="0d954-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d954-113">Si vous ne créez pas de base de données de persistance, la fonctionnalité de magasin d’instances de workflow SQL lève une exception semblable à la suivante lorsqu’un hôte essaie de rendre des workflows persistants.</span><span class="sxs-lookup"><span data-stu-id="0d954-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="0d954-114">System.Data.SqlClient.SqlException : Impossible de trouver la procédure stockée « System.Activities.DurableInstancing.CreateLockOwner »</span><span class="sxs-lookup"><span data-stu-id="0d954-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="0d954-115">Les sections suivantes décrivent comment activer la persistance pour les workflows et les services de workflow à l'aide du magasin d'instances de workflow SQL.</span><span class="sxs-lookup"><span data-stu-id="0d954-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="0d954-116">Pour plus d’informations sur les propriétés du magasin d’instances de workflow SQL, consultez [Propriétés du magasin d’instances de workflow SQL](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="0d954-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="0d954-117">Activation de la persistance pour les workflows auto-hébergés qui utilisent WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="0d954-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="0d954-118">Vous pouvez activer la persistance pour les workflows auto-hébergés qui utilisent <xref:System.Activities.WorkflowApplication> par programmation à l'aide du modèle d'objet <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.</span><span class="sxs-lookup"><span data-stu-id="0d954-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="0d954-119">La procédure suivante contient les étapes pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="0d954-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="0d954-120">Pour activer la persistance pour les workflows auto-hébergés</span><span class="sxs-lookup"><span data-stu-id="0d954-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="0d954-121">Ajoutez une référence à System.Activities.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="0d954-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="0d954-122">Ajoutez l'instruction suivante en haut du fichier source après les instructions « using » existantes.</span><span class="sxs-lookup"><span data-stu-id="0d954-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="0d954-123">Construisez un <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> et affectez-le au <xref:System.Activities.WorkflowApplication.InstanceStore%2A> du <xref:System.Activities.WorkflowApplication>, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="0d954-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="0d954-124">Selon votre édition de SQL Server, le nom du serveur de chaîne de connexion peut être différent.</span><span class="sxs-lookup"><span data-stu-id="0d954-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="0d954-125">Appelez la méthode <xref:System.Activities.WorkflowApplication.Persist%2A> sur l'objet <xref:System.Activities.WorkflowApplication> pour rendre un workflow persistant ou la méthode <xref:System.Activities.WorkflowApplication.Unload%2A> pour rendre persistant et décharger un workflow.</span><span class="sxs-lookup"><span data-stu-id="0d954-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="0d954-126">Vous pouvez également gérer l'événement <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> déclenché par l'objet <xref:System.Activities.WorkflowApplication> et retourner un membre approprié (<xref:System.Activities.PersistableIdleAction.Persist> ou <xref:System.Activities.PersistableIdleAction.Unload>) de <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="0d954-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="0d954-127">Pour obtenir des instructions pas à pas, consultez l’étape [Comment : créer et exécuter un flux de travail à long terme](how-to-create-and-run-a-long-running-workflow.md) du [didacticiel de prise en main](getting-started-tutorial.md) .</span><span class="sxs-lookup"><span data-stu-id="0d954-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="0d954-128">Activation de la persistance pour les services de workflow auto-hébergés qui utilisent WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="0d954-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="0d954-129">Vous pouvez activer la persistance pour les services de workflow auto-hébergés qui utilisent <xref:System.ServiceModel.WorkflowServiceHost> par programmation à l'aide de la classe <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ou <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d954-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="0d954-130">Utilisation de la classe SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="0d954-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="0d954-131">La procédure suivante contient les étapes pour utiliser la classe <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> afin d'activer la persistance pour les services de workflow auto-hébergés.</span><span class="sxs-lookup"><span data-stu-id="0d954-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="0d954-132">Pour activer la persistance à l'aide de SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="0d954-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="0d954-133">Ajoutez une référence à System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="0d954-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="0d954-134">Ajoutez l'instruction suivante en haut du fichier source après les instructions « using » existantes.</span><span class="sxs-lookup"><span data-stu-id="0d954-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="0d954-135">Créez une instance du `WorkflowServiceHost` et ajoutez des points de terminaison pour le service de workflow.</span><span class="sxs-lookup"><span data-stu-id="0d954-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="0d954-136">Construisez un objet `SqlWorkflowInstanceStoreBehavior` et définissez les propriétés de l'objet de comportement.</span><span class="sxs-lookup"><span data-stu-id="0d954-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="0d954-137">Ouvrez l'hôte de service de workflow.</span><span class="sxs-lookup"><span data-stu-id="0d954-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="0d954-138">Utilisation de la propriété DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="0d954-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="0d954-139">Lorsque le `SqlWorkflowInstanceStoreBehavior` est appliqué, le `DurableInstancingOptions.InstanceStore` sur le `WorkflowServiceHost` a pour valeur l'objet `SqlWorkflowInstanceStore` créé à l'aide des valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d954-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="0d954-140">Vous pouvez effectuer la même opération par programmation pour définir la propriété <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> du `WorkflowServiceHost` sans utiliser la classe `SqlWorkflowInstanceStoreBehavior`, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="0d954-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="0d954-141">Activation de la persistance pour les services de workflow hébergés par le service d'activation de processus Windows qui utilisent WorkflowServiceHost à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0d954-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="0d954-142">Vous pouvez activer la persistance pour les services de workflow auto-hébergés ou hébergés par le service d'activation des processus Windows (WAS) à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d954-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="0d954-143">Un service de workflow hébergé par le service d'activation de processus Windows utilise WorkflowServiceHost de la même façon que les services de workflow auto-hébergés.</span><span class="sxs-lookup"><span data-stu-id="0d954-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="0d954-144">`SqlWorkflowInstanceStoreBehavior`, Un comportement de service qui vous permet de modifier facilement les propriétés du [magasin d’instances de workflow SQL](sql-workflow-instance-store.md) via la configuration XML.</span><span class="sxs-lookup"><span data-stu-id="0d954-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="0d954-145">Pour les services de workflow hébergés par le service d'activation de processus Windows, utilisez le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="0d954-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="0d954-146">L'exemple de configuration suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement `sqlWorkflowInstanceStore` dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d954-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="0d954-147">Si vous ne définissez pas de valeurs pour la propriété `connectionString` ou `connectionStringName`, le magasin d'instances de workflow SQL utilise la chaîne de connexion `DefaultSqlWorkflowInstanceStoreConnectionString` nommée par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d954-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="0d954-148">Lorsque le `SqlWorkflowInstanceStoreBehavior` est appliqué, le `DurableInstancingOptions.InstanceStore` sur le `WorkflowServiceHost` a pour valeur l'objet `SqlWorkflowInstanceStore` créé à l'aide des valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d954-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="0d954-149">Vous pouvez effectuer la même opération par programmation pour utiliser le `SqlWorkflowInstanceStore` avec `WorkflowServiceHost` sans utiliser l'élément de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="0d954-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="0d954-150">Il est recommandé de ne pas stocker d'informations sensibles, telles que les noms d'utilisateur et mots de passe, dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="0d954-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="0d954-151">Si vous stockez des informations sensibles dans le fichier Web.config, vous devez sécuriser l'accès au fichier Web.config à l'aide des listes de contrôle d'accès (ACL) du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="0d954-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="0d954-152">En outre, vous pouvez également sécuriser les valeurs de configuration dans un fichier de configuration comme indiqué dans [chiffrement des informations de configuration à l’aide de la configuration protégée](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d954-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="0d954-153">Éléments Machine.config liés à la fonctionnalité de magasin d'instances de workflow SQL</span><span class="sxs-lookup"><span data-stu-id="0d954-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="0d954-154">L'installation de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ajoute les éléments suivants liés à la fonctionnalité de magasin d'instances de workflow SQL au fichier Machine.config :</span><span class="sxs-lookup"><span data-stu-id="0d954-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="0d954-155">Ajoute l’élément d’extension de comportement suivant au fichier Machine.config afin que vous puissiez utiliser l' \<sqlWorkflowInstanceStore> élément de comportement de service dans le fichier de configuration pour configurer la persistance pour vos services.</span><span class="sxs-lookup"><span data-stu-id="0d954-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
