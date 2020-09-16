---
title: Magasin d'instances de workflow SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 38cf83ebb8417009c6aa205aa29cd633d1232f0a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540230"
---
# <a name="sql-workflow-instance-store"></a>Magasin d'instances de workflow SQL
Le [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] est fourni avec le magasin d'instances de workflow SQL, qui permet aux workflows de rendre les informations d'état persistantes à propos des instances de workflow dans SQL Server 2005 ou dans une base de données SQL Server 2008. Cette fonctionnalité est implémentée principalement dans le formulaire de la classe <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui dérive de la classe <xref:System.Runtime.DurableInstancing.InstanceStore> abstraite de l'infrastructure de persistance. La fonctionnalité de magasin d’instances de workflow SQL constitue un fournisseur de persistance SQL, qui est une implémentation concrète de l’API de persistance qu’un hôte utilise pour envoyer des commandes de persistance au magasin.  
  
 Le SQL Workflow Instance Store prend en charge à la fois les workflows auto-hébergés ou les services de workflow qui utilisent <xref:System.Activities.WorkflowApplication> ou <xref:System.ServiceModel.WorkflowServiceHost> et les services hébergés dans WAS qui utilisent <xref:System.ServiceModel.WorkflowServiceHost>. Vous pouvez configurer par programmation la fonctionnalité de magasin d’instances de workflow SQL pour les services auto-hébergés à l’aide du modèle objet exposé par la fonctionnalité. Vous pouvez configurer cette fonctionnalité pour les services hébergés à la fois par programmation par <xref:System.ServiceModel.WorkflowServiceHost> à l'aide du modèle objet et également en utilisant un fichier de configuration XML.  
  
 La fonctionnalité de magasin d’instances de workflow SQL (classe**SqlWorkflowInstanceStore** ) n’implémente pas <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> et n’offre donc pas de prise en charge de la persistance pour les services WCF sans flux de travail durables. Il n'implémente pas également <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> et d'où n'offre pas support de persistance pour 3.x workflows. La fonctionnalité prend uniquement en charge la persistance pour les services de workflow et les workflow WF 4.0 (et version ultérieure). La fonctionnalité ne prend pas en charge les bases de données autres que SQL Server 2005 et SQL Server 2008.  
  
 Les rubriques de cette section décrivent les propriétés et fonctionnalités du magasin d’instances de workflow SQL et vous fournissent des détails sur la configuration du magasin.  
  
 Windows Server AppFabric fournit son propre magasin d'instances et des outils pour simplifier la configuration et l'utilisation du magasin d'instances. Pour plus d’informations, consultez [magasin d’instances Windows Server App Fabric](/previous-versions/appfabric/ff383417(v=azure.10)). Pour plus d’informations sur l’application Fabric SQL Server base de données de persistance, consultez [application fabric SQL Server base de données de persistance](/previous-versions/appfabric/ee790819(v=azure.10))  
  
## <a name="in-this-section"></a>Dans cette section  
  
- [Propriétés du magasin d'instances de workflow SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Procédure : activer la persistance SQL pour les workflow et les services de workflow](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Activation d'instance](instance-activation.md)  
  
- [Prise en charge des requêtes](support-for-queries.md)  
  
- [Stocker l'extensibilité](store-extensibility.md)  
  
- [Sécurité](security.md)  
  
- [Base de données de persistance SQL Server](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de persistance](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
