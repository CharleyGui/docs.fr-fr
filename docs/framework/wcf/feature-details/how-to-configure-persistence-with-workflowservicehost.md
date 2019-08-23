---
title: 'Procédure : configurer la persistance avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2cae73bd503afec6ddd1faf435645ebc21f4fc76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968483"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Procédure : configurer la persistance avec WorkflowServiceHost
Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration. Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes. Pour plus d’informations, consultez [Guide pratique pour Activez la persistance SQL pour les workflows et](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)les services de Workflow.  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Pour configurer le magasin d'instances de workflow SQL en mode Configuration  
  
1. Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML. L’exemple de configuration suivant montre comment configurer le magasin d’instances de workflow SQL à l'`sqlWorkflowInstanceStore`aide de l’élément de comportement < > dans un fichier de configuration.  
  
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
  
     Pour plus d’informations sur la configuration du magasin d’instances de workflow SQL [, consultez Procédure: Activez la persistance SQL pour les workflows et](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)les services de Workflow. Pour plus d’informations sur les différents paramètres de l'`sqlWorkflowInstanceStore`< > élément de comportement, consultez [magasin d’instances de workflow SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fournit son propre magasin de persistance. Pour plus d’informations, consultez persistance de [Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise une configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Pour configurer le magasin d'instances de workflow SQL en code  
  
1. Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code. L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.  
  
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
  
     Pour plus d’informations sur la configuration du magasin d’instances de workflow SQL [, consultez Procédure: Activez la persistance SQL pour les workflows et](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)les services de Workflow. Pour plus d’informations sur les différents paramètres de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> l’élément de comportement, consultez [magasin d’instances de workflow SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fournit son propre magasin de persistance. Pour plus d’informations, consultez persistance de [Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise une configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Pour obtenir un exemple de configuration de la persistance par programme, [consultez Comment: Activez la persistance pour les workflows et](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)les services de Workflow.  
  
## <a name="see-also"></a>Voir aussi

- [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Persistance du workflow](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Persistance de Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121)
