---
title: 'Comment : créer un contrat demande-réponse'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593436"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="0aaa5-102">Comment : créer un contrat demande-réponse</span><span class="sxs-lookup"><span data-stu-id="0aaa5-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="0aaa5-103">Un contrat demande-réponse spécifie une méthode qui retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="0aaa5-104">La réponse doit être envoyée et corrélée à la demande selon les termes de ce contrat.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="0aaa5-105">Même si la méthode ne retourne aucune réponse (`void` dans C# ou un `Sub` dans Visual Basic), l'infrastructure crée et envoie un message vide à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="0aaa5-106">Pour empêcher l'envoi d'un message de réponse vide, utilisez un contrat unidirectionnel pour l'opération.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="0aaa5-107">Pour créer un contrat demande-réponse</span><span class="sxs-lookup"><span data-stu-id="0aaa5-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="0aaa5-108">Créez une interface dans le langage de programmation de votre choix.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="0aaa5-109">Appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="0aaa5-110">Appliquez l'attribut <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode que les clients peuvent appeler.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="0aaa5-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-111">Optional.</span></span> <span data-ttu-id="0aaa5-112">Affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> la valeur `true` pour empêcher l'envoi d'un message de réponse vide.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="0aaa5-113">Par défaut, toutes les opérations sont des contrats demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aaa5-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="0aaa5-114">Example</span></span>  
 <span data-ttu-id="0aaa5-115">L'exemple suivant définit un contrat pour un service de calculatrice qui fournit des méthodes `Add` et `Subtract`.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="0aaa5-116">La méthode `Multiply` ne fait pas partie du contrat car elle n'est pas marquée par la classe <xref:System.ServiceModel.OperationContractAttribute> et n'est pas, par conséquent, accessible aux clients.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="0aaa5-117">Pour plus d’informations sur la façon de spécifier des contrats d’opération, consultez la <xref:System.ServiceModel.OperationContractAttribute> classe et la <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="0aaa5-118">Appliquer les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> entraîne la génération automatique de définitions de contrat de service dans un document WSDL (Web Services Description Language) une fois le service déployé.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="0aaa5-119">Le document est téléchargé en ajoutant `?wsdl` à l'adresse de base HTTP du service.</span><span class="sxs-lookup"><span data-stu-id="0aaa5-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="0aaa5-120">Par exemple : `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="0aaa5-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aaa5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aaa5-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="0aaa5-122">Conception de contrats de service</span><span class="sxs-lookup"><span data-stu-id="0aaa5-122">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="0aaa5-123">Comment : créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="0aaa5-123">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
