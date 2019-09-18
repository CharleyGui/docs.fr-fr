---
title: 'Procédure : définir la stratégie de cache basée sur la durée par défaut pour une application'
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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048089"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="baa41-102">Procédure : définir la stratégie de cache basée sur la durée par défaut pour une application</span><span class="sxs-lookup"><span data-stu-id="baa41-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="baa41-103">Avec la stratégie de cache basée sur la durée par défaut, le comportement de cache d’une application est déterminé par les en-têtes envoyés avec la ressource en cache et par les sections 13 et 14 du document RFC 2616, disponible sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="baa41-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="baa41-104">Ce comportement de cache convient à la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="baa41-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="baa41-105">Pour utiliser automatiquement la stratégie par défaut pour une application</span><span class="sxs-lookup"><span data-stu-id="baa41-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="baa41-106">Créez une stratégie basée sur la durée par défaut.</span><span class="sxs-lookup"><span data-stu-id="baa41-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="baa41-107">Définissez cette stratégie comme stratégie par défaut pour le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="baa41-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa41-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="baa41-108">Example</span></span>  
 <span data-ttu-id="baa41-109">Les deux exemples de cette section créent des stratégies identiques.</span><span class="sxs-lookup"><span data-stu-id="baa41-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="baa41-110">L’exemple suivant crée une stratégie basée sur la durée par défaut et la définit comme stratégie par défaut pour le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="baa41-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="baa41-111">Vous pouvez également créer une stratégie de cache basée sur la durée par défaut à l’aide la classe <xref:System.Net.Cache.RequestCachePolicy>, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="baa41-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baa41-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baa41-112">See also</span></span>

- [<span data-ttu-id="baa41-113">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="baa41-113">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="baa41-114">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="baa41-114">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="baa41-115">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="baa41-115">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="baa41-116">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="baa41-116">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="baa41-117">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="baa41-117">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
