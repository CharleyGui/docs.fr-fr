---
title: Implémentation de contrats de service
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 121922e3de62653babdac084d6bd226f7263e33c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262734"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="d2667-102">Implémentation de contrats de service</span><span class="sxs-lookup"><span data-stu-id="d2667-102">Implementing Service Contracts</span></span>

<span data-ttu-id="d2667-103">Un service est une classe qui expose les fonctionnalités disponibles aux clients à un ou plusieurs points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d2667-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="d2667-104">Pour créer un service, écrivez une classe qui implémente un contrat Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d2667-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="d2667-105">Vous pouvez le faire de deux façons.</span><span class="sxs-lookup"><span data-stu-id="d2667-105">You can do this in one of two ways.</span></span> <span data-ttu-id="d2667-106">Vous pouvez définir séparément le contrat comme une interface, puis créer une classe qui implémente cette interface.</span><span class="sxs-lookup"><span data-stu-id="d2667-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="d2667-107">Vous pouvez également créer la classe et le contrat directement en plaçant l'attribut <xref:System.ServiceModel.ServiceContractAttribute> sur la classe elle-même et l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur les méthodes qui sont à la disposition des clients du service.</span><span class="sxs-lookup"><span data-stu-id="d2667-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="d2667-108">Création d'une classe de service</span><span class="sxs-lookup"><span data-stu-id="d2667-108">Creating a service class</span></span>  

 <span data-ttu-id="d2667-109">Voici l'exemple d'un service qui implémente un contrat `IMath` défini séparément.</span><span class="sxs-lookup"><span data-stu-id="d2667-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="d2667-110">Un service peut également exposer directement un contrat.</span><span class="sxs-lookup"><span data-stu-id="d2667-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="d2667-111">Voici l'exemple d'une classe de service qui définit et implémente un contrat `MathService`.</span><span class="sxs-lookup"><span data-stu-id="d2667-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="d2667-112">Notez que les services précédents exposent des contrats différents parce que les noms des contrats sont différents.</span><span class="sxs-lookup"><span data-stu-id="d2667-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="d2667-113">Dans le premier cas, le contrat exposé est nommé « `IMath` » alors que dans le second cas, le contrat est nommé « `MathService` ».</span><span class="sxs-lookup"><span data-stu-id="d2667-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="d2667-114">Vous pouvez définir quelques éléments au niveau de l'implémentation du service et des opérations, tels que l'accès concurrentiel et l'instanciation.</span><span class="sxs-lookup"><span data-stu-id="d2667-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="d2667-115">Pour plus d’informations, consultez [conception et implémentation de services](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2667-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="d2667-116">Après avoir implémenté un contrat de service, vous devez créer un ou plusieurs points de terminaison pour le service.</span><span class="sxs-lookup"><span data-stu-id="d2667-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="d2667-117">Pour plus d’informations, consultez [vue d’ensemble de la création d’un point de terminaison](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2667-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="d2667-118">Pour plus d’informations sur l’exécution d’un service, consultez [services d’hébergement](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2667-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2667-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2667-119">See also</span></span>

- [<span data-ttu-id="d2667-120">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="d2667-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="d2667-121">Procédure : créer un service avec une classe de contrat</span><span class="sxs-lookup"><span data-stu-id="d2667-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="d2667-122">Procédure : créer un service avec une interface de contrat</span><span class="sxs-lookup"><span data-stu-id="d2667-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="d2667-123">Spécification du comportement du service au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d2667-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
