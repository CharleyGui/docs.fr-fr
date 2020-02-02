---
title: Programmes de résolution d'homologue
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 3bcdeffac3673c1c464a35d8b6e089efd7394907
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919240"
---
# <a name="peer-resolvers"></a>Programmes de résolution d'homologue
Pour se connecter à une maille, un nœud d'homologue requiert les adresses IP d'autres nœuds. Les adresses IP sont obtenues en contactant un service de résolution, qui prend l'ID de la maille et retourne une liste d'adresses correspondant aux nœuds enregistrés sous cet ID de maille particulier. Le programme de résolution conserve une liste des adresses inscrites, qu'il crée en inscrivant chaque nœud de la maille avec le service.  
  
 Vous pouvez spécifier le service PeerResolver à utiliser par le biais de la propriété `Resolver` du <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Programmes de résolution de pair pris en charge  
 Le canal homologue prend en charge deux types de programmes de résolution : le protocole PNRP (Peer Name Resolution Protocol) et les services de résolution personnalisés.  
  
 Par défaut, le canal homologue utilise le service de résolution de pair PNRP pour la découverte d'homologues et de voisins dans la maille. Pour les situations/plateformes où PNRP n’est pas disponible ou faisable, Windows Communication Foundation (WCF) fournit un autre service de découverte basé sur le serveur, le <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Vous pouvez également définir explicitement un service de résolution personnalisé en écrivant une classe qui implémente l'interface <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract>.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protocole PNRP (Peer Name Resolution Protocol)  
 PNRP, le programme de résolution par défaut de Windows Vista, est un service de résolution de noms distribué sans serveur. Vous pouvez également utiliser PNRP sur Windows XP SP2 en installant le Pack Advanced Networking. Deux clients qui exécutent la même version de PNRP peuvent se localiser mutuellement à l'aide de ce protocole, à condition qu'ils remplissent certaines conditions (telles que l'absence d'un pare-feu d'entreprise intermédiaire). Notez que la version de PNRP fournie avec Windows Vista est plus récente que la version incluse dans le Pack Advanced Networking. Consultez le centre de téléchargement Microsoft pour obtenir les mises à jour de PNRP pour Windows XP SP2.  
  
### <a name="custom-resolver-services"></a>Services de résolution personnalisés  
 Lorsque le service PNRP n'est pas disponible ou que vous souhaitez contrôler entièrement la maille, vous pouvez utiliser un service de résolution serveur personnalisé. Vous pouvez définir explicitement ce service en écrivant une classe de programme de résolution qui implémente l'interface <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract>, ou en utilisant l'implémentation par défaut fournie, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 Sous l'implémentation par défaut du service, les inscriptions des clients expirent au bout d'un certain délai si les clients n'actualisent pas leur inscription explicitement. Les clients qui utilisent le service de résolution doivent connaître la limite supérieure de la latence client-serveur pour pourvoir actualiser les inscriptions en temps opportun. Cela implique de choisir un délai d'actualisation approprié (`RefreshInterval`) sur le service de résolution. (Pour plus d’informations, consultez [à l’intérieur du CustomPeerResolverService : inscriptions des clients](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Le writer d'applications doit également envisager de sécuriser la connexion entre les clients et le service de résolution personnalisé. Pour cela, vous pouvez spécifier les paramètres de sécurité sur <xref:System.ServiceModel.NetTcpBinding> que les clients utilisent pour contacter le service de résolution. Vous devez spécifier des informations d'identification (le cas échéant) sur la `ChannelFactory` qui permet de créer le canal homologue. Ces informations d'identification sont passées à la `ChannelFactory` qui permet de créer des canaux dans le programme de résolution personnalisé.  
  
> [!NOTE]
> Lors de l'utilisation de réseaux locaux et impromptus avec un programme de résolution personnalisé, il est fortement recommandé que les applications utilisant ou prenant en charge des réseaux de liaison locale ou impromptus incluent une logique qui sélectionne une adresse de liaison locale unique à utiliser lors de la connexion. Cela empêche tout risque de confusion provoquée par des ordinateurs dotés de plusieurs adresses de liaison locale. Ainsi, le canal homologue ne peut utiliser qu'une seule adresse de liaison locale à la fois. Vous pouvez spécifier cette adresse à l'aide de la propriété `ListenIpAddress` sur <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Pour une démonstration de l’implémentation d’un programme de résolution personnalisé, consultez canal homologue programme de [résolution d’homologue personnalisé](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Dans CustomPeerResolverService : inscriptions des clients](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Voir aussi

- [Concepts de canal homologue](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Sécurité de canal homologue](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Création d’une application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
