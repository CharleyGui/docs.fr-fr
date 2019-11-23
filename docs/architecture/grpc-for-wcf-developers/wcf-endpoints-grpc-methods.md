---
title: Points de terminaison WCF et méthodes gRPC-gRPC pour les développeurs WCF
description: Comparaison des points de terminaison WCF déclarés avec les attributs ServiceContract et OperationContract et les méthodes gRPC déclarées dans Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 763862a363afc6aab72335050cf4822754816c7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966935"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="ee118-103">Points de terminaison WCF et méthodes gRPC</span><span class="sxs-lookup"><span data-stu-id="ee118-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="ee118-104">Dans WCF, lorsque vous écrivez le code de votre application, vous utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee118-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="ee118-105">Vous écrivez le code de l’application dans une classe et vous décorez les méthodes avec l’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ee118-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="ee118-106">Vous déclarez une interface pour le service et ajoutez des attributs [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à l’interface.</span><span class="sxs-lookup"><span data-stu-id="ee118-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="ee118-107">Par exemple, l’équivalent WCF du service `greet.proto` Greeter peut être écrit comme suit :</span><span class="sxs-lookup"><span data-stu-id="ee118-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="ee118-108">Le chapitre 3 a montré que les définitions de message Protobuf sont utilisées pour générer des classes de données.</span><span class="sxs-lookup"><span data-stu-id="ee118-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="ee118-109">Les déclarations de service et de méthode sont utilisées pour générer les classes de base que vous héritez de pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="ee118-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="ee118-110">Il vous suffit de déclarer les méthodes à implémenter dans le fichier `.proto`, et le compilateur génère une classe de base avec des méthodes virtuelles que vous devez substituer.</span><span class="sxs-lookup"><span data-stu-id="ee118-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="ee118-111">Propriétés de OperationContract</span><span class="sxs-lookup"><span data-stu-id="ee118-111">OperationContract properties</span></span>

<span data-ttu-id="ee118-112">L’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) possède des propriétés permettant de contrôler ou d’affiner son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="ee118-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="ee118-113">les méthodes gRPC n’offrent pas ce type de contrôle.</span><span class="sxs-lookup"><span data-stu-id="ee118-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="ee118-114">Le tableau suivant présente les propriétés de `OperationContract` et la façon dont les fonctionnalités qu’elles spécifient sont (ou ne sont pas) traitées dans gRPC :</span><span class="sxs-lookup"><span data-stu-id="ee118-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="ee118-115">Propriété `OperationContract`</span><span class="sxs-lookup"><span data-stu-id="ee118-115">`OperationContract` property</span></span> | <span data-ttu-id="ee118-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="ee118-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="ee118-117">URI identifiant l’opération.</span><span class="sxs-lookup"><span data-stu-id="ee118-117">URI identifying the operation.</span></span> <span data-ttu-id="ee118-118">gRPC utilise le nom de l' `package`, `service` et `rpc` du fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="ee118-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="ee118-119">Toutes les méthodes de service gRPC retournent des objets `Task`.</span><span class="sxs-lookup"><span data-stu-id="ee118-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="ee118-120">Voir la remarque ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ee118-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="ee118-121">Les méthodes gRPC à sens unique retournent `Empty` résultats ou utilisent la diffusion en continu du client.</span><span class="sxs-lookup"><span data-stu-id="ee118-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="ee118-122">Voir la remarque ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ee118-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="ee118-123">Lié à SOAP, aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="ee118-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="ee118-124">Aucun chiffrement de message ; le chiffrement réseau est géré au niveau de la couche de transport (TLS sur HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="ee118-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="ee118-125">Lié à SOAP, aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="ee118-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="ee118-126">La propriété `IsInitiating` vous permet d’indiquer qu’une méthode dans un [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) ne peut pas être la première méthode appelée dans le cadre d’une session.</span><span class="sxs-lookup"><span data-stu-id="ee118-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="ee118-127">La propriété `IsTerminating` oblige le serveur à fermer la session après l’appel d’une opération (ou le client, s’il est utilisé sur un client de rappel).</span><span class="sxs-lookup"><span data-stu-id="ee118-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="ee118-128">Dans gRPC, les flux sont créés par des méthodes uniques et fermés explicitement.</span><span class="sxs-lookup"><span data-stu-id="ee118-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="ee118-129">Consultez [diffusion en continu gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="ee118-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="ee118-130">Pour plus d’informations sur la sécurité et le chiffrement gRPC, consultez le [chapitre 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="ee118-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ee118-131">[Précédent](wcf-services-to-grpc-comparison.md)
>[Suivant](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ee118-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
