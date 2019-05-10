---
title: Fabrication de canal et mise en cache
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 94b3cb22c76a215944d044db0f4392005e49f2ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645415"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="f0e29-102">Fabrication de canal et mise en cache</span><span class="sxs-lookup"><span data-stu-id="f0e29-102">Channel Factory and Caching</span></span>
<span data-ttu-id="f0e29-103">Les applications clientes WCF utilisent la classe <xref:System.ServiceModel.ChannelFactory%601> pour créer un canal de communication avec un service WCF.</span><span class="sxs-lookup"><span data-stu-id="f0e29-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="f0e29-104">La création d'instances <xref:System.ServiceModel.ChannelFactory%601> entraîne une certaine charge, car elle comporte les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0e29-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
- <span data-ttu-id="f0e29-105">Construction de l’arborescence <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="f0e29-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
- <span data-ttu-id="f0e29-106">Refléter tous les types CLR requis</span><span class="sxs-lookup"><span data-stu-id="f0e29-106">Reflecting all of the required CLR types</span></span>  
  
- <span data-ttu-id="f0e29-107">Construction de la pile de canaux</span><span class="sxs-lookup"><span data-stu-id="f0e29-107">Constructing the channel stack</span></span>  
  
- <span data-ttu-id="f0e29-108">Suppression de ressources</span><span class="sxs-lookup"><span data-stu-id="f0e29-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="f0e29-109">Pour réduire cette surcharge, WCF peut mettre en cache les fabriques de canaux lorsque vous utilisez un proxy du client WCF.</span><span class="sxs-lookup"><span data-stu-id="f0e29-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f0e29-110">Vous disposez d'un contrôle direct sur la création de fabrique de canaux lorsque vous utilisez la classe <xref:System.ServiceModel.ChannelFactory%601> directement.</span><span class="sxs-lookup"><span data-stu-id="f0e29-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="f0e29-111">Proxys clients WCF générés avec [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sont dérivés de <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="f0e29-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="f0e29-112"><xref:System.ServiceModel.ClientBase%601> définit une propriété <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> statique qui définit le comportement de mise en cache de la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="f0e29-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="f0e29-113">Les paramètres de cache sont faits pour un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0e29-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="f0e29-114">Par exemple, la définition `ClientBase<ITest>.CacheSettings` à une des valeurs définies ci-dessous affecte uniquement les proxy/ClientBase de type `ITest`.</span><span class="sxs-lookup"><span data-stu-id="f0e29-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="f0e29-115">Le paramètre de cache pour un <xref:System.ServiceModel.ClientBase%601> particulier est immuable dès que la première instance de proxy/ClientBase est créée.</span><span class="sxs-lookup"><span data-stu-id="f0e29-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="f0e29-116">Spécifier le comportement de mise en cache</span><span class="sxs-lookup"><span data-stu-id="f0e29-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="f0e29-117">Le comportement de mise en cache est spécifié en affectant à la propriété <xref:System.ServiceModel.ClientBase%601.CacheSetting> l'une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="f0e29-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="f0e29-118">Valeur de paramètre de cache</span><span class="sxs-lookup"><span data-stu-id="f0e29-118">Cache Setting Value</span></span>|<span data-ttu-id="f0e29-119">Description</span><span class="sxs-lookup"><span data-stu-id="f0e29-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="f0e29-120">Toutes les instances de <xref:System.ServiceModel.ClientBase%601> du domaine d'application peuvent participer à la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="f0e29-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="f0e29-121">Le développeur a déterminé qu'il n'y a aucune conséquence défavorable à la mise en cache sur la sécurité.</span><span class="sxs-lookup"><span data-stu-id="f0e29-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="f0e29-122">La mise en cache ne sera pas désactivée même si la sécurité « sensibles » les propriétés <xref:System.ServiceModel.ClientBase%601> sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="f0e29-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="f0e29-123">Les propriétés de sécurité « sensibles » de <xref:System.ServiceModel.ClientBase%601> sont <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> et <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0e29-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="f0e29-124">Seules les instances de <xref:System.ServiceModel.ClientBase%601> créées à partir des points de terminaison définis dans les fichiers de configuration participent à la mise en cache dans le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="f0e29-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="f0e29-125">Les instances de <xref:System.ServiceModel.ClientBase%601> créées par programme dans ce domaine d'application ne participent pas à la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="f0e29-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="f0e29-126">En outre, la mise en cache sera désactivée pour une instance de <xref:System.ServiceModel.ClientBase%601> une fois qu’une de ses propriétés de sécurité « sensibles » est accessible.</span><span class="sxs-lookup"><span data-stu-id="f0e29-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="f0e29-127">La mise en cache est désactivée pour toutes les instances de <xref:System.ServiceModel.ClientBase%601> d'un type spécifique dans le domaine d'application concerné.</span><span class="sxs-lookup"><span data-stu-id="f0e29-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="f0e29-128">Les extraits de code suivants montrent comment utiliser la propriété <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0e29-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="f0e29-129">Dans le code ci-dessus, toutes les instances de `TestClient` utilisent la même fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="f0e29-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="f0e29-130">Dans l'exemple ci-dessus, toutes les instances de `TestClient` utilisent la même fabrique de canaux, à l'exception de l'instance #4.</span><span class="sxs-lookup"><span data-stu-id="f0e29-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="f0e29-131">L'instance #4 utiliserait une fabrique de canaux créée spécifiquement pour son utilisation.</span><span class="sxs-lookup"><span data-stu-id="f0e29-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="f0e29-132">Ce paramètre doit s'exécuter pour les scénarios où un point de terminaison spécifique exige des paramètres de sécurité différents de ceux des autres points de terminaison du même type de fabrique de canaux (dans ce cas `ITest`).</span><span class="sxs-lookup"><span data-stu-id="f0e29-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="f0e29-133">Dans l'exemple ci-dessus, toutes les instances de `TestClient` utilisent différentes fabriques de canaux.</span><span class="sxs-lookup"><span data-stu-id="f0e29-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="f0e29-134">Cela est utile lorsque tous les points de terminaison ont différentes exigences de sécurité et la mise en cache n’est pas justifiée.</span><span class="sxs-lookup"><span data-stu-id="f0e29-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e29-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e29-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="f0e29-136">Génération de clients</span><span class="sxs-lookup"><span data-stu-id="f0e29-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="f0e29-137">Clients</span><span class="sxs-lookup"><span data-stu-id="f0e29-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="f0e29-138">Accès aux services à l’aide d’un client WCF</span><span class="sxs-lookup"><span data-stu-id="f0e29-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="f0e29-139">Guide pratique pour Utiliser la classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="f0e29-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
