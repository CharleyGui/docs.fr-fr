---
title: 'Comment : personnaliser une stratégie de cache basée sur la durée'
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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040635"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="3aa34-102">Comment : personnaliser une stratégie de cache basée sur la durée</span><span class="sxs-lookup"><span data-stu-id="3aa34-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="3aa34-103">Lors de la création d’une stratégie de cache basée sur la durée, vous pouvez personnaliser le comportement de la mise en cache en spécifiant des valeurs pour l’ancienneté maximale, l’actualisation minimale, l’obsolescence maximale ou la date de synchronisation du cache.</span><span class="sxs-lookup"><span data-stu-id="3aa34-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="3aa34-104">L’objet <xref:System.Net.Cache.HttpRequestCachePolicy> fournit plusieurs constructeurs qui vous permettent de spécifier des combinaisons valides de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="3aa34-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="3aa34-105">Pour créer une stratégie de cache basée sur la durée qui utilise une date de synchronisation du cache</span><span class="sxs-lookup"><span data-stu-id="3aa34-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="3aa34-106">Créez une stratégie de cache basée sur la durée qui utilise une date de synchronisation du cache en passant un objet <xref:System.DateTime> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy> :</span><span class="sxs-lookup"><span data-stu-id="3aa34-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="3aa34-107">La sortie est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3aa34-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="3aa34-108">Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale</span><span class="sxs-lookup"><span data-stu-id="3aa34-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="3aa34-109">Créez une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> comme valeur de paramètre `cacheAgeControl` et en passant un objet <xref:System.TimeSpan> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy> :</span><span class="sxs-lookup"><span data-stu-id="3aa34-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="3aa34-110">Pour l’appel suivant :</span><span class="sxs-lookup"><span data-stu-id="3aa34-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="3aa34-111">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3aa34-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="3aa34-112">Pour créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale et l’ancienneté maximale</span><span class="sxs-lookup"><span data-stu-id="3aa34-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="3aa34-113">Créer une stratégie de cache basée sur la durée qui est basée sur l’actualisation minimale et l’ancienneté maximale en spécifiant <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> comme valeur de paramètre `cacheAgeControl` et en passant deux objets <xref:System.TimeSpan> au constructeur <xref:System.Net.Cache.HttpRequestCachePolicy>, un pour spécifier l’âge maximal pour les ressources et une seconde pour Spécifiez l’actualisation minimale autorisée pour un objet retourné à partir du cache :</span><span class="sxs-lookup"><span data-stu-id="3aa34-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

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

<span data-ttu-id="3aa34-114">Pour l’appel suivant :</span><span class="sxs-lookup"><span data-stu-id="3aa34-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="3aa34-115">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3aa34-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aa34-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aa34-116">See also</span></span>

- [<span data-ttu-id="3aa34-117">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="3aa34-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="3aa34-118">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="3aa34-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="3aa34-119">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="3aa34-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="3aa34-120">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="3aa34-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="3aa34-121">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3aa34-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
