---
title: 'Procédure : configurer la persistance avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 3d8b7183b11c138b8da1f04d9084f8b94b7dcaa6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257338"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="f478b-102">Procédure : configurer la persistance avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="f478b-102">How to: Configure Persistence with WorkflowServiceHost</span></span>

<span data-ttu-id="f478b-103">Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f478b-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="f478b-104">Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="f478b-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="f478b-105">Pour plus d’informations, consultez [Comment : activer la persistance SQL pour les workflows et les services de workflow](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="f478b-106">Pour configurer le magasin d'instances de workflow SQL en mode Configuration</span><span class="sxs-lookup"><span data-stu-id="f478b-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="f478b-107">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML.</span><span class="sxs-lookup"><span data-stu-id="f478b-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="f478b-108">L’exemple de configuration suivant montre comment configurer le magasin d’instances de workflow SQL à l’aide de l' `sqlWorkflowInstanceStore` élément de comportement <> dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f478b-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
            </sqlWorkflowInstanceStore>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="f478b-109">Pour plus d’informations sur la configuration du magasin d’instances de workflow SQL, consultez [Comment : activer la persistance SQL pour les workflows et les services de workflow](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="f478b-110">Pour plus d’informations sur les différents paramètres de l' <`sqlWorkflowInstanceStore`> élément de comportement, consultez [magasin d’instances de workflow SQL](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="f478b-111">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="f478b-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="f478b-112">Pour plus d’informations, consultez [persistance de Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="f478b-112">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f478b-113">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="f478b-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="f478b-114">Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f478b-114">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="f478b-115">Pour configurer le magasin d'instances de workflow SQL en code</span><span class="sxs-lookup"><span data-stu-id="f478b-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="f478b-116">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code.</span><span class="sxs-lookup"><span data-stu-id="f478b-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="f478b-117">L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.</span><span class="sxs-lookup"><span data-stu-id="f478b-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="f478b-118">Pour plus d’informations sur la configuration du magasin d’instances de workflow SQL, consultez [Comment : activer la persistance SQL pour les workflows et les services de workflow](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="f478b-119">Pour plus d’informations sur les différents paramètres de l' <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> élément de comportement, consultez [magasin d’instances de workflow SQL](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="f478b-120">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="f478b-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="f478b-121">Pour plus d’informations, consultez [persistance de Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="f478b-121">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f478b-122">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="f478b-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="f478b-123">Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f478b-123">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="f478b-124">Pour obtenir un exemple de configuration de la persistance par programmation [, consultez Comment : activer la persistance pour les workflows et les services de workflow](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f478b-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f478b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f478b-125">See also</span></span>

- [<span data-ttu-id="f478b-126">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="f478b-126">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="f478b-127">Persistance du workflow</span><span class="sxs-lookup"><span data-stu-id="f478b-127">Workflow Persistence</span></span>](../../windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="f478b-128">[Persistance de Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f478b-128">[Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
