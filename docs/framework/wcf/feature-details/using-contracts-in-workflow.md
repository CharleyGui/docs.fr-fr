---
title: Utilisation de contrats dans le workflow
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595009"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="b0b88-102">Utilisation de contrats dans le workflow</span><span class="sxs-lookup"><span data-stu-id="b0b88-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="b0b88-103">Lorsque vous implémentez un service, vous définissez plusieurs contrats qui décrivent le service et les données qu'il envoie et reçoit.</span><span class="sxs-lookup"><span data-stu-id="b0b88-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="b0b88-104">Les données sont représentées sous la forme de contrats de données et de contrats de message. WCF et les services de workflow utilisent les définitions de contrat de données et de contrat de message dans le cadre des descriptions de service.</span><span class="sxs-lookup"><span data-stu-id="b0b88-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="b0b88-105">Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service.</span><span class="sxs-lookup"><span data-stu-id="b0b88-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="b0b88-106">Dans WCF, les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="b0b88-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="b0b88-107">Toutefois, dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même ; ils sont exposés dans les métadonnées par un processus nommé inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="b0b88-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="b0b88-108">Inférence de contrat</span><span class="sxs-lookup"><span data-stu-id="b0b88-108">Contract Inference</span></span>  
 <span data-ttu-id="b0b88-109">Lorsqu'un service de workflow est hébergé à l'aide d'un objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la définition du workflow est examinée et un contrat est généré en fonction du jeu d'activités de messagerie qui se trouvent dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="b0b88-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="b0b88-110">En particulier, les activités et les propriétés suivantes sont utilisées pour générer le contrat :</span><span class="sxs-lookup"><span data-stu-id="b0b88-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="b0b88-111"><xref:System.ServiceModel.Activities.Receive> Activité</span><span class="sxs-lookup"><span data-stu-id="b0b88-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="b0b88-112"><xref:System.ServiceModel.Activities.SendReply> Activité</span><span class="sxs-lookup"><span data-stu-id="b0b88-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="b0b88-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activité</span><span class="sxs-lookup"><span data-stu-id="b0b88-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="b0b88-114">Le résultat final de l'inférence de contrat est une description du service utilisant les mêmes structures de données que le service WCF et les contrats d'opération.</span><span class="sxs-lookup"><span data-stu-id="b0b88-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="b0b88-115">Puis ces informations sont utilisées pour exposer WSDL pour le service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b0b88-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b88-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0b88-116">See also</span></span>

- [<span data-ttu-id="b0b88-117">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="b0b88-117">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="b0b88-118">Activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="b0b88-118">Messaging Activities</span></span>](messaging-activities.md)
- [<span data-ttu-id="b0b88-119">Procédure : créer un service de workflow avec les activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="b0b88-119">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="b0b88-120">Guide pratique pour créer un service de workflow qui utilise un contrat de service existant</span><span class="sxs-lookup"><span data-stu-id="b0b88-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
