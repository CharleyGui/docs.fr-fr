---
title: Points de terminaison WCF et méthodes gRPC-gRPC pour les développeurs WCF
description: Comparaison des points de terminaison WCF déclarés avec les attributs ServiceContract et OperationContract et les méthodes gRPC déclarées dans Protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184063"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="21f82-103">Points de terminaison WCF et méthodes gRPC</span><span class="sxs-lookup"><span data-stu-id="21f82-103">WCF endpoints and gRPC methods</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="21f82-104">Dans WCF, lorsque vous écrivez le code de votre application, vous utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="21f82-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="21f82-105">Vous écrivez le code de l’application dans une classe et vous décorez les méthodes avec l’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="21f82-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="21f82-106">Vous déclarez une interface pour le service et ajoutez des attributs [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à l’interface.</span><span class="sxs-lookup"><span data-stu-id="21f82-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="21f82-107">Par exemple, l’équivalent WCF du `greet.proto` service Greeter peut être écrit comme suit :</span><span class="sxs-lookup"><span data-stu-id="21f82-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="21f82-108">Le chapitre 3 a montré que les définitions de message Protobuf sont utilisées pour générer des classes de données.</span><span class="sxs-lookup"><span data-stu-id="21f82-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="21f82-109">Les déclarations de service et de méthode sont utilisées pour générer les classes de base que vous héritez de pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="21f82-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="21f82-110">Il vous suffit de déclarer les méthodes à implémenter `.proto` dans le fichier, et le compilateur génère une classe de base avec des méthodes virtuelles que vous devez substituer.</span><span class="sxs-lookup"><span data-stu-id="21f82-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="21f82-111">Propriétés de OperationContract</span><span class="sxs-lookup"><span data-stu-id="21f82-111">OperationContract properties</span></span>

<span data-ttu-id="21f82-112">L’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) possède des propriétés permettant de contrôler ou d’affiner son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="21f82-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="21f82-113">les méthodes gRPC n’offrent pas ce type de contrôle.</span><span class="sxs-lookup"><span data-stu-id="21f82-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="21f82-114">Le tableau suivant définit ces `OperationContract` propriétés et comment les fonctionnalités qu’elles spécifient sont (ou ne sont pas) traitées dans gRPC :</span><span class="sxs-lookup"><span data-stu-id="21f82-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="21f82-115">Propriété`OperationContract`</span><span class="sxs-lookup"><span data-stu-id="21f82-115">`OperationContract` property</span></span> | <span data-ttu-id="21f82-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="21f82-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="21f82-117">URI identifiant l’opération.</span><span class="sxs-lookup"><span data-stu-id="21f82-117">URI identifying the operation.</span></span> <span data-ttu-id="21f82-118">gRPC `package`utilise le nom du `service` et `rpc` `.proto` du fichier.</span><span class="sxs-lookup"><span data-stu-id="21f82-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="21f82-119">Toutes les méthodes de service `Task` gRPC retournent des objets.</span><span class="sxs-lookup"><span data-stu-id="21f82-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="21f82-120">Voir la remarque ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="21f82-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="21f82-121">Les méthodes gRPC à sens unique `Empty` renvoient des résultats ou utilisent la diffusion en continu du client.</span><span class="sxs-lookup"><span data-stu-id="21f82-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="21f82-122">Voir la remarque ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="21f82-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="21f82-123">Lié à SOAP, aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="21f82-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="21f82-124">Aucun chiffrement de message ; le chiffrement réseau est géré au niveau de la couche de transport (TLS sur HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="21f82-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="21f82-125">Lié à SOAP, aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="21f82-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="21f82-126">La `IsInitiating` propriété vous permet d’indiquer qu’une méthode dans un [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) ne peut pas être la première méthode appelée dans le cadre d’une session.</span><span class="sxs-lookup"><span data-stu-id="21f82-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="21f82-127">La `IsTerminating` propriété force le serveur à fermer la session après l’appel d’une opération (ou le client, s’il est utilisé sur un client de rappel).</span><span class="sxs-lookup"><span data-stu-id="21f82-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="21f82-128">Dans gRPC, les flux sont créés par des méthodes uniques et fermés explicitement.</span><span class="sxs-lookup"><span data-stu-id="21f82-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="21f82-129">Consultez [diffusion en continu gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="21f82-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="21f82-130">Pour plus d’informations sur la sécurité et le chiffrement gRPC, consultez le [chapitre 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="21f82-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="21f82-131">[Précédent](wcf-services-to-grpc-comparison.md)
>[Suivant](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="21f82-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
