---
title: Persistance du workflow
description: .NET Framework 4.6.1 comprend la classe SqlWorkflowInstanceStore, qui permet la persistance des données et métadonnées de workflow dans une base de données SQL Server.
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 2184a159423a611a8936e900591a480ce7ef6ec8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293804"
---
# <a name="workflow-persistence"></a>Persistance du workflow

La persistance de workflow est la capture durable de l'état d'une instance de workflow, indépendamment des informations sur le processus ou l'ordinateur. Cela permet d'abord de fournir, en cas de défaillance du système, un point connu de récupération de l'instance de workflow. Ensuite, la mémoire est conservée en déchargeant les instances de workflow qui ne fonctionnent pas activement. Enfin, l'état de l'instance de workflow peut être déplacé d'un nœud vers un autre dans une batterie de serveurs.  
  
 La persistance permet l'agilité de processus, l'évolutivité, la récupération en cas de défaillance et la capacité de gérer la mémoire plus efficacement. Le processus de persistance inclut l'identification d'un point de persistance, la collecte des données à enregistrer et enfin, la délégation de la mémoire physique des données à un fournisseur de persistance.  
  
 Pour activer la persistance pour un flux de travail, vous devez associer un magasin d’instances à **WorkflowApplication** ou **WorkflowServiceHost** comme indiqué dans Guide pratique [pour activer la persistance pour les workflows et les services de workflow](how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** et **WorkflowServiceHost** utilisent le magasin d’instances associé pour activer les instances de workflow persistantes dans un magasin de persistance et charger des instances de workflow en mémoire en fonction des données d’instance de workflow stockées dans le magasin de persistance.  
  
 Le est [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fourni avec la classe **SqlWorkflowInstanceStore** , qui permet la persistance des données et des métadonnées sur les instances de workflow dans une base de données SQL Server 2005 ou SQL Server 2008. Pour plus d’informations, consultez [magasin d’instances de workflow SQL](sql-workflow-instance-store.md) .  
  
 Pour stocker et charger vos données spécifiques à l'application, ainsi que les informations sur l'instance de workflow, vous pouvez créer des participants de persistance qui étendent la classe <xref:System.Activities.Persistence.PersistenceParticipant>. Un participant de persistance participe au processus de persistance pour les fins suivantes : enregistrer des données sérialisables personnalisées dans le magasin de persistance ; charger des données, du magasin d’instances vers la mémoire ; et effectuer toute logique supplémentaire dans le cadre d’une transaction de persistance. Pour plus d’informations, consultez [participants de persistance](persistence-participants.md).  
  
 Windows Server AppFabric simplifie le processus de configuration de la persistance. Pour plus d’informations, consultez [concepts de persistance avec Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10)) .  
  
## <a name="implicit-persistence-points"></a>Points de persistance implicites  

 La liste suivante comprend des exemples de conditions selon lesquelles un workflow est rendu persistant, lors de l'association d'un magasin d'instances à un workflow.  
  
- Lorsqu’une activité **TransactionScope** se termine ou qu’une activité **TransactedReceiveScope** se termine.  
  
- Lorsqu’une instance de workflow devient inactive et que **WorkflowIdleBehavior** est défini sur l’hôte de Workflow. Cela se produit, par exemple, lorsque vous utilisez des activités de messagerie ou une activité de **délai** .  
  
- Lorsqu’un WorkflowApplication devient inactif et que la propriété **PersistableIdle** de l’application est définie sur **PersistableIdleAction. Persist**.  
  
- Lorsqu'une application hôte a pour instruction de rendre persistante ou de décharger une instance de workflow.  
  
- Lorsqu'une instance de workflow est arrêtée ou prend fin.  
  
- Lors de l’exécution d’une activité **Persist** .  
  
- Lorsqu'une instance d'un workflow développé à l'aide d'une version précédente de Windows Workflow Foundation rencontre un point de persistance lors de l'exécution interopérable.  
  
## <a name="in-this-section"></a>Dans cette section  
  
- [Magasin d'instances de workflow SQL](sql-workflow-instance-store.md)  
  
- [Magasins d'instances](instance-stores.md)  
  
- [Participants de persistance](persistence-participants.md)  
  
- [Meilleures pratiques de persistance](persistence-best-practices.md)  
  
- [Instances de workflow non persistantes](non-persisted-workflow-instances.md)  
  
- [Suspension et reprise d'un workflow](pausing-and-resuming-a-workflow.md)
