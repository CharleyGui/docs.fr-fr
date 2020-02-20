---
title: Points de terminaison WCF et méthodes gRPC-gRPC pour les développeurs WCF
description: Comparaison des points de terminaison WCF déclarés avec les attributs ServiceContract et OperationContract et les méthodes gRPC déclarées dans Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503433"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="8e6fe-103">Points de terminaison WCF et méthodes gRPC</span><span class="sxs-lookup"><span data-stu-id="8e6fe-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="8e6fe-104">Dans Windows Communication Foundation (WCF), lorsque vous écrivez le code de votre application, vous utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e6fe-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="8e6fe-105">Vous écrivez le code de l’application dans une classe et vous décorez les méthodes avec l’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8e6fe-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="8e6fe-106">Vous déclarez une interface pour le service et ajoutez des attributs [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à l’interface.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="8e6fe-107">Par exemple, l’équivalent WCF du service `greet.proto` Greeter peut être écrit comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e6fe-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="8e6fe-108">Le chapitre 3 a montré que les définitions de message Protobuf sont utilisées pour générer des classes de données.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="8e6fe-109">Les déclarations de service et de méthode sont utilisées pour générer les classes de base que vous héritez de pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="8e6fe-110">Il vous suffit de déclarer les méthodes à implémenter dans le fichier `.proto`, et le compilateur génère une classe de base avec des méthodes virtuelles que vous devez substituer.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="8e6fe-111">Propriétés de OperationContract</span><span class="sxs-lookup"><span data-stu-id="8e6fe-111">OperationContract properties</span></span>

<span data-ttu-id="8e6fe-112">L’attribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) possède des propriétés permettant de contrôler ou d’affiner son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="8e6fe-113">les méthodes gRPC n’offrent pas ce type de contrôle.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="8e6fe-114">Le tableau suivant répertorie ces propriétés de `OperationContract` et décrit comment les fonctionnalités qu’elles spécifient sont (ou ne sont pas) traitées dans gRPC :</span><span class="sxs-lookup"><span data-stu-id="8e6fe-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="8e6fe-115">Propriété `OperationContract`</span><span class="sxs-lookup"><span data-stu-id="8e6fe-115">`OperationContract` property</span></span> | <span data-ttu-id="8e6fe-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="8e6fe-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="8e6fe-117">Un URI identifie l’opération.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-117">A URI identifies the operation.</span></span> <span data-ttu-id="8e6fe-118">gRPC utilise le nom de `package`, `service`et `rpc` dans le fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="8e6fe-119">Toutes les méthodes de service gRPC retournent des objets `Task`.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="8e6fe-120">Consultez le paragraphe après ce tableau.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="8e6fe-121">Les méthodes gRPC à sens unique retournent `Empty` résultats ou utilisent la diffusion en continu du client.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="8e6fe-122">Consultez le paragraphe après ce tableau.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="8e6fe-123">Cette propriété est liée à SOAP et n’a aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="8e6fe-124">Il n’y a pas de chiffrement des messages.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-124">There's no message encryption.</span></span> <span data-ttu-id="8e6fe-125">Le chiffrement réseau est géré au niveau de la couche de transport (TLS sur HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="8e6fe-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="8e6fe-126">Cette propriété est liée à SOAP et n’a aucune signification dans gRPC.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="8e6fe-127">La propriété `IsInitiating` vous permet d’indiquer qu’une méthode dans [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) ne peut pas être la première méthode appelée dans le cadre d’une session.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="8e6fe-128">La propriété `IsTerminating` oblige le serveur à fermer la session après l’appel d’une opération (ou le client, si la propriété est utilisée sur un client de rappel).</span><span class="sxs-lookup"><span data-stu-id="8e6fe-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="8e6fe-129">Dans gRPC, les flux sont créés par des méthodes uniques et fermés explicitement.</span><span class="sxs-lookup"><span data-stu-id="8e6fe-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="8e6fe-130">Consultez [diffusion en continu gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="8e6fe-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="8e6fe-131">Pour plus d’informations sur la sécurité et le chiffrement gRPC, consultez le [chapitre 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="8e6fe-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e6fe-132">[Précédent](wcf-services-to-grpc-comparison.md)
>[Suivant](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8e6fe-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
