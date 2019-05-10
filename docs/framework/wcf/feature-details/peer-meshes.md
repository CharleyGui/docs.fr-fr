---
title: Mailles d'homologues
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: 9113fab13da8503e6ce0335e5bb19a2634973dad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654499"
---
# <a name="peer-meshes"></a>Mailles d'homologues
Un *mesh* est une collection nommée (un graphique interconnecté) de nœuds homologues qui peuvent communiquer entre eux et qui sont identifiés par un ID de maille unique. Chaque nœud est connecté à plusieurs autres nœuds. Dans un maillage bien connecté, il existe un chemin entre chaque paire de nœuds, avec relativement peu de sauts entre les nœuds aux extrémités les plus éloignées du maillage, et le maillage reste connecté y compris si quelques nœuds ou connexions sont abandonnés. Les nœuds actifs dans la maille publient leurs informations de point de terminaison avec un ID de maille correspondant afin que d'autres homologues puissent les trouver.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Caractéristiques d'un maillage créé à l'aide du canal homologue  
  
#### <a name="uniquely-identified"></a>Identifié de manière unique.  
  
- Un ID unique identifie chaque maillage. Le nom de la maille (ou ID de maille) a le même format qu'un nom d'hôte DNS (Domain Name System). Ainsi, cet ID de maille doit être unique pour le client prévu de l'application dans la portée du programme de résolution utilisé. Un nom commun, tel que « MembresMaFamille » ou « TablePokerKevin », peut facilement entrer en conflit avec d'autres noms d'utilisateurs et peut retourner par erreur des informations sur le point de terminaison d'homologue, susceptibles de compromettre la confidentialité ou d'augmenter le temps de latence à la connexion. Pour éviter ces problèmes, vous pouvez ajouter un ID unique comme postfix au surnom du maillage (par exemple « TablePokerKevin90210 »).  
  
#### <a name="message-flooding"></a>Saturation de messages  
  
- La maille permet la propagation des messages d'un ou plusieurs expéditeurs à tous les autre nœuds d'homologues de la même maille. Les messages de saturation transmis par les nœuds d'homologues utilisent des en-têtes spécifiés dans l'espace de noms à l'adresse `http://schemas.microsoft.com/net/2006/05/peer`  
  
#### <a name="optimized-connections"></a>Connexions optimisées  
  
- Un maillage du canal homologue s'ajuste automatiquement en fonction des nœuds qui sont ajoutés ou supprimés, ce qui garantit la fiabilité de la connectivité de tous les nœuds tout en limitant les risques de création de partitions (groupes de nœuds isolés les uns des autres). Les connexions dans la maille sont également optimisées de manière dynamique en fonction des modèles de trafic actuels afin de minimiser le temps de latence des messages entre expéditeur et destinataire.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Fonctionnalités réseau courantes que le canal homologue ne fournit pas  
 Il est important de connaître les fonctionnalités réseau courantes que le canal homologue ne fournit pas. Ces fonctionnalités, qui peuvent toutes êtres créées au-dessus du canal homologue, sont les suivantes :  
  
- **Classement des messages :** Les messages provenant d’une source unique peut ne pas arrivent dans tous les autres parties dans le même ordre ou dans l’ordre dans lequel la source envoyées. Les programmes qui requièrent que les messages soient remis dans un ordre déterminé doivent intégrer cette fonction dans leurs applications (par exemple, en incluant un ID qui augmente de manière monotone dans tous les messages).  
  
- **Messagerie fiable :** Canal homologue n’inclut pas un mécanisme pour garantir la réception des messages par tous les homologues. Pour garantir la remise des messages, vous devez écrire une couche de fiabilité sur le canal homologue.
