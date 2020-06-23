---
title: Configuration des comportements clients
description: 'Découvrez les deux façons dont WCF configure les comportements : dans le fichier de configuration de l’application ou par programmation à partir de l’application appelante.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245438"
---
# <a name="configuring-client-behaviors"></a>Configuration des comportements clients
Windows Communication Foundation (WCF) configure les comportements de deux manières : soit en faisant référence aux configurations de comportement, qui sont définies dans la `<behavior>` section d’un fichier de configuration d’application cliente, soit par programme dans l’application appelante. Cette rubrique décrit ces deux approches.  
  
 Lors de l’utilisation d’un fichier de configuration, la configuration du comportement est une collection nommée de paramètres de configuration. Le nom de chaque configuration de comportement doit être unique. Cette chaîne est utilisée dans l'attribut `behaviorConfiguration` d'une configuration de point de terminaison pour lier le point de terminaison au comportement.  
  
## <a name="example"></a>Exemple  
 Le code de configuration suivant définit un comportement appelé `myBehavior`. Le point de terminaison de client référence ce comportement dans l'attribut `behaviorConfiguration`.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Utilisation de comportements par programme  
 Vous pouvez également configurer ou insérer des comportements par programme en localisant la `Behaviors` propriété appropriée sur l’objet client Windows Communication Foundation (WCF) ou sur l’objet de fabrique de canaux client avant d’ouvrir le client.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant indique comment insérer par programme un comportement en accédant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> sur <xref:System.ServiceModel.Description.ServiceEndpoint> retournée à partir de la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> avant la création de l'objet de canal.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
