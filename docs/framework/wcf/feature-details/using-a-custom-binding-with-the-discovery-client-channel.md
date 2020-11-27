---
title: Utilisation d’une liaison personnalisée avec le canal client de découverte
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: d84739a0021262826c541ab3ff9df663adabf44a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289657"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="18f92-102">Utilisation d’une liaison personnalisée avec le canal client de découverte</span><span class="sxs-lookup"><span data-stu-id="18f92-102">Using a Custom Binding with the Discovery Client Channel</span></span>

<span data-ttu-id="18f92-103">Lorsque vous utilisez une liaison personnalisée avec l’élément <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, vous devez définir un objet <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> qui crée des instances <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="18f92-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="18f92-104">Création d'un DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="18f92-104">Creating a DiscoveryEndpointProvider</span></span>  

 <span data-ttu-id="18f92-105">La <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> est chargée de créer <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> des instances à la demande.</span><span class="sxs-lookup"><span data-stu-id="18f92-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="18f92-106">Pour définir un fournisseur de points de terminaison de découverte, dérivez une classe à partir de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, substituez la méthode <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> et retournez un nouveau point de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="18f92-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="18f92-107">L'exemple suivant indique comment créer un fournisseur de points de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="18f92-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 <span data-ttu-id="18f92-108">Une fois que vous avez défini le fournisseur de points de terminaison de découverte, vous pouvez créer une liaison personnalisée et ajouter l'objet <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, qui référence le fournisseur de points de terminaison de découverte, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="18f92-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 <span data-ttu-id="18f92-109">Pour plus d’informations sur l’utilisation du canal client de découverte, consultez [utilisation du canal client de découverte](using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="18f92-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="18f92-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18f92-110">See also</span></span>

- [<span data-ttu-id="18f92-111">Vue d'ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="18f92-111">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="18f92-112">Utilisation du canal client de découverte</span><span class="sxs-lookup"><span data-stu-id="18f92-112">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
