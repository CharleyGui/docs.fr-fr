---
title: Configuration des comportements clients
description: 'Découvrez les deux façons dont WCF configure les comportements : dans le fichier de configuration de l’application ou par programmation à partir de l’application appelante.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 34cbb9e31933debb5120eb30956c3a5f0be065ed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266712"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="951e7-103">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="951e7-103">Configuring Client Behaviors</span></span>

<span data-ttu-id="951e7-104">Windows Communication Foundation (WCF) configure les comportements de deux manières : soit en faisant référence aux configurations de comportement, qui sont définies dans la `<behavior>` section d’un fichier de configuration d’application cliente, soit par programme dans l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="951e7-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="951e7-105">Cette rubrique décrit ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="951e7-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="951e7-106">Lors de l’utilisation d’un fichier de configuration, la configuration du comportement est une collection nommée de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="951e7-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="951e7-107">Le nom de chaque configuration de comportement doit être unique.</span><span class="sxs-lookup"><span data-stu-id="951e7-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="951e7-108">Cette chaîne est utilisée dans l'attribut `behaviorConfiguration` d'une configuration de point de terminaison pour lier le point de terminaison au comportement.</span><span class="sxs-lookup"><span data-stu-id="951e7-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="951e7-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="951e7-109">Example</span></span>  

 <span data-ttu-id="951e7-110">Le code de configuration suivant définit un comportement appelé `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="951e7-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="951e7-111">Le point de terminaison de client référence ce comportement dans l'attribut `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="951e7-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="951e7-112">Utilisation de comportements par programme</span><span class="sxs-lookup"><span data-stu-id="951e7-112">Using Behaviors Programmatically</span></span>  

 <span data-ttu-id="951e7-113">Vous pouvez également configurer ou insérer des comportements par programme en localisant la `Behaviors` propriété appropriée sur l’objet client Windows Communication Foundation (WCF) ou sur l’objet de fabrique de canaux client avant d’ouvrir le client.</span><span class="sxs-lookup"><span data-stu-id="951e7-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="951e7-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="951e7-114">Example</span></span>  

 <span data-ttu-id="951e7-115">L'exemple de code suivant indique comment insérer par programme un comportement en accédant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> sur <xref:System.ServiceModel.Description.ServiceEndpoint> retournée à partir de la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> avant la création de l'objet de canal.</span><span class="sxs-lookup"><span data-stu-id="951e7-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="951e7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="951e7-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
