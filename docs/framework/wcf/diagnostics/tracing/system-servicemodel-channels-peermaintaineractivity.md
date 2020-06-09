---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596075"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).  
  
## <a name="description"></a>Description  
 Ce suivi se produit pendant différentes opérations PeerMaintainer.  
  
 PeerMaintainer est un composant interne de PeerNode. Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés). Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier. Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins. Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles. Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
