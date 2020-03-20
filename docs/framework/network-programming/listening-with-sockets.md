---
title: écoute avec des sockets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180739"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="db6ef-102">écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="db6ef-102">Listening with Sockets</span></span>
<span data-ttu-id="db6ef-103">Les sockets de serveur et d’écoute ouvrent un port sur le réseau, puis attendent qu’un client se connecte à ce port.</span><span class="sxs-lookup"><span data-stu-id="db6ef-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="db6ef-104">Cet exemple montre comment créer un service distant pour un réseau TCP/IP, cependant, il existe d’autres protocoles et familles d’adresses réseau.</span><span class="sxs-lookup"><span data-stu-id="db6ef-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="db6ef-105">L’adresse unique d’un service TCP/IP peut être définie en combinant l’adresse IP de l’hôte avec le numéro de port du service afin de créer un point de terminaison pour ce service.</span><span class="sxs-lookup"><span data-stu-id="db6ef-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="db6ef-106">La classe <xref:System.Net.Dns> fournit des méthodes qui retournent des informations sur les adresses réseau prises en charge par l’appareil du réseau local.</span><span class="sxs-lookup"><span data-stu-id="db6ef-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="db6ef-107">Lorsque l’appareil du réseau local a plus d’une adresse réseau, ou si le système local prend en charge plusieurs appareils réseau, la classe **Dns** retourne des informations sur toutes les adresses réseau, et c’est à l’application de choisir l’adresse appropriée pour le service.</span><span class="sxs-lookup"><span data-stu-id="db6ef-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="db6ef-108">L’Internet Assigned Numbers Authority (Iana) définit les numéros portuaires pour les services communs; pour plus d’informations, voir [Nom de service et Registre des numéros de port du Protocole de transport](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="db6ef-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="db6ef-109">Les autres services peuvent avoir un numéro de port compris dans la plage 1 024 à 65 535.</span><span class="sxs-lookup"><span data-stu-id="db6ef-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="db6ef-110">L’exemple suivant crée un <xref:System.Net.IPEndPoint> pour un serveur en combinant la première adresse IP retournée par **Dns** pour l’ordinateur hôte, avec un numéro de port choisi dans la plage de numéros des ports inscrits.</span><span class="sxs-lookup"><span data-stu-id="db6ef-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="db6ef-111">Une fois le point de terminaison local déterminé, le <xref:System.Net.Sockets.Socket> doit être associé à ce point de terminaison à l’aide de la méthode <xref:System.Net.Sockets.Socket.Bind%2A>, puis configuré pour écouter le point de terminaison à l’aide de la méthode <xref:System.Net.Sockets.Socket.Listen%2A>.</span><span class="sxs-lookup"><span data-stu-id="db6ef-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="db6ef-112">**Bind** lève une exception si la combinaison adresse-port est déjà utilisée.</span><span class="sxs-lookup"><span data-stu-id="db6ef-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="db6ef-113">L’exemple suivant montre comment associer un **Socket** à un **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="db6ef-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="db6ef-114">La méthode **Listen** prend un seul paramètre qui spécifie combien de connexions au **Socket** peuvent être mises en attente avant qu’une erreur « Serveur occupé » soit retournée au client qui souhaite se connecter.</span><span class="sxs-lookup"><span data-stu-id="db6ef-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="db6ef-115">Dans ce cas, jusqu’à 100 clients peuvent être placés dans la file d’attente de connexion avant qu’une réponse « Serveur occupé » ne soit retournée au 101e client.</span><span class="sxs-lookup"><span data-stu-id="db6ef-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db6ef-116">See also</span></span>

- [<span data-ttu-id="db6ef-117">Utilisation d’un socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="db6ef-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="db6ef-118">Utilisation d’un socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="db6ef-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="db6ef-119">Utilisation de sockets clients</span><span class="sxs-lookup"><span data-stu-id="db6ef-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="db6ef-120">Comment : créer un socket</span><span class="sxs-lookup"><span data-stu-id="db6ef-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="db6ef-121">Sockets</span><span class="sxs-lookup"><span data-stu-id="db6ef-121">Sockets</span></span>](sockets.md)
