---
title: Configuration des comportements clients
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: ca466af71f62ef72e021753b132afdc847f75d76
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320696"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="bf8a9-102">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="bf8a9-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="bf8a9-103">Windows Communication Foundation (WCF) configure les comportements de deux manières : soit en faisant référence aux configurations de comportement, qui sont définies dans la section `<behavior>` d’un fichier de configuration d’application cliente, soit par programme dans l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="bf8a9-104">Cette rubrique décrit ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="bf8a9-105">Lors de l’utilisation d’un fichier de configuration, la configuration du comportement est une collection nommée de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="bf8a9-106">Le nom de chaque configuration de comportement doit être unique.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="bf8a9-107">Cette chaîne est utilisée dans l'attribut `behaviorConfiguration` d'une configuration de point de terminaison pour lier le point de terminaison au comportement.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8a9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf8a9-108">Example</span></span>  
 <span data-ttu-id="bf8a9-109">Le code de configuration suivant définit un comportement appelé `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="bf8a9-110">Le point de terminaison de client référence ce comportement dans l'attribut `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="bf8a9-111">Utilisation de comportements par programme</span><span class="sxs-lookup"><span data-stu-id="bf8a9-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="bf8a9-112">Vous pouvez également configurer ou insérer des comportements par programme en localisant la propriété `Behaviors` appropriée sur l’objet client Windows Communication Foundation (WCF) ou sur l’objet de fabrique de canaux client avant d’ouvrir le client.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8a9-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf8a9-113">Example</span></span>  
 <span data-ttu-id="bf8a9-114">L'exemple de code suivant indique comment insérer par programme un comportement en accédant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> sur <xref:System.ServiceModel.Description.ServiceEndpoint> retournée à partir de la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> avant la création de l'objet de canal.</span><span class="sxs-lookup"><span data-stu-id="bf8a9-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="bf8a9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf8a9-115">See also</span></span>

- [<span data-ttu-id="bf8a9-116">@no__t 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="bf8a9-116">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
