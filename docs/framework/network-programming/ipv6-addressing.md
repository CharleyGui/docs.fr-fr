---
title: Adressage IPv6
description: En savoir plus sur le protocole IPv6 (Internet Protocol version 6), les adresses, y compris la représentation textuelle et les types d’adresses.
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: fbf68cb5f40450c2f9ecf4900801ee55e326fcb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502338"
---
# <a name="ipv6-addressing"></a>Adressage IPv6

Dans le protocole IPv6, les adresses ont une longueur de 128 bits. Une telle taille d’espace d’adressage permet de subdiviser les adresses disponibles en une hiérarchie de domaines de routage qui reflète la topologie d’Internet. Elle permet également de mapper les adresses des cartes réseau (ou des interfaces) qui connectent les appareils au réseau. IPv6 contient une fonctionnalité inhérente permettant de résoudre les adresses au niveau le plus bas, c’est-à-dire au niveau de l’interface réseau, et contient également des fonctionnalités de configuration automatique.

## <a name="text-representation"></a>Représentation textuelle

Les trois formats conventionnels utilisés pour représenter les adresses IPv6 sous forme de chaînes textuelles sont les suivants :

- **Format hexadécimal/deux-points**. Il s’agit du format recommandé : n:n:n:n:n:n:n:n. Chaque n représente la valeur hexadécimale de l’un des huit éléments 16 bits de l’adresse. Par exemple : `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Format compressé**. En raison de la longueur des adresses, il est courant d’avoir des adresses comprenant une longue chaîne de zéros. Pour simplifier l’écriture de ces adresses, utilisez le format compressé, dans lequel une séquence ininterrompue de blocs de 0 est représentée par un double deux-points (::). Ce symbole peut n’apparaître qu’une seule fois dans une adresse. Par exemple, l’adresse de multidiffusion `FFED:0:0:0:0:BA98:3210:4562` s’affiche ainsi au format compressé : `FFED::BA98:3210:4562`. L’adresse de monodiffusion `3FFE:FFFF:0:0:8:800:20C4:0` s’affiche ainsi au format compressé : `3FFE:FFFF::8:800:20C4:0`. L’adresse de bouclage `0:0:0:0:0:0:0:1` s’affiche ainsi au format compressé : `::`. L’adresse non spécifiée `0:0:0:0:0:0:0:0` s’affiche ainsi au format compressé : `::`.

- **Format mixte**. Ce format associe les adresses IPv4 et IPv6. Dans ce cas, le format d’adresse est n:n:n:n:n:n:d.d.d.d, où chaque n représente les valeurs hexadécimales des six éléments d’adresse 16 bits d’ordre haut IPv6, et où chaque d représente la valeur décimale d’une adresse IPv4.

## <a name="address-types"></a>Types d’adresses

Les bits de début de l’adresse déterminent le type de l’adresse IPv6. Le champ de longueur variable qui contient ces bits de début est appelé « préfixe de format ».

Une adresse de monodiffusion IPv6 est constituée de deux parties. La première partie contient le préfixe de l’adresse et la seconde contient l’identificateur d’interface. Voici comment écrire de manière concise la combinaison préfixe-adresse IPv6 : ipv6-address/prefix-length.

Voici un exemple d’adresse avec un préfixe 64 bits.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Dans cet exemple, le préfixe est `3FFE:FFFF:0:CD30`. L’adresse peut également être écrite au format compressé, de la manière suivante : `3FFE:FFFF:0:CD30::/64`.

IPv6 définit les types d’adresses suivants :

- **Adresses de monodiffusion**. Identificateur d’une interface unique. Un paquet envoyé à cette adresse est remis à l’interface identifiée. Les adresses de monodiffusion se distinguent des adresses de multidiffusion par la valeur de l’octet d’ordre haut. L’octet d’ordre haut des adresses de multidiffusion a une valeur hexadécimale de FF. Pour cet octet, toute autre valeur correspond à une adresse de monodiffusion. Voici les différents types d’adresses de monodiffusion :

  - **Adresses link-local**. Ces adresses sont utilisées sur une même liaison et sont au format suivant : FE80::*ID_interface*. Les adresses link-local sont utilisées entre les nœuds d’une liaison pour la configuration automatique d’adresse, la découverte de voisin, ou en l’absence d’un routeur. Une adresse link-local est utilisée principalement au démarrage et lorsque le système n’a pas encore acquis les adresses d’une plus grande étendue.

  - **Adresses site-local**. Ces adresses sont utilisées sur un même site et sont au format suivant : FEC0::*ID_sous_réseau*:*ID_interface*. Les adresses site-local sont utilisées pour l’adressage à l’intérieur d’un site sans recourir à un préfixe global.

  - **Adresses de monodiffusion IPv6 globales**. Ces adresses peuvent être utilisées sur Internet et sont au format suivant : 010(FP, 3 bits) TLA ID (13 bits) Reserved (8 bits) NLA ID (24 bits) SLA ID (16 bits) *ID_interface* (64 bits).

- **Adresses de multidiffusion**. Identificateur d’un ensemble d’interfaces (appartenant généralement à des nœuds différents). Un paquet envoyé à cette adresse est remis à toutes les interfaces identifiées par cette adresse. Les types d’adresses de multidiffusion remplacent les adresses de diffusion IPv4.

- **Adresses anycast**. Identificateur d’un ensemble d’interfaces (appartenant généralement à des nœuds différents). Un paquet envoyé à cette adresse est remis à seulement une interface identifiée par cette adresse. Il s’agit de l’interface la plus proche, d’après les métriques de routage. Les adresses anycast proviennent de l’espace d’adressage de monodiffusion et ne peuvent pas être distinguées par leur syntaxe. L’interface adressée effectue la distinction entre les adresses de monodiffusion et les adresses anycast, dans le cadre de sa configuration.

En général, un nœud a toujours une adresse link-local. Il peut avoir une adresse site-local, et une ou plusieurs adresses globales.

## <a name="see-also"></a>Voir aussi

- [Protocole Internet version 6](internet-protocol-version-6.md)
- [Sockets](sockets.md)
