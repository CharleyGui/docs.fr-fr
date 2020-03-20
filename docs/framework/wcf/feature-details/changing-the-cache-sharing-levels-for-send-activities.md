---
title: Modification des niveaux de partage du cache pour les activités d'envoi
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185395"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="aee50-102">Modification des niveaux de partage du cache pour les activités d'envoi</span><span class="sxs-lookup"><span data-stu-id="aee50-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="aee50-103">L’extension <xref:System.ServiceModel.Activities.SendMessageChannelCache> vous permet de personnaliser les niveaux de partage du cache, les paramètres du cache de fabrication de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d’activités de messagerie <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="aee50-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="aee50-104">Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="aee50-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="aee50-105">Le cache de fabrication de canaux contient des objets <xref:System.ServiceModel.ChannelFactory%601> mis en cache.</span><span class="sxs-lookup"><span data-stu-id="aee50-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="aee50-106">Le cache de canaux contient des canaux mis en cache.</span><span class="sxs-lookup"><span data-stu-id="aee50-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aee50-107">Pour envoyer des messages ou des paramètres, les flux de travail peuvent utiliser des activités de messagerie <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="aee50-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="aee50-108">Le runtime du workflow ajoute au cache des fabriques de canaux qui créent des canaux du type <xref:System.ServiceModel.Channels.IRequestChannel> si vous utilisez une activité <xref:System.ServiceModel.Activities.ReceiveReply> avec une activité <xref:System.ServiceModel.Activities.Send>, et un objet <xref:System.ServiceModel.Channels.IOutputChannel> si vous utilisez simplement une activité <xref:System.ServiceModel.Activities.Send> (sans <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="aee50-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="aee50-109">Niveaux de partage du cache</span><span class="sxs-lookup"><span data-stu-id="aee50-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="aee50-110">Par défaut, dans un workflow hébergé par un objet <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de workflow dans l'objet <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="aee50-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="aee50-111">Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance).</span><span class="sxs-lookup"><span data-stu-id="aee50-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="aee50-112">Le cache est uniquement disponible pour les activités <xref:System.ServiceModel.Activities.Send> qui n'utilisent pas les points de terminaison définis dans la configuration, sauf en cas d'activation de la mise en cache non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="aee50-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="aee50-113">Voici les différents niveaux de partage du cache disponibles pour les activités <xref:System.ServiceModel.Activities.Send> dans un flux de travail et leur utilisation recommandée :</span><span class="sxs-lookup"><span data-stu-id="aee50-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="aee50-114">**Niveau hôte**: Au niveau de partage de l’hôte, le cache n’est disponible que pour les instances de flux de travail hébergées dans l’hôte du service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="aee50-115">Un cache peut également être partagé entre des hôtes du service de workflow dans un cache au niveau du processus.</span><span class="sxs-lookup"><span data-stu-id="aee50-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="aee50-116">**Niveau d’instance**: Dans le niveau de partage par exemple, le cache est disponible pour une instance particulière de flux de travail tout au long de sa vie, mais le cache n’est pas disponible pour d’autres instances de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="aee50-117">**Pas de cache**: Le cache est désactivé par défaut si vous avez un flux de travail qui utilise des paramètres définis dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="aee50-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="aee50-118">Dans ce cas, il est également recommandé de garder le cache désactivé, car son activation peut être non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="aee50-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="aee50-119">Citons, par exemple, le cas où une identité différente (informations d'identification différentes ou utilisation de l'emprunt d'identité) serait requise pour chaque envoi.</span><span class="sxs-lookup"><span data-stu-id="aee50-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="aee50-120">Modification du niveau de partage du cache pour un workflow client</span><span class="sxs-lookup"><span data-stu-id="aee50-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="aee50-121">Pour définir le partage du cache dans un workflow client, ajoutez une instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>, en tant qu’extension, à l’ensemble souhaité d’instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="aee50-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="aee50-122">Le cache est ainsi partagé entre toutes les instances de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="aee50-123">Les exemples de code suivants illustrent les étapes décrites ci-après.</span><span class="sxs-lookup"><span data-stu-id="aee50-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="aee50-124">D'abord, déclarez une instance du type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="aee50-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="aee50-125">Ensuite, ajoutez l’extension de cache à chaque instance de flux de travail client.</span><span class="sxs-lookup"><span data-stu-id="aee50-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="aee50-126">Modification du niveau de partage du cache pour un service de flux de travail hébergé</span><span class="sxs-lookup"><span data-stu-id="aee50-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="aee50-127">Pour définir le partage du cache dans un service de flux de travail hébergé, ajoutez une instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>, en tant qu'extension, à tous les hôtes du service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="aee50-128">Le cache est ainsi partagé entre tous les hôtes du service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="aee50-129">Les exemples de code suivants illustrent les étapes décrites ci-après.</span><span class="sxs-lookup"><span data-stu-id="aee50-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="aee50-130">D'abord, déclarez une instance du type <xref:System.ServiceModel.Activities.SendMessageChannelCache> au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="aee50-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="aee50-131">Ensuite, ajoutez l’extension de cache statique à chaque hôte du service de workflow.</span><span class="sxs-lookup"><span data-stu-id="aee50-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="aee50-132">Pour définir le partage du cache sur le niveau de l’instance dans un service de workflow hébergé, ajoutez un délégué `Func<SendMessageChannelCache>` en tant qu’extension à l’hôte du service de workflow et affectez ce délégué au code qui instancie une nouvelle instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="aee50-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="aee50-133">Cela permet d'obtenir un cache différent par instance de workflow, au lieu d'un cache unique partagé par toutes les instances de workflow, dans l'hôte du service de workflow.</span><span class="sxs-lookup"><span data-stu-id="aee50-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="aee50-134">L'exemple de code suivant indique comment parvenir à ce résultat, à l'aide d'une expression lambda permettant de définir directement l'extension <xref:System.ServiceModel.Activities.SendMessageChannelCache> vers laquelle le délégué pointe.</span><span class="sxs-lookup"><span data-stu-id="aee50-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="aee50-135">Personnalisation des paramètres de cache</span><span class="sxs-lookup"><span data-stu-id="aee50-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="aee50-136">Vous pouvez personnaliser les paramètres du cache de fabrication de canaux et du cache de canaux.</span><span class="sxs-lookup"><span data-stu-id="aee50-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="aee50-137">Les paramètres de cache sont définis dans la classe <xref:System.ServiceModel.Activities.ChannelCacheSettings>.</span><span class="sxs-lookup"><span data-stu-id="aee50-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="aee50-138">La <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe définit les paramètres de cache par défaut pour le cache de l’usine de canal et le cache du canal dans son constructeur sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="aee50-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="aee50-139">Le tableau suivant répertorie les valeurs par défaut de ces paramètres de cache, par type de cache.</span><span class="sxs-lookup"><span data-stu-id="aee50-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="aee50-140">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aee50-140">Settings</span></span>|<span data-ttu-id="aee50-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="aee50-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="aee50-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="aee50-142">IdleTimeout (min)</span></span>|<span data-ttu-id="aee50-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="aee50-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="aee50-144">Valeur par défaut du cache de fabrication</span><span class="sxs-lookup"><span data-stu-id="aee50-144">Factory Cache Default</span></span>|<span data-ttu-id="aee50-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="aee50-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="aee50-146">2</span><span class="sxs-lookup"><span data-stu-id="aee50-146">2</span></span>|<span data-ttu-id="aee50-147">16</span><span class="sxs-lookup"><span data-stu-id="aee50-147">16</span></span>|  
|<span data-ttu-id="aee50-148">Valeur par défaut du cache de canaux</span><span class="sxs-lookup"><span data-stu-id="aee50-148">Channel Cache Default</span></span>|<span data-ttu-id="aee50-149">5</span><span class="sxs-lookup"><span data-stu-id="aee50-149">5</span></span>|<span data-ttu-id="aee50-150">2</span><span class="sxs-lookup"><span data-stu-id="aee50-150">2</span></span>|<span data-ttu-id="aee50-151">16</span><span class="sxs-lookup"><span data-stu-id="aee50-151">16</span></span>|  
  
 <span data-ttu-id="aee50-152">Pour personnaliser les paramètres des caches de fabrication et de canaux, instanciez la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache> à l'aide du constructeur paramétré <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> et passez une nouvelle instance de l'objet <xref:System.ServiceModel.Activities.ChannelCacheSettings> avec les valeurs personnalisées à chacun des paramètres `factorySettings` et `channelSettings`.</span><span class="sxs-lookup"><span data-stu-id="aee50-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="aee50-153">Ensuite, ajoutez la nouvelle instance de cette classe en tant qu'extension à un hôte du service de flux de travail ou à une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="aee50-154">L'exemple de code suivant indique comment effectuer ces étapes pour une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="aee50-155">Pour activer la mise en cache lorsque votre service de flux de travail a des points de terminaison définis dans la configuration, instanciez la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache> à l'aide du constructeur paramétré <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> avec le paramètre `allowUnsafeCaching` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="aee50-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="aee50-156">Ensuite, ajoutez la nouvelle instance de cette classe en tant qu'extension à un hôte du service de flux de travail ou à une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="aee50-157">L'exemple de code suivant indique la procédure d'activation de la mise en cache pour une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="aee50-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="aee50-158">Pour désactiver complètement le cache pour les fabriques de canaux et les canaux, désactivez le cache de fabrication de canaux.</span><span class="sxs-lookup"><span data-stu-id="aee50-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="aee50-159">Cette action désactive également le cache de canaux, car ces derniers appartiennent à leur fabrique de canaux respective.</span><span class="sxs-lookup"><span data-stu-id="aee50-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="aee50-160">Pour désactiver le cache de fabrication de canaux, passez le paramètre `factorySettings` au constructeur <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> initialisé avec une instance <xref:System.ServiceModel.Activities.ChannelCacheSettings> ayant 0 comme valeur <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A>.</span><span class="sxs-lookup"><span data-stu-id="aee50-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="aee50-161">L'exemple de code suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="aee50-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="aee50-162">Vous pouvez choisir d'utiliser uniquement le cache de fabrication de canaux et de désactiver le cache de canaux en transmettant le paramètre `channelSettings` au constructeur <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> initialisé avec une instance <xref:System.ServiceModel.Activities.ChannelCacheSettings> ayant 0 comme valeur <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A>.</span><span class="sxs-lookup"><span data-stu-id="aee50-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="aee50-163">L'exemple de code suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="aee50-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="aee50-164">Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="aee50-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="aee50-165">Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service.</span><span class="sxs-lookup"><span data-stu-id="aee50-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="aee50-166">L’exemple suivant montre le contenu d’un fichier de configuration qui contient le comportement de `MyChannelCacheBehavior` service avec le cache d’usine personnalisé et les paramètres de cache de canal.</span><span class="sxs-lookup"><span data-stu-id="aee50-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="aee50-167">Ce comportement de service est `behaviorConfiguration` ajouté au service grâce à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="aee50-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
