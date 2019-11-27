---
title: Programmation réseau dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204696"
---
# <a name="network-programming-in-the-net-framework"></a>Programmation réseau dans le .NET Framework
Microsoft .NET Framework fournit une implémentation en couche, extensible et managée des services Internet que vous pouvez intégrer rapidement et facilement à vos applications. Les applications réseau peuvent générer des protocoles enfichables pour tirer parti automatiquement de nouveaux protocoles Internet, ou elles peuvent utiliser une implémentation managée de l'interface Windows Socket pour fonctionner au niveau du socket.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Introduction aux protocoles enfichables](introducing-pluggable-protocols.md)  
 Décrit comment accéder à une ressource réseau sans tenir compte du protocole d'accès dont elle a besoin.  
  
 [Demande de données](requesting-data.md)  
 Explique comment utiliser des protocoles enfichables pour charger et télécharger les données à partir des ressources Internet.  
  
 [Programmation de protocoles enfichables](programming-pluggable-protocols.md)  
 Explique comment dériver les classes spécifiques au protocole pour implémenter des protocoles enfichables.  
  
 [Utilisation de protocoles d’application](using-application-protocols.md)  
 Décrit les applications de programmation qui tirent parti des protocoles réseau comme TCP, UDP, et HTTP.  
  
 [Protocole IPv6](internet-protocol-version-6.md)  
 Décrit les avantages du protocole IPv6 (Internet Protocol version 6) par rapport à la version actuelle de la suite des protocoles Internet (IPv4), décrit l’adressage IPv6, le routage et la configuration automatique, et comment activer et désactiver IPv6.  
  
 [Configuration des applications Internet](configuring-internet-applications.md)  
 Explique comment utiliser les fichiers de configuration .NET Framework pour configurer les applications Web.  
  
 [Traçage réseau dans .NET Framework](network-tracing.md)  
 Explique comment utiliser le traçage réseau pour obtenir des informations sur les appels de méthode et le trafic réseau généré par une application managée.  
  
 [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)  
 Décrit comment utiliser la mise en cache pour les applications qui utilisent les classes <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>et <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .  
  
 [Sécurité dans la programmation réseau](security-in-network-programming.md)  
 Explique comment utiliser des techniques standard de sécurité Internet et d'authentification.  
  
 [Bonnes pratiques pour les classes System.Net](best-practices-for-system-net-classes.md)  
 Fournit des conseils et des astuces pour profiter au mieux de vos applications Web.  
  
 [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)  
 Décrit comment configurer des proxies.  
  
 [NetworkInformation](networkinformation.md)  
 Explique comment collecter des informations sur les événements, les modifications, les statistiques et les propriétés réseau et explique également comment déterminer si un hôte distant est accessible ou non à l'aide de la classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> .  
  
 [Modifications apportées à l’espace de noms System.Uri dans la version 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Décrit plusieurs modifications apportées à la classe <xref:System.Uri?displayProperty=nameWithType> dans la version 2.0 pour corriger les comportements incorrects, améliorer la convivialité et la sécurité.  
  
 [Prise en charge de l’identificateur de ressource internationalisée (IRI) dans System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Décrit les améliorations apportées à la classe <xref:System.Uri?displayProperty=nameWithType> dans la version 3.5, 3.0 SP1, et 2.0 SP1 pour la prise en charge de l'identifiant de ressource internationalisée et du nom de domaine internationalisé.  
  
 [Améliorations des performances de socket dans la version 3.5](socket-performance-enhancements-in-version-3-5.md)  
 Décrit un ensemble d'améliorations apportées à la classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> dans la version 3.5, 3.0 SP1 et 2.0 SP1 qui fournit un autre modèle asynchrone pouvant être utilisé par les applications de socket spécialisées très performantes.  
  
 [Protocole PNRP](peer-name-resolution-protocol.md)  
 Décrit l’ajout de la prise en charge à la version 3.5 pour prendre en charge le protocole PNRP (Peer Name Resolution Protocol), une inscription de noms dynamiques et sans serveur et un protocole de résolution de noms. Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer?displayProperty=nameWithType> .  
  
 [Collaboration pair à pair](peer-to-peer-collaboration.md)  
 Décrit l'ajout de la prise en charge à la version 3.5 pour prendre en charge la collaboration pair à pair qui s'appuie sur PNRP. Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> .  
  
 [Changements apportés à l’authentification NTLM pour HttpWebRequest dans la version 3.5 SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Décrit les changements de sécurité apportés à la version 3.5 SP1 qui affectent la manière dont l'intégration de l'authentification Windows est gérée par <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, et les classes associées dans l'espace de noms System.Net.  
  
 [Authentification Windows intégrée avec protection étendue](integrated-windows-authentication-with-extended-protection.md)  
 Décrit les améliorations de la protection étendue qui affectent la manière dont l'authentification Windows intégrée est gérée par <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, et les classes associées dans <xref:System.Net?displayProperty=nameWithType> et les espaces de noms associés.  
  
 [Parcours NAT avec IPv6 et Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Décrit les améliorations apportées aux espaces de noms <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, et <xref:System.Net.Sockets?displayProperty=nameWithType> pour prendre en charge le parcours NAT avec IPv6 et Teredo.  
  
 [Isolement réseau pour les applications du Windows Store](network-isolation-for-windows-store-apps.md)  
 Décrit l’impact de l’isolement réseau lorsque les classes des espaces de noms <xref:System.Net>, <xref:System.Net.Http>et <xref:System.Net.Http.Headers> sont utilisées dans les applications du Windows 8. x Store.  
  
 [Exemples de programmation réseau](network-programming-samples.md)  
 Liens vers des exemples téléchargeables de programmation qui utilisent des classes dans les espaces de noms <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> .  
  
## <a name="reference"></a>Référence  
 <xref:System.Net?displayProperty=nameWithType>  
 Constitue une interface de programmation simple pour un grand nombre des protocoles réseau employés aujourd'hui. Les classes <xref:System.Net.WebRequest?displayProperty=nameWithType> et <xref:System.Net.WebResponse?displayProperty=nameWithType> de cet espace de noms servent de base aux protocoles enfichables.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Définit les types et les énumérations utilisés pour définir des stratégies de cache applicables aux ressources et obtenus via l'utilisation des classes <xref:System.Net.WebRequest?displayProperty=nameWithType> et <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Classes utilisées par les applications pour accéder et mettre à jour par programmation des paramètres de configuration pour les espaces de noms System.Net.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Classes qui fournissent une interface de programmation pour les applications HTTP modernes.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Prend en charge les collections d'en-têtes HTTP utilisés par l'espace de noms <xref:System.Net.Http?displayProperty=nameWithType>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Classes pour composer et envoyer des messages à l'aide du protocole SMTP.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Définit les types utilisés pour représenter les en-têtes MIME (Multipurpose Internet Mail Exchange) utilisés par les classes de l'espace de noms <xref:System.Net.Mail?displayProperty=nameWithType> .  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 Classes permettant de recueillir des informations par programmation sur les événements, les modifications, des statistiques et les propriétés réseau.  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 Fournit une implémentation managée du protocole PNRP (Peer Name Resolution Protocol) pour les développeurs.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 Fournit une implémentation managée de l'interface de collaboration pair à pair aux développeurs.  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 Classes pour fournir des flux de réseau pour des communications sécurisées entre les hôtes.  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 Fournit une implémentation managée de l'interface Windows Sockets (Winsock) pour les développeurs qui doivent aider à contrôler étroitement l'accès au réseau.  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 Fournit une implémentation managée de l'interface WebSocket pour les développeurs.  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 Fournit une représentation objet d'un URI (Uniform Resource Identifier) et un accès simplifié aux parties de l'identificateur.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 Fournit un support pour l'authentification à l'aide de la protection étendue pour les applications.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 Fournit un support pour la configuration de l'authentification à l'aide de la protection étendue pour les applications.  
  
## <a name="see-also"></a>Voir aussi

- [Bonnes pratiques du protocole TLS (Transport Layer Security) avec le .NET Framework](tls.md)
- [Rubriques de guide pratique sur la programmation réseau](network-programming-how-to-topics.md)
- [Exemples de programmation réseau](network-programming-samples.md)
- [Exemple HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
