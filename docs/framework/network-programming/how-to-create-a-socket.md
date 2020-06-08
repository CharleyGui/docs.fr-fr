---
title: 'Comment : créer un socket'
description: Découvrez comment initialiser un socket pour communiquer avec des appareils distants. Utilisez la classe Socket pour spécifier la famille d’adresses, le type de socket et le type de protocole.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502546"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="7a523-104">Comment : créer un socket</span><span class="sxs-lookup"><span data-stu-id="7a523-104">How to: Create a Socket</span></span>
<span data-ttu-id="7a523-105">Avant de pouvoir utiliser un socket pour communiquer avec des appareils distants, le socket doit être initialisé avec des informations de protocole et d’adresse réseau.</span><span class="sxs-lookup"><span data-stu-id="7a523-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="7a523-106">Le constructeur de la classe <xref:System.Net.Sockets.Socket> a des paramètres qui spécifient la famille d’adresses, le type de socket et le type de protocole que le socket utilise pour établir des connexions.</span><span class="sxs-lookup"><span data-stu-id="7a523-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a523-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a523-107">Example</span></span>  
 <span data-ttu-id="7a523-108">L’exemple suivant crée un socket qui peut être utilisé pour communiquer sur un réseau TCP/IP comme Internet.</span><span class="sxs-lookup"><span data-stu-id="7a523-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="7a523-109">Pour utiliser le protocole UDP plutôt que TCP, remplacez le type de protocole, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a523-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="7a523-110">L’énumération <xref:System.Net.Sockets.AddressFamily> spécifie les familles d’adresses standard utilisées par la classe **Socket** pour résoudre les adresses réseau (par exemple, le membre **AddressFamily.InterNetwork** spécifie la famille d’adresses IP version 4).</span><span class="sxs-lookup"><span data-stu-id="7a523-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="7a523-111">L’énumération <xref:System.Net.Sockets.SocketType> spécifie le type de socket (par exemple, le membre **SocketType.Stream** indique un socket standard pour envoyer et recevoir des données avec le contrôle de flux).</span><span class="sxs-lookup"><span data-stu-id="7a523-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="7a523-112">L’énumération <xref:System.Net.Sockets.ProtocolType> spécifie le protocole réseau à utiliser lors de communications sur le **socket** (par exemple, **ProtocolType.Tcp** indique que le socket utilise TCP ; **ProtocolType.Udp** indique que le socket utilise UDP).</span><span class="sxs-lookup"><span data-stu-id="7a523-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="7a523-113">Une fois qu’un **socket** est créé, il peut initier une connexion à un point de terminaison distant ou recevoir des connexions d’appareils distants.</span><span class="sxs-lookup"><span data-stu-id="7a523-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a523-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a523-114">See also</span></span>

- [<span data-ttu-id="7a523-115">Utilisation de sockets clients</span><span class="sxs-lookup"><span data-stu-id="7a523-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="7a523-116">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="7a523-116">Listening with Sockets</span></span>](listening-with-sockets.md)
