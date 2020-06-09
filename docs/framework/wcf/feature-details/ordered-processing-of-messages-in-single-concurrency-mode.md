---
title: Traitement ordonné des messages en mode de concurrence simple
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: baba75fe398d974f989acfda7ef7366986f6813b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598734"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Traitement ordonné des messages en mode de concurrence simple
WCF ne fournit aucune garantie quant à l’ordre dans lequel les messages sont traités, à moins que le canal sous-jacent soit de session.  Par exemple, un service WCF qui utilise MsmqInputChannel, qui n’est pas un canal de session, ne parviendra pas à traiter les messages dans l’ordre. Dans certains cas, un développeur peut souhaiter le comportement de traitement de l’ordre, mais ne souhaite pas utiliser les sessions. Cette rubrique décrit comment configurer ce comportement lorsqu'un service s'exécute en mode de concurrence simple.  
  
## <a name="in-order-message-processing"></a>Traitement des messages dans l'ordre  
 Un nouvel attribut nommé <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a été ajouté à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>. Lorsque <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a la valeur true et <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single> les messages envoyés au service sont traités dans l'ordre. L'extrait de code suivant illustre comment définir ces attributs.  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Si une autre valeur est affectée à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, une exception <xref:System.InvalidOperationException> est levée.  
  
## <a name="see-also"></a>Voir aussi

- [Sessions, instanciation et concurrence](sessions-instancing-and-concurrency.md)
- [Concurrency](../samples/concurrency.md)
