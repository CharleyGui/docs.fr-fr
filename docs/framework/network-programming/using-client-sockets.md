---
title: Utilisation de sockets clients
description: Cet exemple montre comment créer une connexion TCP/IP à un service distant à l’aide d’un socket dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: 6982d09c20cd0d7e9d27fc63880b39e0982c86ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265191"
---
# <a name="using-client-sockets"></a><span data-ttu-id="64457-103">Utilisation de sockets clients</span><span class="sxs-lookup"><span data-stu-id="64457-103">Using Client Sockets</span></span>

<span data-ttu-id="64457-104">Avant de démarrer une conversation via un <xref:System.Net.Sockets.Socket>, vous devez créer un canal de données entre votre application et l’appareil distant.</span><span class="sxs-lookup"><span data-stu-id="64457-104">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="64457-105">Il existe d’autres protocoles et familles d’adresses réseau, mais cet exemple montre comment créer une connexion TCP/IP à un service distant.</span><span class="sxs-lookup"><span data-stu-id="64457-105">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="64457-106">TCP/IP utilise une adresse réseau et un numéro de port de service pour identifier un service de manière unique.</span><span class="sxs-lookup"><span data-stu-id="64457-106">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="64457-107">L’adresse réseau identifie un appareil spécifique sur le réseau ; le numéro de port identifie le service spécifique sur cet appareil faisant l’objet de la connexion.</span><span class="sxs-lookup"><span data-stu-id="64457-107">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="64457-108">La combinaison de l’adresse réseau et du port de service constitue un point de terminaison, qui est représenté par la classe <xref:System.Net.EndPoint> dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="64457-108">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="64457-109">Un descendant du point de terminaison (**EndPoint**) est défini pour chaque famille d’adresses prise en charge. Pour la famille d’adresses IP, il s’agit de la classe <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="64457-109">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="64457-110">La classe <xref:System.Net.Dns> fournit des services de nom de domaine aux applications qui utilisent des services Internet TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="64457-110">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="64457-111">La méthode <xref:System.Net.Dns.Resolve%2A> interroge un serveur DNS pour mapper un nom de domaine convivial (par exemple, « host.contoso.com ») à une adresse Internet numérique (par exemple, 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="64457-111">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="64457-112">**Resolve** retourne un <xref:System.Net.IPHostEntry> qui contient une liste des adresses et alias pour le nom demandé.</span><span class="sxs-lookup"><span data-stu-id="64457-112">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="64457-113">Dans la plupart des cas, vous pouvez utiliser la première adresse retournée dans le tableau <xref:System.Net.IPHostEntry.AddressList%2A>.</span><span class="sxs-lookup"><span data-stu-id="64457-113">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="64457-114">Le code suivant obtient un <xref:System.Net.IPAddress> contenant l’adresse IP du serveur host.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="64457-114">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="64457-115">L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants. Pour plus d’informations, consultez [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).</span><span class="sxs-lookup"><span data-stu-id="64457-115">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="64457-116">Les autres services peuvent avoir un numéro de port compris dans la plage 1 024 à 65 535.</span><span class="sxs-lookup"><span data-stu-id="64457-116">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="64457-117">Le code suivant combine l’adresse IP du serveur host.contoso.com avec un numéro de port pour créer un point de terminaison distant pour une connexion.</span><span class="sxs-lookup"><span data-stu-id="64457-117">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="64457-118">Après avoir déterminé l’adresse de l’appareil distant et sélectionné le port à utiliser pour la connexion, l’application peut essayer d’établir une connexion avec l’appareil distant.</span><span class="sxs-lookup"><span data-stu-id="64457-118">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="64457-119">L’exemple suivant utilise un **IPEndPoint** existant pour établir une connexion à un appareil distant et intercepte les exceptions qui sont levées.</span><span class="sxs-lookup"><span data-stu-id="64457-119">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="64457-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64457-120">See also</span></span>

- [<span data-ttu-id="64457-121">Utilisation d’un socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="64457-121">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="64457-122">Utilisation d’un socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="64457-122">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="64457-123">Procédure : créer un socket</span><span class="sxs-lookup"><span data-stu-id="64457-123">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="64457-124">Sockets</span><span class="sxs-lookup"><span data-stu-id="64457-124">Sockets</span></span>](sockets.md)
