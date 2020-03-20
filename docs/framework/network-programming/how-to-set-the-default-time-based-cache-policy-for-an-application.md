---
title: 'Comment : définir la stratégie de cache à durée définie par défaut pour une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 0aaa26f67ef1ef191060e682690fa14de328b812
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048089"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Comment : définir la stratégie de cache à durée définie par défaut pour une application
Avec la stratégie de cache basée sur la durée par défaut, le comportement de cache d’une application est déterminé par les en-têtes envoyés avec la ressource en cache et par les sections 13 et 14 du document RFC 2616, disponible sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/). Ce comportement de cache convient à la plupart des applications.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Pour utiliser automatiquement la stratégie par défaut pour une application  
  
1. Créez une stratégie basée sur la durée par défaut.  
  
2. Définissez cette stratégie comme stratégie par défaut pour le domaine d’application.  
  
## <a name="example"></a> Exemple  
 Les deux exemples de cette section créent des stratégies identiques.  
  
 L’exemple suivant crée une stratégie basée sur la durée par défaut et la définit comme stratégie par défaut pour le domaine d’application.  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 Vous pouvez également créer une stratégie de cache basée sur la durée par défaut à l’aide la classe <xref:System.Net.Cache.RequestCachePolicy>, comme indiqué dans l’exemple suivant :  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)
- [Stratégie de cache](cache-policy.md)
- [Stratégies de cache basées sur l’emplacement](location-based-cache-policies.md)
- [Stratégies de cache basées sur la durée](time-based-cache-policies.md)
- [\<demandeCaching> Element (Paramètres réseau)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
