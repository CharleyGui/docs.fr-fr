---
title: Services demande-réponse
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 10b82e859369dae4f57e0e13782e2375a304ab02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295520"
---
# <a name="request-reply-services"></a>Services demande-réponse

Les services demande-réponse sont le type de contrat d’opération par défaut dans Windows Communication Foundation (WCF). Les clients effectuent des appels aux opérations de service et attendent une réponse du service. Vous pouvez effectuer des appels à une opération de service de façon synchrone (le client se bloque jusqu'à ce qu'il reçoive une réponse du service ou que l'appel expire) ou de façon asynchrone (le client effectue un appel à l'opération de service, continue à fonctionner et reçoit la réponse du service sur un autre thread).  
  
 Pour créer un contrat de service demande-réponse, définissez votre contrat de service et appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération, tel qu'indiqué dans l'exemple de code suivant.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Il n'est pas nécessaire d'affecter <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à la propriété `false`car il s'agit du comportement par défaut.  
  
## <a name="see-also"></a>Voir aussi

- [Services monodirectionnels](one-way-services.md)
- [Services duplex](duplex-services.md)
