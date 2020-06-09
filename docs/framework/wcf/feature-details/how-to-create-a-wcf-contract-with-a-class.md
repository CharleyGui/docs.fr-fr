---
title: "Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597135"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="93fa1-102">Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe</span><span class="sxs-lookup"><span data-stu-id="93fa1-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="93fa1-103">La méthode recommandée pour créer un contrat Windows Communication Foundation (WCF) consiste à utiliser une interface.</span><span class="sxs-lookup"><span data-stu-id="93fa1-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="93fa1-104">Pour plus d’informations, consultez [Comment : définir un contrat de service](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="93fa1-104">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="93fa1-105">Une autre solution, présentée dans cette rubrique, consiste à créer une classe, à appliquer l'attribut <xref:System.ServiceModel.ServiceContractAttribute> directement sur celle-ci, puis l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur chacune des méthodes de la classe qui font partie du contrat.</span><span class="sxs-lookup"><span data-stu-id="93fa1-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="93fa1-106">`[ServiceContract]` et `[ServiceContractAttribute]` produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="93fa1-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="93fa1-107">La même chose est vraie pour `[OperationContract]` et `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="93fa1-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="93fa1-108">Dans chaque cas, le premier est raccourci pour le deuxième.</span><span class="sxs-lookup"><span data-stu-id="93fa1-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="93fa1-109">Pour plus d’informations sur les contrats de service, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="93fa1-109">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="93fa1-110">Création d'un contrat Windows Communication Foundation à l'aide d'une classe</span><span class="sxs-lookup"><span data-stu-id="93fa1-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="93fa1-111">Créez une classe en utilisant Visual Basic, C# ou tout autre langage de common language runtime.</span><span class="sxs-lookup"><span data-stu-id="93fa1-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="93fa1-112">Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="93fa1-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="93fa1-113">Créez des méthodes dans la classe.</span><span class="sxs-lookup"><span data-stu-id="93fa1-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="93fa1-114">Appliquez la <xref:System.ServiceModel.OperationContractAttribute> classe à chaque méthode qui doit être exposée dans le cadre du contrat WCF public.</span><span class="sxs-lookup"><span data-stu-id="93fa1-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93fa1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="93fa1-115">Example</span></span>  
 <span data-ttu-id="93fa1-116">L'exemple de code suivant présente une classe qui définit un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="93fa1-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="93fa1-117">Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut.</span><span class="sxs-lookup"><span data-stu-id="93fa1-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="93fa1-118">Pour plus d’informations sur ce modèle de message, consultez [Comment : créer un contrat de demande-réponse](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="93fa1-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="93fa1-119">Vous pouvez également créer et utiliser d'autres modèles de message en définissant les propriétés de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="93fa1-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="93fa1-120">Pour obtenir plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](how-to-create-a-one-way-contract.md) et [Comment : créer un contrat duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="93fa1-120">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fa1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93fa1-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
