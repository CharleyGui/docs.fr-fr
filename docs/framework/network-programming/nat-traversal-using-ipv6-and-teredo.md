---
title: Parcours NAT avec IPv6 et Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: a6448ddf117e1f454338869820751ae5d9e0070e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258619"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Parcours NAT avec IPv6 et Teredo

Des améliorations ont été apportées à la prise en charge du parcours NAT. Ces changements prévoient l’utilisation d’IPv6 et de Teredo. Toutefois, d’autres technologies de tunneling IP peuvent être utilisées. Ces améliorations affectent les classes de <xref:System.Net> et les espaces de noms qui leur sont associés.  
  
 Ces modifications peuvent affecter les applications clientes et serveur qui doivent utiliser des technologies de tunneling IP.  
  
 Les modifications de prise en charge du parcours NAT sont disponibles uniquement pour les applications qui utilisent le .NET Framework version 4. Ces fonctionnalités ne sont pas disponibles dans les versions antérieures du .NET Framework.  
  
## <a name="overview"></a>Vue d'ensemble  

 Le protocole IPv4 définit une adresse IPv4 comme ayant une longueur de 32 bits. Par conséquent, il prend en charge environ 4 milliards d’adresses IP uniques (2^32). Lorsque le nombre d’ordinateurs et d’appareils réseau connectés à Internet a augmenté dans les années 1990, les limites de l’espace d’adressage IPv4 sont devenues évidentes.  
  
 L’une des techniques utilisées pour étendre la durée de vie d’IPv4 consiste à déployer le NAT pour permettre à une adresse IP publique unique de représenter un grand nombre d’adresses IP privées (intranet privé). Les adresses IP privées situées derrière un appareil NAT partagent une même adresse IPv4 publique. L’appareil NAT peut être un appareil matériel dédié (un point d’accès sans fil et un routeur peu coûteux, par exemple) ou un ordinateur exécutant un service NAT. L’appareil ou le service de cette adresse IP publique va traduire les paquets IP entre un Internet public et un intranet privé.  
  
 Ce modèle fonctionne bien pour les applications clientes exécutées sur un intranet privé qui envoient des requêtes à d’autres adresses IP (généralement des serveurs) sur Internet. L’appareil ou le serveur NAT peut conserver les requêtes client. Ainsi, lorsqu’une réponse est retournée, il sait où l’envoyer. Mais ce schéma pose problème pour les applications qui sont exécutées sur un intranet privé derrière un appareil NAT et qui souhaitent fournir des services, écouter les paquets et répondre. Cela est d’autant plus vrai pour les applications pair à pair.  
  
 Le protocole IPv6 définit une adresse IPv4 comme ayant une longueur de 128 bits. Par conséquent, IPv6 prend en charge un très grand espace d’adressage équivalant à 3,2 x 10^38 adresses uniques (2^128). Avec un espace d’adressage de cette taille, il est possible pour tous les appareils connectés à Internet de recevoir une adresse unique. Mais cela pose problème. En effet, IPv4 reste le protocole utilisé par la majorité des utilisateurs. La plupart des routeurs et points d’accès sans fil utilisés par les petites entreprises, les organisations et les particuliers ne prennent pas en charge IPv6. De plus, certains fournisseurs de services Internet ne prennent pas en charge ou n’ont pas configuré la prise en charge d’IPv6.  
  
 Plusieurs technologies de transition IPv6 ont été développées pour « tunneler » les adresses IPv6 dans un paquet IPv4. Ces technologies incluent les tunnels 6to4, ISATAP et Teredo, qui fournissent une attribution d’adresses et un tunneling automatique d’hôte à hôte pour un trafic IPv6 monodiffusion, lorsque les hôtes IPv6 doivent parcourir les réseaux IP4 pour atteindre d’autres réseaux IPv6. Les paquets IPv6 sont « tunnelés » sous la forme de paquets IPv4. Plusieurs techniques de tunneling utilisées actuellement permettent un parcours NAT pour les adresses IPv6 à travers un appareil NAT.  
  
 Teredo fait partie des technologies de transition IPv6 qui permettent une connectivité IPv6 aux réseaux IPv4. Teredo est documenté dans les normes RFC 4380 publiées par l’IETF (Internet Engineering Task Force). Windows XP SP2 et les versions ultérieures prennent en charge la carte virtuelle Teredo qui peut fournir une adresse IPv6 publique dans la plage 2001:0::/32. Cette adresse IPv6 peut être utilisée pour écouter les connexions entrantes à partir d’Internet et peut être fournie aux clients compatibles IPv6 qui souhaitent se connecter au service d’écoute. Ainsi, l’application n’a plus à se préoccuper de la manière dont elle doit contacter un ordinateur situé derrière un appareil NAT, puisqu’elle peut simplement se connecter à l’aide de son adresse Teredo IPv6.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Améliorations apportées à la prise en charge du parcours NAT et de Teredo  

 Des améliorations ont été apportées aux espaces de noms <xref:System.Net>, <xref:System.Net.NetworkInformation>, et <xref:System.Net.Sockets> pour prendre en charge le parcours NAT avec IPv6 et Teredo.  
  
 Plusieurs méthodes ont été ajoutées à la classe <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> pour obtenir la liste d’adresses IP de monodiffusion sur l’hôte. La méthode <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> lance une requête asynchrone pour récupérer la table des adresses IP de monodiffusion stable sur l’ordinateur local. La méthode <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> termine une requête asynchrone en attente pour récupérer la table des adresses IP de monodiffusion stable sur l’ordinateur local. La méthode <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> est une requête synchrone qui permet de récupérer la table d’adresses IP de monodiffusion stable sur l’ordinateur local, et d’attendre que la table d’adresses soit stable, si nécessaire.  
  
 La propriété <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> peut être utilisée pour déterminer si un <xref:System.Net.IPAddress> est une adresse Teredo IPv6.  
  
 L’association de ces nouvelles méthodes de classe <xref:System.Net.NetworkInformation.IPGlobalProperties> et de la propriété <xref:System.Net.IPAddress.IsIPv6Teredo%2A> permet à une application de retrouver facilement l’adresse Teredo. Généralement, une application a seulement besoin de connaître l’adresse Teredo locale si elle communique ces informations à des applications distantes. Par exemple, une application pair à pair peut envoyer toutes ses adresses IPv6 à un serveur de matchmaking qui peut ensuite les transférer à d’autres pairs pour permettre une communication directe.  
  
 Une application doit normalement définir son service d’écoute pour écouter <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> plutôt que l’adresse Teredo locale. Par conséquent, si un client ou un pair distant dispose d’un itinéraire IPv6 direct vers l’hôte du service d’écoute, le client ou le pair peut se connecter directement à l’aide d’IPv6, sans devoir utiliser Teredo pour « tunneler » les paquets.  
  
 Pour les applications TCP, la classe <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> comprend une méthode <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> qui permet un parcours NAT. Pour les applications UDP, la classe <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> comprend une méthode <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> qui permet un parcours NAT.  
  
 Pour les applications qui utilisent <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> et les classes associées, les méthodes <xref:System.Net.Sockets.Socket.GetSocketOption%2A> et <xref:System.Net.Sockets.Socket.SetSocketOption%2A> peuvent être utilisées avec l’option de socket <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> pour interroger, activer ou désactiver le parcours NAT.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
