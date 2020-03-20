---
title: 'Comment : configurer un service Windows Communication Foundation pour utiliser le partage de ports'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: cd8d76137ac195e452a7d66fb6ddbeda405a922f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185097"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Comment : configurer un service Windows Communication Foundation pour utiliser le partage de ports
La façon la plus simple d’utiliser net.tcp:// partage de port dans votre <xref:System.ServiceModel.NetTcpBinding>application Windows Communication Foundation (WCF) est d’exposer un service en utilisant le .  
  
 Cette liaison fournit une propriété <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> qui contrôle si le partage de ports net.tcp:// est activé pour le service configuré avec cette liaison.  
  
 La procédure suivante montre comment utiliser la classe <xref:System.ServiceModel.NetTcpBinding> pour ouvrir un point de terminaison à l'URI net.tcp://localhost/MyService, d'abord dans du code puis en utilisant des éléments de configuration.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Pour activer le partage de ports net.tcp:// sur une liaison NetTcpBinding dans du code  
  
1. Créer un service pour `IMyService` mettre en `MyService`œuvre un contrat appelé et l’appeler , .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Créez une instance de la classe <xref:System.ServiceModel.NetTcpBinding>, puis affectez à la propriété <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> la valeur `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Créez un <xref:System.ServiceModel.ServiceHost> et ajoutez-lui le point de terminaison de service pour `MyService` qui utilise la liaison <xref:System.ServiceModel.NetTcpBinding> avec partage de ports activé par partage et qui écoute l'URI de l'adresse du point de terminaison « net.tcp://localhost/MyService ».  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Cet exemple utilise le port TCP par défaut 808 parce que l'URI de l'adresse du point de terminaison ne spécifie pas de numéro de port différent. Vu que le partage de ports est activé explicitement sur la liaison de transport, ce service peut partager le port 808 avec d’autres services dans d’autres processus. Si le partage de ports n'a pas été autorisé et si une autre application utilise déjà le port 808, ce service lève une <xref:System.ServiceModel.AddressAlreadyInUseException> lorsqu'il est ouvert.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Pour activer le partage de ports net.tcp:// sur une liaison NetTcpBinding dans la configuration  
  
1. L'exemple suivant montre comment activer le partage de ports et ajouter le point de terminaison de service à l'aide d'éléments de configuration.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Comment : activer le service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
