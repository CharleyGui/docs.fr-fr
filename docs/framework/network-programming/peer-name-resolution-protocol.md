---
title: Protocole PNRP
description: En savoir plus sur le protocole PNRP (Peer Name Resolution Protocol), un protocole de résolution de noms et d’inscription de noms sécurisé, évolutif et dynamique.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: d50514569d066d04391ce65522df789ed421dbed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239391"
---
# <a name="peer-name-resolution-protocol"></a>Protocole PNRP

Dans les environnements pair à pair, les pairs utilisent des systèmes de résolution de noms spécifiques pour résoudre les emplacements réseau les uns des autres (adresses, protocoles et ports) à partir de noms et d’autres types d’identificateurs. Dans le passé, la résolution des noms de pairs était compliquée en raison de la nature transitoire de la connectivité, et d’autres défauts du système DNS.  
  
 La plateforme de réseau pair à pair de Microsoft® Windows® a résolu ce problème grâce au protocole PNRP, à une inscription de noms sécurisée, évolutive et dynamique, ainsi qu’au protocole de résolution de noms développé à l’origine pour Windows XP, puis amélioré pour Windows Vista™. Le protocole PNRP fonctionne très différemment des systèmes traditionnels de résolution de noms, et offre de nouvelles possibilités aux développeurs d’applications.  
  
 Avec le protocole PNRP, les noms de pairs peuvent être appliqués à l’ordinateur, ou à certaines applications ou certains services de l’ordinateur. Une résolution de noms de pairs comprend une adresse, un port et éventuellement une charge utile étendue. Les avantages de ce système sont la tolérance de panne, l’absence de goulots d’étranglement et le fait que les résolutions de noms ne retournent jamais d’adresses périmées. Ce protocole constitue donc une excellente solution pour la localisation des utilisateurs mobiles.  
  
 En ce qui concerne la sécurité, les noms de pairs peuvent être publiés comme des noms sécurisés (protégés) ou non sécurisés (non protégés). Le protocole PNRP utilise le chiffrement à clé publique pour protéger les noms de pairs sécurisés contre l’usurpation d’identité. Les ordinateurs et les services peuvent être nommés à l’aide du protocole PNRP.  
  
Les particularités du protocole PNRP sont les suivantes :  
  
- Il est distribué et presque entièrement sans serveur. Les serveurs sont uniquement nécessaires pour le processus d’amorçage.  
  
- La publication des noms est sécurisée (elle n’implique pas de tierces parties). Contrairement à la publication de noms DNS, la publication de noms PNRP est instantanée et sans coûts financiers.  
  
- Le protocole PNRP est mis à jour en temps réel, ce qui évite la résolution d’adresses périmées.  
  
- La résolution de noms via le protocole PNRP s’étend au-delà des ordinateurs, puisqu’elle permet également de résoudre des noms de services.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Espace de noms System.Net.PeerToPeer  
  
- La fonctionnalité PNRP est définie par l’espace de noms <xref:System.Net.PeerToPeer> dans le .NET Framework version 3.5. Elle fournit un ensemble de types qui peuvent être utilisés pour inscrire et résoudre des noms de pairs avec un service PNRP disponible.  
  
- Les programmes de résolution de pairs personnalisés et les programmes de résolution PNRP peuvent être créés et instanciés à l’aide des types fournis dans l’espace de noms <xref:System.ServiceModel.PeerResolvers>.  
  
- Les types de base utilisés pour inscrire et résoudre des noms avec un service PNRP disponible sont les suivants :  
  
- <xref:System.Net.PeerToPeer.Cloud> : définit les informations qui décrivent un cloud PNRP disponible, y compris son étendue.  
  
- <xref:System.Net.PeerToPeer.PeerName> : définit un nom de pair qui peut être utilisé pour inscrire puis résoudre un pair au sein d’un cloud.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord> : définit l’enregistrement du cloud PNRP qui contient les informations d’inscription d’un pair, notamment les points de terminaison réseau auxquels le pair peut être contacté.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration> : définit le processus d’inscription d’un nom de pair, y compris les méthodes pour démarrer et arrêter l’inscription des noms de pairs.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver> : définit la procédure de résolution d’un nom de pair en son point de terminaison réseau, y compris les méthodes synchrones et asynchrones de résolution.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Exemples de programmation réseau](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
