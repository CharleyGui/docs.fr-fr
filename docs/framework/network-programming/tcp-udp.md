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
# <a name="tcp-udp"></a><span data-ttu-id="925b3-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="925b3-102">TCP-UDP</span></span>
<span data-ttu-id="925b3-103">Les applications peuvent utiliser les services TCP (Transmission Control Protocol) et UDP (User Datagram Protocol) avec les classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> et <xref:System.Net.Sockets.UdpClient>.</span><span class="sxs-lookup"><span data-stu-id="925b3-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="925b3-104">Ces classes de protocole reposent sur la classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>. Elles gèrent les informations relatives au transfert des données.</span><span class="sxs-lookup"><span data-stu-id="925b3-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="925b3-105">Les classes de protocole utilisent les méthodes synchrones de la classe **Socket** pour fournir un accès simple et direct aux services réseau sans avoir à tenir à jour les informations d’état ou à connaître les paramètres de configuration des sockets liés au protocole.</span><span class="sxs-lookup"><span data-stu-id="925b3-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="925b3-106">Vous pouvez utiliser les méthodes **Socket** asynchrones par le biais des méthodes asynchrones fournies par la classe <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="925b3-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="925b3-107">Pour accéder aux fonctionnalités de la classe **Socket** qui ne sont pas exposées par les classes de protocole, vous devez utiliser la classe **Socket**.</span><span class="sxs-lookup"><span data-stu-id="925b3-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="925b3-108">**TcpClient** et **TcpListener** représentent le réseau utilisant la classe **NetworkStream**.</span><span class="sxs-lookup"><span data-stu-id="925b3-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="925b3-109">Utilisez la méthode <xref:System.Net.Sockets.TcpClient.GetStream%2A> pour retourner le flux réseau, puis appelez les méthodes <xref:System.Net.Sockets.NetworkStream.Read%2A> et <xref:System.Net.Sockets.NetworkStream.Write%2A> du flux.</span><span class="sxs-lookup"><span data-stu-id="925b3-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="925b3-110">La classe **NetworkStream** ne possède pas le socket sous-jacent des classes de protocole. Sa fermeture n’a donc pas d’effet sur le socket.</span><span class="sxs-lookup"><span data-stu-id="925b3-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="925b3-111">La classe **UdpClient** utilise un tableau d’octets pour stocker le datagramme UDP.</span><span class="sxs-lookup"><span data-stu-id="925b3-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="925b3-112">Utilisez la méthode <xref:System.Net.Sockets.UdpClient.Send%2A> pour envoyer les données sur le réseau, et la méthode <xref:System.Net.Sockets.UdpClient.Receive%2A> pour recevoir un datagramme entrant.</span><span class="sxs-lookup"><span data-stu-id="925b3-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925b3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="925b3-113">See also</span></span>

- [<span data-ttu-id="925b3-114">Utilisation des services TCP</span><span class="sxs-lookup"><span data-stu-id="925b3-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="925b3-115">Utilisation des services UDP</span><span class="sxs-lookup"><span data-stu-id="925b3-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="925b3-116">Utilisation de flux sur le réseau</span><span class="sxs-lookup"><span data-stu-id="925b3-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="925b3-117">Utilisation d’un socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="925b3-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="925b3-118">Utilisation d’un socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="925b3-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="925b3-119">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="925b3-119">Using Application Protocols</span></span>](using-application-protocols.md)
