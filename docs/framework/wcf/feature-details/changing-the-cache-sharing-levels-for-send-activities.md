---
title: Modification des niveaux de partage du cache pour les activités d'envoi
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: cbb937ac47c93307db922b28e3df0ea694a77960
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262046"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Modification des niveaux de partage du cache pour les activités d'envoi

L’extension <xref:System.ServiceModel.Activities.SendMessageChannelCache> vous permet de personnaliser les niveaux de partage du cache, les paramètres du cache de fabrication de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d’activités de messagerie <xref:System.ServiceModel.Activities.Send>. Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>. Le cache de fabrication de canaux contient des objets <xref:System.ServiceModel.ChannelFactory%601> mis en cache. Le cache de canaux contient des canaux mis en cache.  
  
> [!NOTE]
> Pour envoyer des messages ou des paramètres, les flux de travail peuvent utiliser des activités de messagerie <xref:System.ServiceModel.Activities.Send>. Le runtime du workflow ajoute au cache des fabriques de canaux qui créent des canaux du type <xref:System.ServiceModel.Channels.IRequestChannel> si vous utilisez une activité <xref:System.ServiceModel.Activities.ReceiveReply> avec une activité <xref:System.ServiceModel.Activities.Send>, et un objet <xref:System.ServiceModel.Channels.IOutputChannel> si vous utilisez simplement une activité <xref:System.ServiceModel.Activities.Send> (sans <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Niveaux de partage du cache  

 Par défaut, dans un workflow hébergé par un objet <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de workflow dans l'objet <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte). Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance). Le cache est uniquement disponible pour les activités <xref:System.ServiceModel.Activities.Send> qui n'utilisent pas les points de terminaison définis dans la configuration, sauf en cas d'activation de la mise en cache non sécurisée.  
  
 Voici les différents niveaux de partage du cache disponibles pour les activités <xref:System.ServiceModel.Activities.Send> dans un flux de travail et leur utilisation recommandée :  
  
- **Niveau** de l’hôte : dans le niveau de partage de l’hôte, le cache est disponible uniquement pour les instances de workflow hébergées dans l’hôte du service de Workflow. Un cache peut également être partagé entre des hôtes du service de workflow dans un cache au niveau du processus.  
  
- **Niveau** de l’instance : dans le niveau de partage de l’instance, le cache est disponible pour une instance de workflow particulière tout au long de sa durée de vie, mais le cache n’est pas disponible pour les autres instances de Workflow.  
  
- **Aucun cache**: le cache est désactivé par défaut si vous avez un flux de travail qui utilise des points de terminaison définis dans la configuration. Dans ce cas, il est également recommandé de garder le cache désactivé, car son activation peut être non sécurisée. Citons, par exemple, le cas où une identité différente (informations d'identification différentes ou utilisation de l'emprunt d'identité) serait requise pour chaque envoi.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Modification du niveau de partage du cache pour un workflow client  

 Pour définir le partage du cache dans un workflow client, ajoutez une instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>, en tant qu’extension, à l’ensemble souhaité d’instances de workflow. Le cache est ainsi partagé entre toutes les instances de flux de travail. Les exemples de code suivants illustrent les étapes décrites ci-après.  
  
 D'abord, déclarez une instance du type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Ensuite, ajoutez l’extension de cache à chaque instance de flux de travail client.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Modification du niveau de partage du cache pour un service de flux de travail hébergé  

 Pour définir le partage du cache dans un service de flux de travail hébergé, ajoutez une instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>, en tant qu'extension, à tous les hôtes du service de flux de travail. Le cache est ainsi partagé entre tous les hôtes du service de flux de travail. Les exemples de code suivants illustrent les étapes décrites ci-après.  
  
 D'abord, déclarez une instance du type <xref:System.ServiceModel.Activities.SendMessageChannelCache> au niveau de la classe.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Ensuite, ajoutez l’extension de cache statique à chaque hôte du service de workflow.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Pour définir le partage du cache sur le niveau de l’instance dans un service de workflow hébergé, ajoutez un délégué `Func<SendMessageChannelCache>` en tant qu’extension à l’hôte du service de workflow et affectez ce délégué au code qui instancie une nouvelle instance de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache>. Cela permet d'obtenir un cache différent par instance de workflow, au lieu d'un cache unique partagé par toutes les instances de workflow, dans l'hôte du service de workflow. L'exemple de code suivant indique comment parvenir à ce résultat, à l'aide d'une expression lambda permettant de définir directement l'extension <xref:System.ServiceModel.Activities.SendMessageChannelCache> vers laquelle le délégué pointe.  
  
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
  
## <a name="customizing-cache-settings"></a>Personnalisation des paramètres de cache  

 Vous pouvez personnaliser les paramètres du cache de fabrication de canaux et du cache de canaux. Les paramètres de cache sont définis dans la classe <xref:System.ServiceModel.Activities.ChannelCacheSettings>. La <xref:System.ServiceModel.Activities.SendMessageChannelCache> classe définit les paramètres de cache par défaut pour le cache de la fabrique de canaux et le cache de canaux dans son constructeur sans paramètre. Le tableau suivant répertorie les valeurs par défaut de ces paramètres de cache, par type de cache.  
  
|Paramètres|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Valeur par défaut du cache de fabrication|TimeSpan.MaxValue|2|16|  
|Valeur par défaut du cache de canaux|5|2|16|  
  
 Pour personnaliser les paramètres des caches de fabrication et de canaux, instanciez la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache> à l'aide du constructeur paramétré <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> et passez une nouvelle instance de l'objet <xref:System.ServiceModel.Activities.ChannelCacheSettings> avec les valeurs personnalisées à chacun des paramètres `factorySettings` et `channelSettings`. Ensuite, ajoutez la nouvelle instance de cette classe en tant qu'extension à un hôte du service de flux de travail ou à une instance de flux de travail. L'exemple de code suivant indique comment effectuer ces étapes pour une instance de flux de travail.  
  
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
  
 Pour activer la mise en cache lorsque votre service de flux de travail a des points de terminaison définis dans la configuration, instanciez la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache> à l'aide du constructeur paramétré <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> avec le paramètre `allowUnsafeCaching` défini sur `true`. Ensuite, ajoutez la nouvelle instance de cette classe en tant qu'extension à un hôte du service de flux de travail ou à une instance de flux de travail. L'exemple de code suivant indique la procédure d'activation de la mise en cache pour une instance de flux de travail.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Pour désactiver complètement le cache pour les fabriques de canaux et les canaux, désactivez le cache de fabrication de canaux. Cette action désactive également le cache de canaux, car ces derniers appartiennent à leur fabrique de canaux respective. Pour désactiver le cache de fabrication de canaux, passez le paramètre `factorySettings` au constructeur <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> initialisé avec une instance <xref:System.ServiceModel.Activities.ChannelCacheSettings> ayant 0 comme valeur <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A>. L'exemple de code suivant illustre ce point.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Vous pouvez choisir d'utiliser uniquement le cache de fabrication de canaux et de désactiver le cache de canaux en transmettant le paramètre `channelSettings` au constructeur <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> initialisé avec une instance <xref:System.ServiceModel.Activities.ChannelCacheSettings> ayant 0 comme valeur <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A>. L'exemple de code suivant illustre ce point.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application. Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service. L’exemple suivant montre le contenu d’un fichier de configuration qui contient le `MyChannelCacheBehavior` comportement de service avec les paramètres du cache de fabrique personnalisé et du cache de canaux. Ce comportement de service est ajouté au service via l' `behaviorConfiguration` attribut.  
  
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
