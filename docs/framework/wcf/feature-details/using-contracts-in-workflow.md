---
title: Utilisation de contrats dans le workflow
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184275"
---
# <a name="using-contracts-in-workflow"></a>Utilisation de contrats dans le workflow
Lorsque vous implémentez un service, vous définissez plusieurs contrats qui décrivent le service et les données qu'il envoie et reçoit. Les données sont représentées sous forme de contrats de données et de contrats de messages; les services WCF et workflow utilisent les définitions des contrats de données et des contrats de messages dans le cadre des descriptions de service. Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service. Dans WCF, les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge. Toutefois, dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même ; ils sont exposés dans les métadonnées par un processus nommé inférence de contrat.  
  
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

- [Services de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Activités de messagerie](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Procédure : créer un service de workflow avec les activités de messagerie](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Guide pratique pour créer un service de workflow qui utilise un contrat de service existant](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
