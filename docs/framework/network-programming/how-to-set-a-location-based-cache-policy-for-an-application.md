---
title: 'Procédure : définir une stratégie de cache basée sur l’emplacement pour une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 1bbbb558134e5f11537de0efef594be2b964cdcb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647383"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="6b3f3-102">Procédure : définir une stratégie de cache basée sur l’emplacement pour une application</span><span class="sxs-lookup"><span data-stu-id="6b3f3-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="6b3f3-103">Avec une stratégie de cache basée sur l’emplacement, une application peut définir explicitement le comportement de cache en fonction de l’emplacement de la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="6b3f3-104">Cette rubrique explique comment définir la stratégie de cache par programmation.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="6b3f3-105">Pour plus d’informations sur la définition de la stratégie pour une application en utilisant les fichiers de configuration, consultez [\<requestCaching>, élément (paramètres réseau)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6b3f3-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="6b3f3-106">Pour définir une stratégie de cache basée sur l’emplacement pour une application</span><span class="sxs-lookup"><span data-stu-id="6b3f3-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="6b3f3-107">Créez un objet <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="6b3f3-108">Définissez l’objet de stratégie par défaut pour le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="6b3f3-109">Pour définir une stratégie qui obtient les ressources demandées à partir d’un cache</span><span class="sxs-lookup"><span data-stu-id="6b3f3-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="6b3f3-110">Créez une stratégie qui obtient les ressources demandées à partir d’un cache disponible ou, sinon, qui envoie les demandes au serveur (pour cela, définissez le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>).</span><span class="sxs-lookup"><span data-stu-id="6b3f3-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="6b3f3-111">Une demande peut être traitée par n’importe quel cache entre le client et le serveur, y compris les caches distants.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="6b3f3-112">Pour définir une stratégie qui empêche tous les caches de fournir des ressources</span><span class="sxs-lookup"><span data-stu-id="6b3f3-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="6b3f3-113">Créez une stratégie qui empêche tous les caches de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="6b3f3-114">Ce niveau de stratégie supprime la ressource qui se trouve éventuellement dans le cache local et spécifie que les caches distants doivent également supprimer cette ressource.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="6b3f3-115">Pour définir une stratégie qui retourne les ressources demandées uniquement si elles sont dans le cache local</span><span class="sxs-lookup"><span data-stu-id="6b3f3-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="6b3f3-116">Créez une stratégie qui retourne les ressources demandées uniquement si elles sont dans le cache local en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="6b3f3-117">Si la ressource demandée n’est pas dans le cache, une exception <xref:System.Net.WebException> est levée.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="6b3f3-118">Pour définir une stratégie qui empêche le cache local de fournir des ressources</span><span class="sxs-lookup"><span data-stu-id="6b3f3-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="6b3f3-119">Créez une stratégie qui empêche le cache local de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="6b3f3-120">Si la ressource demandée se trouve dans un cache intermédiaire et qu’elle a été revalidée, le cache intermédiaire est autorisé à fournir cette ressource.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="6b3f3-121">Pour définir une stratégie qui empêche tous les caches de fournir les ressources demandées</span><span class="sxs-lookup"><span data-stu-id="6b3f3-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="6b3f3-122">Créez une stratégie qui empêche tous les caches de fournir les ressources demandées en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="6b3f3-123">La ressource retournée par le serveur peut être stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="6b3f3-124">Pour définir une stratégie qui autorise tous les caches à fournir les ressources demandées si la ressource sur le serveur n’est pas plus récente que la copie en cache</span><span class="sxs-lookup"><span data-stu-id="6b3f3-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="6b3f3-125">Créez une stratégie qui autorise tous les caches à fournir les ressources demandées si la ressource sur le serveur n’est pas plus récente que la copie en cache, en définissant le niveau de cache à <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="6b3f3-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b3f3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b3f3-126">See also</span></span>

- [<span data-ttu-id="6b3f3-127">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="6b3f3-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="6b3f3-128">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="6b3f3-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="6b3f3-129">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="6b3f3-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="6b3f3-130">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="6b3f3-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="6b3f3-131">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6b3f3-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
