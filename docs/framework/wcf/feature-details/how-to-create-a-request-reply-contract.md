---
title: 'Procédure : créer un contrat de demande-réponse'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 506ce527348286bb53223c64245c74e4cb21879a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286550"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="e9c12-102">Procédure : créer un contrat de demande-réponse</span><span class="sxs-lookup"><span data-stu-id="e9c12-102">How to: Create a Request-Reply Contract</span></span>

<span data-ttu-id="e9c12-103">Un contrat demande-réponse spécifie une méthode qui retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="e9c12-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="e9c12-104">La réponse doit être envoyée et corrélée à la demande selon les termes de ce contrat.</span><span class="sxs-lookup"><span data-stu-id="e9c12-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="e9c12-105">Même si la méthode ne retourne aucune réponse (`void` dans C# ou un `Sub` dans Visual Basic), l'infrastructure crée et envoie un message vide à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="e9c12-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="e9c12-106">Pour empêcher l'envoi d'un message de réponse vide, utilisez un contrat unidirectionnel pour l'opération.</span><span class="sxs-lookup"><span data-stu-id="e9c12-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="e9c12-107">Pour créer un contrat demande-réponse</span><span class="sxs-lookup"><span data-stu-id="e9c12-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="e9c12-108">Créez une interface dans le langage de programmation de votre choix.</span><span class="sxs-lookup"><span data-stu-id="e9c12-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="e9c12-109">Appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.</span><span class="sxs-lookup"><span data-stu-id="e9c12-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="e9c12-110">Appliquez l'attribut <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode que les clients peuvent appeler.</span><span class="sxs-lookup"><span data-stu-id="e9c12-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="e9c12-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e9c12-111">Optional.</span></span> <span data-ttu-id="e9c12-112">Affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> la valeur `true` pour empêcher l'envoi d'un message de réponse vide.</span><span class="sxs-lookup"><span data-stu-id="e9c12-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="e9c12-113">Par défaut, toutes les opérations sont des contrats demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="e9c12-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c12-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e9c12-114">Example</span></span>  

 <span data-ttu-id="e9c12-115">L'exemple suivant définit un contrat pour un service de calculatrice qui fournit des méthodes `Add` et `Subtract`.</span><span class="sxs-lookup"><span data-stu-id="e9c12-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="e9c12-116">La méthode `Multiply` ne fait pas partie du contrat car elle n'est pas marquée par la classe <xref:System.ServiceModel.OperationContractAttribute> et n'est pas, par conséquent, accessible aux clients.</span><span class="sxs-lookup"><span data-stu-id="e9c12-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
- <span data-ttu-id="e9c12-117">Pour plus d’informations sur la façon de spécifier des contrats d’opération, consultez la <xref:System.ServiceModel.OperationContractAttribute> classe et la <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e9c12-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="e9c12-118">Appliquer les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> entraîne la génération automatique de définitions de contrat de service dans un document WSDL (Web Services Description Language) une fois le service déployé.</span><span class="sxs-lookup"><span data-stu-id="e9c12-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="e9c12-119">Le document est téléchargé en ajoutant `?wsdl` à l'adresse de base HTTP du service.</span><span class="sxs-lookup"><span data-stu-id="e9c12-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="e9c12-120">Par exemple : `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="e9c12-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c12-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9c12-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="e9c12-122">Conception de contrats de service</span><span class="sxs-lookup"><span data-stu-id="e9c12-122">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="e9c12-123">Procédure : créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="e9c12-123">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
