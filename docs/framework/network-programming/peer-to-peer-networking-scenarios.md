---
title: Scénarios de réseaux homologues
ms.date: 03/30/2017
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
ms.openlocfilehash: 9b5d4d35085585fe04f2f0c0a105e6dff4b1fcc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623087"
---
# <a name="peer-to-peer-networking-scenarios"></a>Scénarios de réseaux homologues

Les réseaux pair à pair (P2P) permettent ou améliorent les scénarios suivants :

## <a name="real-time-communications-rtc"></a>Communications en temps réel

- Messagerie instantanée sans serveur

  Les communications en temps réel sont couramment utilisées de nos jours. En effet, les utilisateurs d’ordinateurs peuvent discuter au moyen de conversations vocales ou vidéo. Toutefois, la plupart des programmes existants et de leurs protocoles de communication s’appuient sur des serveurs. Si vous appartenez à un réseau sans fil ad hoc ou à un réseau isolé, vous ne pouvez pas utiliser ces fonctionnalités de communication en temps réel. Le technologie pair à pair permet d’étendre les technologies de communication en temps réel aux autres environnements réseau.

- Matchmaking et jeu en temps réel

  Les jeux en temps réel font également partie des technologies couramment utilisées aujourd’hui. Il existe de nombreux sites de jeux en ligne qui proposent à la communauté des gamers de jouer sur Internet. Ils permettent de trouver d’autres joueurs ayant les mêmes centres d’intérêt et de jouer avec eux. Le problème est que les sites de jeux n’existent que sur Internet et sont destinés aux joueurs invétérés qui souhaitent se mesurer aux meilleurs joueurs du monde. Ces sites font le suivi de vos parties et fournissent des statistiques. Toutefois, ils ne permettent pas de configurer un jeu ad hoc entre joueurs disposant d’environnements réseau différents. Les réseaux pair à pair, en revanche, fournissent cette possibilité.

## <a name="collaboration"></a>Collaboration

- Espaces de travail de projet pour la résolution des problèmes

  Les applications d’espace de travail partagé permettent de créer des groupes de travail ad hoc, puis d’autoriser les propriétaires des groupes de travail à ajouter à l’espace de travail partagé les outils et le contenu qui permettront au groupe de résoudre un problème. Il peut s’agir de forums, d’outils de productivité ou de fichiers.

- Partage de fichiers

  Le partage d’un sous-ensemble d’espace de travail de projet correspond à la possibilité de partager des fichiers. Même si cette fonctionnalité est disponible dans la version actuelle de Windows, elle peut être améliorée grâce à l’utilisation d’un réseau pair à pair qui facilite la mise à disposition du contenu des fichiers. Le fait de faciliter l’accès à la grande richesse de contenu située à la périphérie d’Internet ou dans des environnements informatiques ad-hoc accroît l’intérêt de l’informatique en réseau.

- Partage des expériences

  Grâce au développement des technologies sans fil, les réseaux pair à pair vous permettent d’être en ligne au sein d’un groupe de pairs, et de partager vos expériences en temps réel (par exemple, un coucher de soleil, un concert de rock ou une croisière).

## <a name="content-distribution"></a>Distribution de contenu

- SMS

  Les réseaux pair à pair permettent la diffusion d’informations textuelles sous la forme de fichiers ou de messages vers un grand groupe d’utilisateurs. Il peut s’agir, par exemple, d’une liste de nouveautés.

- Audio et vidéo

  Les réseaux pair à pair peuvent également permettre de diffuser des informations audio ou vidéo pour un grand groupe d’utilisateurs, par exemple, lors d’un grand concert ou d’une réunion d’entreprise. À l’heure actuelle, pour distribuer du contenu, vous devez configurer des serveurs à capacité élevée pour collecter et distribuer la charge à des centaines, voire des milliers d’utilisateurs. Avec un réseau pair à pair, seuls quelques pairs obtiennent leur contenu des serveurs centralisés. Les pairs envoient ces informations à quelques autres personnes, qui les envoient à d’autres utilisateurs, et ainsi de suite. La charge de distribution du contenu est ainsi répartie entre les pairs du cloud. Un pair qui souhaite recevoir ce contenu va s’adresser au pair de distribution le plus proche.

- Distribution de mises à jour produit

  Les réseaux pair à pair peuvent également fournir un mécanisme efficace de distribution de logiciels tels que les mises à jour produit (mises à jour de sécurité et service packs). Un pair qui dispose d’une connexion à un serveur de distribution de logiciels peut obtenir la mise à jour produit et la propager vers les autres membres de son groupe.

## <a name="distributed-processing"></a>Traitement distribué

- Division et distribution d’une tâche

  Une tâche de calcul de grande envergure peut d’abord être divisée en plusieurs tâches de calcul plus petites, mieux adaptées aux ressources informatiques du pair. Un pair peut se charger de la division de la tâche de calcul. Ensuite, les réseaux pair à pair peuvent distribuer les différentes tâches à chaque pair du groupe. Chaque pair exécute sa tâche de calcul et signale ses résultats à un point d’accumulation centralisé.

- Agrégation des ressources informatiques

  Une autre façon d’utiliser les réseaux pair à pair pour le traitement distribué consiste à utiliser des programmes qui sont exécutés sur chaque pair pendant les périodes d’inactivité du processeur et qui font partie d’une plus grande tâche de calcul coordonnée par un serveur central. En regroupant les processeurs de plusieurs ordinateurs, les réseaux pair à pair peuvent transformer un groupe d’ordinateurs pairs en un grand processeur parallèle servant aux tâches de calcul de grande envergure.

## <a name="see-also"></a>Voir aussi

- <xref:System.Net.PeerToPeer.Collaboration>
