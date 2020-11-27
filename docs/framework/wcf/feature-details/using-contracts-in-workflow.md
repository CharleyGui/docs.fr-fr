---
title: Utilisation de contrats dans le workflow
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: e32130395e05a56de081620f82e0e6f72ae0db38
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289618"
---
# <a name="using-contracts-in-workflow"></a>Utilisation de contrats dans le workflow

Lorsque vous implémentez un service, vous définissez plusieurs contrats qui décrivent le service et les données qu'il envoie et reçoit. Les données sont représentées sous la forme de contrats de données et de contrats de message. WCF et les services de workflow utilisent les définitions de contrat de données et de contrat de message dans le cadre des descriptions de service. Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service. Dans WCF, les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge. Toutefois, dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même ; ils sont exposés dans les métadonnées par un processus nommé inférence de contrat.  
  
## <a name="contract-inference"></a>Inférence de contrat  

 Lorsqu'un service de workflow est hébergé à l'aide d'un objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la définition du workflow est examinée et un contrat est généré en fonction du jeu d'activités de messagerie qui se trouvent dans le workflow. En particulier, les activités et les propriétés suivantes sont utilisées pour générer le contrat :  
  
 <xref:System.ServiceModel.Activities.Receive> Activité  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply> Activité  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Activité  
  
 Le résultat final de l'inférence de contrat est une description du service utilisant les mêmes structures de données que le service WCF et les contrats d'opération. Puis ces informations sont utilisées pour exposer WSDL pour le service de workflow.  
  
## <a name="see-also"></a>Voir aussi

- [Services de workflow](workflow-services.md)
- [Activités de messagerie](messaging-activities.md)
- [Procédure : créer un service de workflow avec des activités de messagerie](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Procédure : créer un service de workflow qui consomme un contrat de service existant](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
