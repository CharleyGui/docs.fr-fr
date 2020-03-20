---
title: 'Procédure : configurer la persistance avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2974b6bcbb94c5b54d91025aeabe7c2d2e94c7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185052"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="5ad86-102">Procédure : configurer la persistance avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="5ad86-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="5ad86-103">Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5ad86-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="5ad86-104">Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="5ad86-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="5ad86-105">Pour plus d’informations, voir [Comment : Activer SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="5ad86-106">Pour configurer le magasin d'instances de workflow SQL en mode Configuration</span><span class="sxs-lookup"><span data-stu-id="5ad86-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="5ad86-107">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML.</span><span class="sxs-lookup"><span data-stu-id="5ad86-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="5ad86-108">L’exemple de configuration suivant montre comment configurer le magasin d’instance de flux de travail SQL en utilisant l’élément `sqlWorkflowInstanceStore` de comportement <> dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5ad86-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="5ad86-109">Pour plus d’informations sur la façon de configurer le magasin d’instance de flux de travail SQL, voir [Comment : Activer SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="5ad86-110">Pour plus d’informations sur les `sqlWorkflowInstanceStore` paramètres individuels pour le <>'élément comportemental, voir [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="5ad86-111">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="5ad86-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="5ad86-112">Pour plus d’informations, voir [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="5ad86-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5ad86-113">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="5ad86-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="5ad86-114">Pour plus d’informations, voir [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="5ad86-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="5ad86-115">Pour configurer le magasin d'instances de workflow SQL en code</span><span class="sxs-lookup"><span data-stu-id="5ad86-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="5ad86-116">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code.</span><span class="sxs-lookup"><span data-stu-id="5ad86-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="5ad86-117">L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.</span><span class="sxs-lookup"><span data-stu-id="5ad86-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     <span data-ttu-id="5ad86-118">Pour plus d’informations sur la façon de configurer le magasin d’instance de flux de travail SQL, voir [Comment : Activer SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="5ad86-119">Pour plus d’informations sur <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> les paramètres individuels de l’élément comportemental, voir [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="5ad86-120">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="5ad86-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="5ad86-121">Pour plus d’informations, voir [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="5ad86-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5ad86-122">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="5ad86-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="5ad86-123">Pour plus d’informations, voir [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="5ad86-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="5ad86-124">Par exemple de la façon de configurer la persistance programmatiquement voir [Comment: Permettre la persistance pour les flux de travail et les services de flux de travail](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="5ad86-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad86-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ad86-125">See also</span></span>

- [<span data-ttu-id="5ad86-126">Services de flux de travail</span><span class="sxs-lookup"><span data-stu-id="5ad86-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="5ad86-127">Persistance du workflow</span><span class="sxs-lookup"><span data-stu-id="5ad86-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="5ad86-128">[Persistance du tissu d’application de serveur Windows](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5ad86-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
