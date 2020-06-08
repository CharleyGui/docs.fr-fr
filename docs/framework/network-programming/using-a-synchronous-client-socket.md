---
title: Utilisation d’un socket client synchrone
description: Cet exemple montre un socket client synchrone dans le .NET Framework, qui interrompt le programme d’application pendant que l’opération réseau se termine.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: ef682af33c10cf06ffc398c22e4a7dc1adf8290e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502065"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="96383-103">Utilisation d’un socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="96383-103">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="96383-104">Un socket client synchrone interrompt l’exécution de l’application durant l’opération réseau.</span><span class="sxs-lookup"><span data-stu-id="96383-104">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="96383-105">Les sockets synchrones ne sont pas appropriés pour les applications dont l’exécution nécessite une utilisation intensive du réseau, mais ils facilitent l’accès aux services réseau pour les autres applications.</span><span class="sxs-lookup"><span data-stu-id="96383-105">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="96383-106">Pour envoyer les données, passez un tableau d’octets à l’une des méthodes d’envoi de données de la classe <xref:System.Net.Sockets.Socket> (<xref:System.Net.Sockets.Socket.Send%2A> et <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="96383-106">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="96383-107">L’exemple suivant encode une chaîne dans une mémoire tampon de tableau d’octets à l’aide de la propriété <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>, puis transmet la mémoire tampon à l’appareil réseau avec la méthode **Send**.</span><span class="sxs-lookup"><span data-stu-id="96383-107">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="96383-108">La méthode **Send** retourne le nombre d’octets envoyés à l’appareil réseau.</span><span class="sxs-lookup"><span data-stu-id="96383-108">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="96383-109">La méthode **Send** supprime les octets dans la mémoire tampon et les met en file d’attente dans l’interface réseau pour l’envoi à l’appareil réseau.</span><span class="sxs-lookup"><span data-stu-id="96383-109">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="96383-110">L’interface réseau peut ne pas envoyer les données immédiatement, mais les envoyer plus tard, dès que la connexion sera fermée normalement avec la méthode <xref:System.Net.Sockets.Socket.Shutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="96383-110">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="96383-111">Pour recevoir les données d’un appareil réseau, passez une mémoire tampon à l’une des méthodes de réception de données de la classe **Socket** (<xref:System.Net.Sockets.Socket.Receive%2A> et <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="96383-111">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="96383-112">Les sockets synchrones interrompent l’exécution de l’application jusqu’à la réception des octets du réseau ou la fermeture du socket.</span><span class="sxs-lookup"><span data-stu-id="96383-112">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="96383-113">L’exemple suivant reçoit les données du réseau, puis les affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="96383-113">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="96383-114">L’exemple suppose que les données provenant du réseau sont encodées en texte ASCII.</span><span class="sxs-lookup"><span data-stu-id="96383-114">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="96383-115">La méthode **Receive** retourne le nombre d’octets reçus du réseau.</span><span class="sxs-lookup"><span data-stu-id="96383-115">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 <span data-ttu-id="96383-116">Quand le socket n’est plus nécessaire, vous devez le libérer en appelant la méthode <xref:System.Net.Sockets.Socket.Shutdown%2A>, puis la méthode **Close**.</span><span class="sxs-lookup"><span data-stu-id="96383-116">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="96383-117">L’exemple suivant libère un **Socket**.</span><span class="sxs-lookup"><span data-stu-id="96383-117">The following example releases a **Socket**.</span></span> <span data-ttu-id="96383-118">L’énumération <xref:System.Net.Sockets.SocketShutdown> définit les constantes qui indiquent si le socket doit être fermé pour l’envoi et/ou la réception des données.</span><span class="sxs-lookup"><span data-stu-id="96383-118">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="96383-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96383-119">See also</span></span>

- [<span data-ttu-id="96383-120">Utilisation d’un socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="96383-120">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="96383-121">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="96383-121">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="96383-122">Exemple de socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="96383-122">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
