---
title: Utilisation d’un socket serveur synchrone
description: Cet exemple montre un socket serveur synchrone dans .NET Framework, qui interrompt une application jusqu’à ce qu’une demande de connexion soit reçue sur le Socket.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
ms.openlocfilehash: 9e7d32595f554b32ecc72bbb1f1a469ad5935467
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502052"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="63acd-103">Utilisation d’un socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="63acd-103">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="63acd-104">Les sockets serveur synchrones interrompent l’exécution de l’application jusqu’à la réception d’une demande de connexion sur le socket.</span><span class="sxs-lookup"><span data-stu-id="63acd-104">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="63acd-105">Les sockets serveur synchrones ne sont pas appropriés pour les applications dont l’exécution nécessite une utilisation intensive du réseau, mais ils peuvent être utiles pour les applications réseau simples.</span><span class="sxs-lookup"><span data-stu-id="63acd-105">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="63acd-106">Après qu’un <xref:System.Net.Sockets.Socket> a été défini pour écouter un point de terminaison à l’aide des méthodes <xref:System.Net.Sockets.Socket.Bind%2A> et <xref:System.Net.Sockets.Socket.Listen%2A>, il est prêt à accepter les demandes de connexion entrantes à l’aide de la méthode <xref:System.Net.Sockets.Socket.Accept%2A>.</span><span class="sxs-lookup"><span data-stu-id="63acd-106">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="63acd-107">L’exécution de l’application est interrompue jusqu’à la réception d’une demande de connexion après l’appel de la méthode **Accept**.</span><span class="sxs-lookup"><span data-stu-id="63acd-107">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="63acd-108">Après la réception d’une demande de connexion, **Accept** retourne une nouvelle instance **Socket** qui est associée au client qui se connecte.</span><span class="sxs-lookup"><span data-stu-id="63acd-108">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="63acd-109">L’exemple suivant lit les données reçues du client, les affiche sur la console et les renvoie au client.</span><span class="sxs-lookup"><span data-stu-id="63acd-109">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="63acd-110">Le **Socket** ne spécifie aucun protocole de messagerie, donc la chaîne « \<EOF> » marque la fin des données du message.</span><span class="sxs-lookup"><span data-stu-id="63acd-110">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="63acd-111">L’exemple suppose qu’un **Socket** nommé `listener` a été initialisé et associé à un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="63acd-111">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="63acd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63acd-112">See also</span></span>

- [<span data-ttu-id="63acd-113">Utilisation d’un socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="63acd-113">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="63acd-114">Exemple de socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="63acd-114">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="63acd-115">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="63acd-115">Listening with Sockets</span></span>](listening-with-sockets.md)
