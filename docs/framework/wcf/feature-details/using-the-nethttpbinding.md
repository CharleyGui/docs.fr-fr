---
title: Utilisation de NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 85a81c353e779800a9aa371658f2f799365b759d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282026"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="db8da-102">Utilisation de NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="db8da-102">Using the NetHttpBinding</span></span>

<span data-ttu-id="db8da-103"><xref:System.ServiceModel.NetHttpBinding> est une liaison conçue pour consommer des services HTTP ou WebSocket et utilise l'encodage binaire par défaut.</span><span class="sxs-lookup"><span data-stu-id="db8da-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="db8da-104"><xref:System.ServiceModel.NetHttpBinding> détecte si elle est utilisée avec un contrat demande-réponse ou un contrat duplex et modifie son comportement pour le faire correspondre - elle utilise HTTP pour les contrats de demande-réponse et WebSockets pour les contrats duplex.</span><span class="sxs-lookup"><span data-stu-id="db8da-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="db8da-105">Vous pouvez substituer ce comportement au moyen du paramètre <xref:System.ServiceModel.Channels.WebSocketTransportUsage> :</span><span class="sxs-lookup"><span data-stu-id="db8da-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="db8da-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> : Force l’utilisation de WebSockets même pour les contrats demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="db8da-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="db8da-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> : Empêche l’utilisation de WebSocket.</span><span class="sxs-lookup"><span data-stu-id="db8da-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="db8da-108">Toute tentative d'utiliser un contrat duplex avec ce paramètre entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="db8da-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="db8da-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -Il s’agit de la valeur par défaut et se comporte comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="db8da-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="db8da-110"><xref:System.ServiceModel.NetHttpBinding> prend en charge les sessions fiables en mode HTTP et en mode WebSocket.</span><span class="sxs-lookup"><span data-stu-id="db8da-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="db8da-111">Les sessions en mode WebSocket sont fournies par le transport.</span><span class="sxs-lookup"><span data-stu-id="db8da-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="db8da-112">Si vous utilisez <xref:System.ServiceModel.NetHttpBinding> et le TransferMode de la liaison a la valeur TransferMode.Streamed, les grands flux peuvent provoquer un interblocage et le dépassement du délai d'attente de l'appel.</span><span class="sxs-lookup"><span data-stu-id="db8da-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="db8da-113">Pour contourner ce problème, envoyez de plus petits messages ou utilisez TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="db8da-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="db8da-114">Configuration d'un service de façon à utiliser NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="db8da-114">Configuring a Service to use NetHttpBinding</span></span>  

 <span data-ttu-id="db8da-115"><xref:System.ServiceModel.NetHttpBinding> peut être configuré de la même façon que toute autre liaison.</span><span class="sxs-lookup"><span data-stu-id="db8da-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="db8da-116">L'extrait de code suivant de configuration montre comment configurer un service WCF avec <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="db8da-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="db8da-117">L'extrait de code suivant montre comment ajouter <xref:System.ServiceModel.NetHttpBinding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="db8da-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="db8da-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db8da-118">See also</span></span>

- [<span data-ttu-id="db8da-119">Configuration de liaisons pour les services</span><span class="sxs-lookup"><span data-stu-id="db8da-119">Configuring Bindings for Services</span></span>](../configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="db8da-120">Liaisons</span><span class="sxs-lookup"><span data-stu-id="db8da-120">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="db8da-121">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="db8da-121">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="db8da-122">Services duplex</span><span class="sxs-lookup"><span data-stu-id="db8da-122">Duplex Services</span></span>](duplex-services.md)
