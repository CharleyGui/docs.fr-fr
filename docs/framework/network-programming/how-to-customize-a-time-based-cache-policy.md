---
title: 'Guide pratique : personnaliser une stratégie de cache basée sur la durée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040635"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="4e188-102">Guide pratique : personnaliser une stratégie de cache basée sur la durée</span><span class="sxs-lookup"><span data-stu-id="4e188-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="4e188-103">Lors de la création d’une stratégie de cache basée sur la durée, vous pouvez personnaliser le comportement de la mise en cache en spécifiant des valeurs pour l’ancienneté maximale, l’actualisation minimale, l’obsolescence maximale ou la date de synchronisation du cache.</span><span class="sxs-lookup"><span data-stu-id="4e188-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="4e188-104">L’objet <xref:System.Net.Cache.HttpRequestCachePolicy> fournit plusieurs constructeurs qui vous permettent de spécifier des combinaisons valides de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4e188-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="4e188-105">Pour créer une stratégie de cache basée sur la durée qui utilise une date de synchronisation du cache</span><span class="sxs-lookup"><span data-stu-id="4e188-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="4e188-106">Créez une stratégie de cache basée sur le temps <xref:System.DateTime> qui utilise <xref:System.Net.Cache.HttpRequestCachePolicy> une date de synchronisation des caches en passant un objet au constructeur :</span><span class="sxs-lookup"><span data-stu-id="4e188-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
    Console.WriteLine("When: {0}", when);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy([when])
    Console.WriteLine("When: {0}", [when])
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="4e188-107">Le résultat ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4e188-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="4e188-108">Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale</span><span class="sxs-lookup"><span data-stu-id="4e188-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="4e188-109">Créez une stratégie de cache basée sur le temps <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> qui `cacheAgeControl` est basée <xref:System.TimeSpan> sur une <xref:System.Net.Cache.HttpRequestCachePolicy> fraîcheur minimale en spécifiant comme valeur de paramètre et en passant un objet au constructeur :</span><span class="sxs-lookup"><span data-stu-id="4e188-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="4e188-110">Pour l’appel suivant :</span><span class="sxs-lookup"><span data-stu-id="4e188-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="4e188-111">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4e188-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="4e188-112">Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale et l’ancienneté maximale</span><span class="sxs-lookup"><span data-stu-id="4e188-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="4e188-113">Créez une stratégie de cache basée <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> sur le `cacheAgeControl` <xref:System.TimeSpan> <xref:System.Net.Cache.HttpRequestCachePolicy> temps qui est basée sur une fraîcheur minimale et un âge maximal en spécifiant comme valeur de paramètre et en passant deux objets au constructeur, l’un pour spécifier l’âge maximum pour les ressources et l’autre pour spécifier la fraîcheur minimale permise pour un objet renvoyé du cache :</span><span class="sxs-lookup"><span data-stu-id="4e188-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="4e188-114">Pour l’appel suivant :</span><span class="sxs-lookup"><span data-stu-id="4e188-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="4e188-115">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4e188-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e188-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e188-116">See also</span></span>

- [<span data-ttu-id="4e188-117">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="4e188-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="4e188-118">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="4e188-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="4e188-119">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="4e188-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="4e188-120">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="4e188-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="4e188-121">\<demandeCaching> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4e188-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
