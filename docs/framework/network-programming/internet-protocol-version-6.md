---
title: Protocole Internet version 6
description: Découvrez le protocole IPv6 et sa différence par rapport à IPv4. Les applications .NET Framework prennent en charge IPv6, mais peuvent nécessiter une configuration.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: c2b23705ae309436344513e54d6258e206d69da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551463"
---
# <a name="internet-protocol-version-6"></a>Protocole Internet version 6
Le protocole IPv6 (protocole Internet version 6) est une nouvelle suite de protocoles standard conçus pour la couche réseau d’Internet. IPv6 est destiné à résoudre bon nombre des problèmes de l’actuelle version de la suite de protocoles (appelée IPv4), notamment ceux liés à l’épuisement des adresses, la sécurité, la configuration automatique, l’extensibilité, etc. IPv6 étend les capacités d’Internet à de nouveaux types d’applications, comme les applications pair à pair (P2P) et les applications mobiles. Voici les principaux problèmes du protocole IPv4 actuel :  
  
- Épuisement rapide de l’espace d’adressage.  
  
     Cela a conduit à l’utilisation de NAT (Network Address Translator) pour mapper plusieurs adresses privées à une seule adresse IP publique. Les principaux problèmes de ce mécanisme sont la surcharge de traitement et l’absence de connectivité de bout en bout.  
  
- Prise en charge hiérarchique insuffisante.  
  
     En raison de son organisation inhérente en classes prédéfinies, IPv4 n’offre pas de véritable prise en charge hiérarchique. Il est impossible d’organiser les adresses IP en les mappant parfaitement à la topologie du réseau. Ce défaut de conception majeur impose l’utilisation de tables de routage de grande taille pour la remise des paquets IPv4 sur Internet.  
  
- Configuration complexe du réseau.  
  
     Avec IPv4, les adresses doivent être assignées de façon statique ou à l’aide d’un protocole de configuration tel que DHCP. Dans l’idéal, les ordinateurs hôtes ne devraient pas avoir à s’appuyer sur l’administration d’une infrastructure DHCP. Ils devraient pouvoir effectuer la configuration eux-mêmes en fonction du segment réseau où ils se trouvent.  
  
- Absence de mécanismes d’authentification et de confidentialité intégrés.  
  
     IPv4 ne nécessite pas la prise en charge d’un mécanisme qui fournit l’authentification ou le chiffrement des données échangées. Cela n’est plus le cas avec IPv6. La sécurité du protocole Internet (IPsec) est une exigence de prise en charge d’IPv6.  
  
 Une nouvelle suite de protocoles doit répondre aux exigences de base suivantes :  
  
- Routage et adressage à grande échelle, avec une faible surcharge.  
  
- Configuration automatique pour diverses situations de connexion.  
  
- Authentification et confidentialité intégrées.  
  
 Pour plus d’informations, consultez [Adressage IPv6](ipv6-addressing.md), [Routage IPv6](ipv6-routing.md), [Configuration automatique IPv6](ipv6-auto-configuration.md), [Activation et désactivation d’IPv6](enabling-and-disabling-ipv6.md) et [Guide pratique pour modifier le fichier de configuration de l’ordinateur en vue de la prise en charge d’IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Références  
 Voici une sélection de normes RFC que vous pouvez consulter sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/) :  
  
- RFC 1287 : Towards the Future Internet Architecture.  
  
- RFC 1454 : Comparison of Proposals for Next Version of IP.  
  
- RFC 2373 : IP Version 6 Addressing Architecture.  
  
- RFC 2374 : An IPv6 Aggregatable Global Unicast Address Format.  
  
 Vous pouvez également trouver des informations concernant IPv6 dans la section [IP Version 6 (IPv6)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Exemple de sockets IPv6](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))
- [Exemples de programmation réseau](network-programming-samples.md)
- [Sockets](sockets.md)
