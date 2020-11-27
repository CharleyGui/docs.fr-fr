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
# <a name="implementing-service-contracts"></a>Implémentation de contrats de service

Un service est une classe qui expose les fonctionnalités disponibles aux clients à un ou plusieurs points de terminaison. Pour créer un service, écrivez une classe qui implémente un contrat Windows Communication Foundation (WCF). Vous pouvez le faire de deux façons. Vous pouvez définir séparément le contrat comme une interface, puis créer une classe qui implémente cette interface. Vous pouvez également créer la classe et le contrat directement en plaçant l'attribut <xref:System.ServiceModel.ServiceContractAttribute> sur la classe elle-même et l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur les méthodes qui sont à la disposition des clients du service.  
  
## <a name="creating-a-service-class"></a>Création d'une classe de service  

 Voici l'exemple d'un service qui implémente un contrat `IMath` défini séparément.  
  
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
  
 Un service peut également exposer directement un contrat. Voici l'exemple d'une classe de service qui définit et implémente un contrat `MathService`.  
  
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
  
 Notez que les services précédents exposent des contrats différents parce que les noms des contrats sont différents. Dans le premier cas, le contrat exposé est nommé « `IMath` » alors que dans le second cas, le contrat est nommé « `MathService` ».  
  
 Vous pouvez définir quelques éléments au niveau de l'implémentation du service et des opérations, tels que l'accès concurrentiel et l'instanciation. Pour plus d’informations, consultez [conception et implémentation de services](designing-and-implementing-services.md).  
  
 Après avoir implémenté un contrat de service, vous devez créer un ou plusieurs points de terminaison pour le service. Pour plus d’informations, consultez [vue d’ensemble de la création d’un point de terminaison](endpoint-creation-overview.md). Pour plus d’informations sur l’exécution d’un service, consultez [services d’hébergement](hosting-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Conception et implémentation de services](designing-and-implementing-services.md)
- [Procédure : créer un service avec une classe de contrat](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Procédure : créer un service avec une interface de contrat](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Spécification du comportement du service au moment de l'exécution](specifying-service-run-time-behavior.md)
