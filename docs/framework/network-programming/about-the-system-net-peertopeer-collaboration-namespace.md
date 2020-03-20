---
title: À propos de l’espace de noms System.Net.PeerToPeer.Collaboration
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: f0c9ecaacc1d875aac8eed61a85ca7579f5cb8a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64649523"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>À propos de l’espace de noms System.Net.PeerToPeer.Collaboration
L’espace de noms <xref:System.Net.PeerToPeer.Collaboration> fournit des classes et des API qui sont utilisées pour implémenter les activités de collaboration pair à l’aide de l’infrastructure de collaboration pair à pair.  
  
## <a name="classes"></a>Classes  
 Les principales classes utilisées dans l’implémentation d’une activité de collaboration pair à pair sont les suivantes :  
  
- La classe <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, qui peut être utilisée pour stocker les contacts du pair.  
  
- La classe <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> dans laquelle collaborer, telle qu’un jeu, un client chat ou une solution de conférence.  
  
- Les pairs qui vont collaborer à une activité.  Ces pairs peuvent être représentés comme des objets <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> ou <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint>.  
  
- La classe statique <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>, qui spécifie les applications qui sont disponibles et les pairs qui y participent.  
  
 Les méthodes <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> sont utilisées pour inviter les pairs à une session de collaboration.  Un pair appelant peut s’abonner aux événements d’un autre pair signalant la mise à jour des données d’application, d’objet ou de présence associées à la session de collaboration. Les classes de présence spécifient si un <xref:System.Net.PeerToPeer.Collaboration.Peer> est disponible pour la collaboration, et la classe <xref:System.Net.PeerToPeer.Collaboration.PeerScope> est utilisée pour spécifier le degré de participation autorisé pour un pair : <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> (sous-réseau) ou <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 Une session de collaboration se compose de quatre étapes :  
  
- La détection. Détectez ou publiez des informations relatives aux applications, aux pairs et à la présence.  Par exemple, trouvez d’autres personnes sur le sous-réseau local qui ont installé les mêmes jeux que vous.  
  
- L’invitation. Envoyez des invitations sécurisées aux pairs distants ou acceptez leurs invitations pour démarrer ou rejoindre des sessions <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>.  
  
- La gestion des contacts. Ajoutez les pairs détectés en tant que contacts à un <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
- La communication. Lorsque la communication est établie, utilisez les API <xref:System.Net>, l’API <xref:System.Net.PeerToPeer> ou les classes de canal pair WCF pour les communications entre plusieurs parties.  
  
 Par exemple, le pair hôte démarre une session de collaboration et utilise la méthode <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> pour ajouter un pair distant et l’un de ses pairs locaux au gestionnaire de contacts du pair hôte.  Les trois utilisateurs participeront alors à leur propre session collaboration privée.  
  
 Voici quelques exemples d’applications P2P typiques : téléconférences pour prise de notes collaborative, applications de conversation sans serveur, publicités interactives, sessions de jeux en ligne.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.PeerToPeer.Collaboration>
