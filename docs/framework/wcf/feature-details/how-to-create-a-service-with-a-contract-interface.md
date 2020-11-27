---
title: 'Procédure : créer un service avec une interface de contrat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 2234e6fe8d0ee2e0029a061ba96ef84f840f0c9b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286342"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="42e50-102">Procédure : créer un service avec une interface de contrat</span><span class="sxs-lookup"><span data-stu-id="42e50-102">How to: Create a Service with a Contract Interface</span></span>

<span data-ttu-id="42e50-103">La méthode recommandée pour créer un contrat Windows Communication Foundation (WCF) consiste à utiliser une interface.</span><span class="sxs-lookup"><span data-stu-id="42e50-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="42e50-104">Ce contrat spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service.</span><span class="sxs-lookup"><span data-stu-id="42e50-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="42e50-105">Cette interface définit les types d'entrée et de sortie en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface et la classe <xref:System.ServiceModel.OperationContractAttribute> aux méthodes que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="42e50-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="42e50-106">Pour plus d’informations sur les contrats de service, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="42e50-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="42e50-107">Création d'un contrat WCF avec une interface</span><span class="sxs-lookup"><span data-stu-id="42e50-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="42e50-108">Créez une interface à l’aide de Visual Basic, C# ou tout autre langage de common language runtime.</span><span class="sxs-lookup"><span data-stu-id="42e50-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="42e50-109">Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.</span><span class="sxs-lookup"><span data-stu-id="42e50-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="42e50-110">Définissez les méthodes dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="42e50-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="42e50-111">Appliquez la <xref:System.ServiceModel.OperationContractAttribute> classe à chaque méthode qui doit être exposée dans le cadre du contrat WCF public.</span><span class="sxs-lookup"><span data-stu-id="42e50-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42e50-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="42e50-112">Example</span></span>  

 <span data-ttu-id="42e50-113">L'exemple de code suivant présente une interface qui définit un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="42e50-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="42e50-114">Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut.</span><span class="sxs-lookup"><span data-stu-id="42e50-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="42e50-115">Pour plus d’informations sur ce modèle de message, consultez [Comment : créer un contrat de Request-Reply](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="42e50-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="42e50-116">Vous pouvez également créer et utiliser d'autres modèles de message en définissant les propriétés de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="42e50-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="42e50-117">Pour obtenir plus d’exemples, consultez [Comment : créer un contrat de One-Way](how-to-create-a-one-way-contract.md) et [Comment : créer un contrat duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="42e50-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e50-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42e50-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
