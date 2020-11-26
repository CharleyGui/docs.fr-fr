---
title: Noms d’homologues et ID PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: a56200d599d417dac549af000b35024338d43796
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239222"
---
# <a name="peer-names-and-pnrp-ids"></a>Noms d’homologues et ID PNRP

Un nom de pair représente un point de terminaison pour la communication. Il peut s’agir d’un ordinateur, d’un utilisateur, d’un groupe, d’un service ou de tout autre élément associé à un pair pouvant être résolu en une adresse IPv6. Le protocole PNRP utilise le nom de pair statistiquement unique pour la création d’un ID PNRP, qui est utilisé pour identifier les membres du cloud.  
  
## <a name="peer-names"></a>Noms de pairs  

 Les noms de pairs peuvent être inscrits comme étant sécurisés ou non sécurisés. Les noms non sécurisés sont de simples chaînes de texte qui peuvent faire l’objet d’une usurpation d’identité, puisque n’importe qui peut inscrire une duplication d’un nom non sécurisé. Il est préférable d’utiliser les noms non sécurisés au sein de réseaux privés ou protégés. Les noms sécurisés sont protégés par un certificat et une signature numérique. Seul l’éditeur d’origine est en mesure de prouver sa propriété d’un nom sécurisé.  
  
 La combinaison d’un cloud et d’une étendue fournit un environnement relativement sécurisé pour les pairs qui participent à des activités PNRP. Toutefois, l’utilisation d’un nom de pair sécurisé ne garantit pas la sécurité de l’ensemble de l’application réseau. La sécurité d’une application dépend de son implémentation.  
  
 Les noms de pairs sécurisés sont inscrits uniquement par leur propriétaire et sont protégés par un chiffrement à clé publique. Un nom de pair sécurisé est considéré comme appartenant à l’entité pair qui contient la clé privée correspondante. La propriété peut être prouvée via l’adresse pair certifiée, qui est signée à l’aide de la clé privée. Un utilisateur malveillant ne peut pas feindre la propriété d’un nom de pair sans disposer de la clé privée correspondante.  
  
## <a name="pnrp-ids"></a>ID PNRP  

 ![ID PNRP](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Les ID PNRP sont formés des composants suivants :  
  
- Les 128 bits d’ordre haut (appelés ID pair à pair (P2P)) correspondent au hachage d’un nom de pair attribué au point de terminaison. Le nom de pair est au format suivant : *Autorité.Classifieur*. Pour les noms sécurisés, *l’autorité* correspond au hachage SHA1 de la clé publique du nom de pair en caractères hexadécimaux. Pour les noms non sécurisés, *l’autorité* correspond au caractère « 0 ». Le *classifieur* est une chaîne qui identifie l’application. Aucun classifieur de nom de pair ne peut dépasser les 149 caractères, terminateur `null` compris.  
  
- Les 128 bits d’ordre bas sont utilisés pour l’emplacement du service, qui est un nombre généré qui identifie les différentes instances du même ID P2P dans un même cloud.  
  
 Cette combinaison d’ID P2P et de l’emplacement du service permet à plusieurs ID PNRP d’être inscrits à partir d’un même ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
