---
title: 'Comment : définir une stratégie de cache basée sur l’emplacement pour une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180778"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="e9704-102">Comment : définir une stratégie de cache basée sur l’emplacement pour une application</span><span class="sxs-lookup"><span data-stu-id="e9704-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="e9704-103">Avec une stratégie de cache basée sur l’emplacement, une application peut définir explicitement le comportement de cache en fonction de l’emplacement de la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="e9704-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="e9704-104">Cette rubrique explique comment définir la stratégie de cache par programmation.</span><span class="sxs-lookup"><span data-stu-id="e9704-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="e9704-105">Pour plus d’informations sur la définition de la stratégie d’une application à l’aide des fichiers de configuration, voir [ \<demandeCaching> Element (Paramètres réseau)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e9704-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="e9704-106">Pour définir une stratégie de cache basée sur l’emplacement pour une application</span><span class="sxs-lookup"><span data-stu-id="e9704-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="e9704-107">Créez un objet <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="e9704-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="e9704-108">Définissez cette stratégie comme stratégie par défaut pour le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e9704-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="e9704-109">Pour définir une stratégie qui obtient les ressources demandées à partir d’un cache</span><span class="sxs-lookup"><span data-stu-id="e9704-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="e9704-110">Créez une stratégie qui obtient les ressources demandées à partir d’un cache disponible ou, sinon, qui envoie les demandes au serveur (pour cela, définissez le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>).</span><span class="sxs-lookup"><span data-stu-id="e9704-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="e9704-111">Une demande peut être traitée par n’importe quel cache entre le client et le serveur, y compris les caches distants.</span><span class="sxs-lookup"><span data-stu-id="e9704-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="e9704-112">Pour définir une stratégie qui empêche tous les caches de fournir des ressources</span><span class="sxs-lookup"><span data-stu-id="e9704-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="e9704-113">Créez une stratégie qui empêche tous les caches de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="e9704-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="e9704-114">Ce niveau de stratégie supprime la ressource qui se trouve éventuellement dans le cache local et spécifie que les caches distants doivent également supprimer cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e9704-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="e9704-115">Pour définir une stratégie qui retourne les ressources demandées uniquement si elles sont dans le cache local</span><span class="sxs-lookup"><span data-stu-id="e9704-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="e9704-116">Créez une stratégie qui retourne les ressources demandées uniquement si elles sont dans le cache local en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="e9704-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="e9704-117">Si la ressource demandée n’est pas dans le cache, une exception <xref:System.Net.WebException> est levée.</span><span class="sxs-lookup"><span data-stu-id="e9704-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="e9704-118">Pour définir une stratégie qui empêche le cache local de fournir des ressources</span><span class="sxs-lookup"><span data-stu-id="e9704-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="e9704-119">Créez une stratégie qui empêche le cache local de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="e9704-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="e9704-120">Si la ressource demandée se trouve dans un cache intermédiaire et qu’elle a été revalidée, le cache intermédiaire est autorisé à fournir cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e9704-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="e9704-121">Pour définir une stratégie qui empêche tous les caches de fournir les ressources demandées</span><span class="sxs-lookup"><span data-stu-id="e9704-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="e9704-122">Créez une stratégie qui empêche tous les caches de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="e9704-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="e9704-123">La ressource retournée par le serveur peut être stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="e9704-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="e9704-124">Pour définir une stratégie qui autorise tous les caches à fournir les ressources demandées si la ressource sur le serveur n’est pas plus récente que la copie en cache</span><span class="sxs-lookup"><span data-stu-id="e9704-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="e9704-125">Créez une stratégie qui autorise tous les caches à fournir les ressources demandées si la ressource sur le serveur n’est pas plus récente que la copie en cache, en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="e9704-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e9704-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9704-126">See also</span></span>

- [<span data-ttu-id="e9704-127">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="e9704-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="e9704-128">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="e9704-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="e9704-129">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="e9704-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="e9704-130">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="e9704-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="e9704-131">\<demandeCaching> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e9704-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
