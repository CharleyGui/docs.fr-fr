---
title: 'Procédure : créer un socket'
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
ms.openlocfilehash: 54706293784d77e535cac582c99b1dd21a12e380
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048383"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="3c1f1-102">Procédure : créer un socket</span><span class="sxs-lookup"><span data-stu-id="3c1f1-102">How to: Create a Socket</span></span>
<span data-ttu-id="3c1f1-103">Avant de pouvoir utiliser un socket pour communiquer avec des appareils distants, le socket doit être initialisé avec des informations de protocole et d’adresse réseau.</span><span class="sxs-lookup"><span data-stu-id="3c1f1-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="3c1f1-104">Le constructeur de la classe <xref:System.Net.Sockets.Socket> a des paramètres qui spécifient la famille d’adresses, le type de socket et le type de protocole que le socket utilise pour établir des connexions.</span><span class="sxs-lookup"><span data-stu-id="3c1f1-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1f1-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="3c1f1-105">Example</span></span>  
 <span data-ttu-id="3c1f1-106">L’exemple suivant crée un socket qui peut être utilisé pour communiquer sur un réseau TCP/IP comme Internet.</span><span class="sxs-lookup"><span data-stu-id="3c1f1-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="3c1f1-107">Pour utiliser le protocole UDP plutôt que TCP, remplacez le type de protocole, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3c1f1-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="3c1f1-108">L’énumération <xref:System.Net.Sockets.AddressFamily> spécifie les familles d’adresses standard utilisées par la classe **Socket** pour résoudre les adresses réseau (par exemple, le membre **AddressFamily.InterNetwork** spécifie la famille d’adresses IP version 4).</span><span class="sxs-lookup"><span data-stu-id="3c1f1-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="3c1f1-109">L’énumération <xref:System.Net.Sockets.SocketType> spécifie le type de socket (par exemple, le membre **SocketType.Stream** indique un socket standard pour envoyer et recevoir des données avec le contrôle de flux).</span><span class="sxs-lookup"><span data-stu-id="3c1f1-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="3c1f1-110">L’énumération <xref:System.Net.Sockets.ProtocolType> spécifie le protocole réseau à utiliser lors de communications sur le **socket** (par exemple, **ProtocolType.Tcp** indique que le socket utilise TCP ; **ProtocolType.Udp** indique que le socket utilise UDP).</span><span class="sxs-lookup"><span data-stu-id="3c1f1-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="3c1f1-111">Une fois qu’un **socket** est créé, il peut initier une connexion à un point de terminaison distant ou recevoir des connexions d’appareils distants.</span><span class="sxs-lookup"><span data-stu-id="3c1f1-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1f1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c1f1-112">See also</span></span>

- [<span data-ttu-id="3c1f1-113">Utilisation de sockets clients</span><span class="sxs-lookup"><span data-stu-id="3c1f1-113">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="3c1f1-114">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="3c1f1-114">Listening with Sockets</span></span>](listening-with-sockets.md)
