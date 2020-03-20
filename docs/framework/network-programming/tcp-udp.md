---
title: TCP-UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047108"
---
# <a name="tcp-udp"></a>TCP-UDP
Les applications peuvent utiliser les services TCP (Transmission Control Protocol) et UDP (User Datagram Protocol) avec les classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> et <xref:System.Net.Sockets.UdpClient>. Ces classes de protocole reposent sur la classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>. Elles gèrent les informations relatives au transfert des données.  
  
 Les classes de protocole utilisent les méthodes synchrones de la classe **Socket** pour fournir un accès simple et direct aux services réseau sans avoir à tenir à jour les informations d’état ou à connaître les paramètres de configuration des sockets liés au protocole. Vous pouvez utiliser les méthodes **Socket** asynchrones par le biais des méthodes asynchrones fournies par la classe <xref:System.Net.Sockets.NetworkStream>. Pour accéder aux fonctionnalités de la classe **Socket** qui ne sont pas exposées par les classes de protocole, vous devez utiliser la classe **Socket**.  
  
 **TcpClient** et **TcpListener** représentent le réseau utilisant la classe **NetworkStream**. Utilisez la méthode <xref:System.Net.Sockets.TcpClient.GetStream%2A> pour retourner le flux réseau, puis appelez les méthodes <xref:System.Net.Sockets.NetworkStream.Read%2A> et <xref:System.Net.Sockets.NetworkStream.Write%2A> du flux. La classe **NetworkStream** ne possède pas le socket sous-jacent des classes de protocole. Sa fermeture n’a donc pas d’effet sur le socket.  
  
 La classe **UdpClient** utilise un tableau d’octets pour stocker le datagramme UDP. Utilisez la méthode <xref:System.Net.Sockets.UdpClient.Send%2A> pour envoyer les données sur le réseau, et la méthode <xref:System.Net.Sockets.UdpClient.Receive%2A> pour recevoir un datagramme entrant.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des services TCP](using-tcp-services.md)
- [Utilisation des services UDP](using-udp-services.md)
- [Utilisation de flux sur le réseau](using-streams-on-the-network.md)
- [Utilisation d’un socket serveur asynchrone](using-an-asynchronous-server-socket.md)
- [Utilisation d’un socket client asynchrone](using-an-asynchronous-client-socket.md)
- [Utilisation de protocoles d’application](using-application-protocols.md)
