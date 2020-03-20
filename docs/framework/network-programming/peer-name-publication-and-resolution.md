---
title: Résolution et publication de nom de pair
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 4a0787972a61f5700d1e8728be96db8ef9ee749e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623201"
---
# <a name="peer-name-publication-and-resolution"></a>Résolution et publication de nom de pair

## <a name="publishing-a-peer-name"></a>Publication d’un nom de pair  

 Pour publier un nouvel ID PNRP, un pair effectue les opérations suivantes :  
  
- Il envoie des messages de publication PNRP à ses voisins du cache (les pairs dont les ID PNRP sont inscrits au niveau le plus bas du cache) pour amorcer leur cache.  
  
- Il choisit de manière aléatoire des nœuds dans le cloud qui ne sont pas ses voisins et leur envoie des requêtes de résolution de nom PNRP pour son propre ID P2P. Le processus de détermination du point de terminaison qui en résulte amorce les caches de nœuds du cloud choisis aléatoirement avec l’ID PNRP du pair de publication.  
  
Les nœuds PNRP version 2 ne publient pas les ID PNRP s’ils résolvent uniquement d’autres ID P2P. La valeur de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 (type REG_DWORD) spécifie que les pairs utilisent uniquement PNRP pour la résolution de noms et jamais pour la publication de noms. Cette valeur de Registre peut également être configurée via la stratégie de groupe.  
  
## <a name="resolving-a-peer-name"></a>Résolution d’un nom de pair

 Le processus de localisation d’autres pairs sur un réseau PNRP ou dans le cloud comprend deux phases :  
  
1. Détermination du point de terminaison  
  
2. Résolution de l’ID PNRP  
  
 Durant la phase de détermination du point de terminaison, un pair qui tenterait de résoudre l’ID PNRP d’un service sur un autre ordinateur va déterminer l’adresse IPv6 de ce pair distant.  Le pair distant est celui qui a publié l’ID PNRP de l’ordinateur ou du service, ou qui est associé à cet ID.  
  
 Après avoir vérifié que le point de terminaison distant a été inscrit dans le cloud PNRP, le pair qui a effectué une demande durant la phase de résolution de l’ID PNRP envoie une demande au point de terminaison pour connaître l’ID PNRP du service souhaité. Le point de terminaison envoie une réponse confirmant l’ID PNRP du service, un commentaire, et jusqu’à 4 Ko d’informations supplémentaires, que le pair à l’origine de la demande peut utiliser pour de futures communications. Par exemple, si le point de terminaison souhaité est un serveur de jeu, les données d’enregistrement de nom de pair supplémentaires peuvent contenir des informations sur le jeu, le niveau du jeu et le nombre actuel de joueurs.  
  
 Dans la phase de détermination du point de terminaison, PNRP utilise un processus itératif pour localiser le nœud qui a publié l’ID PNRP. Durant ce processus, le nœud qui effectue la résolution est chargé de contacter les nœuds qui sont successivement les plus proches de l’ID PNRP cible.  
  
 Pour effectuer la résolution de noms dans PNRP, le pair recherche dans les entrées de son propre cache une entrée correspondant à l’ID PNRP cible. S’il en trouve une, le pair envoie un message de demande PNRP au pair et attend une réponse. Si aucune entrée d’ID PNRP n’est trouvée, le pair envoie un message de demande PNRP au pair qui correspond à l’entrée dont l’ID PNRP est la plus proche de l’ID PNRP cible. Le nœud qui reçoit le message de demande PNRP examine son propre cache et effectue les opérations suivantes :  
  
- Si l’ID PNRP est trouvé, le pair de point de terminaison qui a reçu la demande répond directement au pair qui a effectué la demande.  
  
- Si l’ID PNRP n’est pas trouvé, et qu’un ID PNRP du cache est proche de l’ID PNRP cible, le pair qui a reçu la demande envoie au pair demandeur une réponse contenant l’adresse IPv6 du pair dont l’ID PNRP est le plus proche de l’ID PNRP cible. À l’aide de l’adresse IP fournie dans la réponse, le nœud demandeur envoie un autre message PNRP à l’adresse IPv6 pour demander une réponse ou l’autorisation d’examiner son cache.  
  
- Si l’ID PNRP n’est pas trouvé, et si aucun des ID PNRP du cache n’est proche du ID PNRP cible, le pair qui reçoit la demande envoie au pair demandeur une réponse indiquant cette condition. Le pair demandeur choisit alors l’ID PNRP le plus proche.  
  
Le pair demandeur continue ce processus avec des itérations successives dans le but de localiser le nœud qui a inscrit l’ID PNRP.  
  
 Dans l’espace de noms <xref:System.Net.PeerToPeer>, il existe une relation plusieurs-à-plusieurs entre les enregistrements <xref:System.Net.PeerToPeer.PeerName> qui contiennent les points de terminaison, et les clouds PNRP ou les mailles avec lesquels ils communiquent. Lorsqu’il y a des entrées obsolètes ou en double, ou plusieurs nœuds portant le même nom de pair, les nœuds PNRP peuvent obtenir des informations actuelles à l’aide de la classe <xref:System.Net.PeerToPeer.PeerNameResolver>. Les méthodes <xref:System.Net.PeerToPeer.PeerNameResolver> utilisent un seul nom de pair pour simplifier les enregistrements de noms de pairs : de un à plusieurs pairs et d’un pair à plusieurs clouds. Ceci est similaire à une requête effectuée à l’aide d’une jointure de table relationnelle. Lorsque vous avez terminé, l’objet Resolver retourne un <xref:System.Net.PeerToPeer.PeerNameRecordCollection> pour le nom de pair spécifié.  Par exemple, un nom de pair peut apparaître dans tous les enregistrements de noms de pairs de la collection, qui sont classés par cloud. Il s’agit là des instances du nom de pair dont les données prises en charge peuvent être demandées par une application PNRP.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.PeerToPeer>
