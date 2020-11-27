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
ms.openlocfilehash: 305feaa71304bef749f999a078b0b5f4fa7be3cc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278152"
---
# <a name="using-a-synchronous-server-socket"></a>Utilisation d’un socket serveur synchrone

Les sockets serveur synchrones interrompent l’exécution de l’application jusqu’à la réception d’une demande de connexion sur le socket. Les sockets serveur synchrones ne sont pas appropriés pour les applications dont l’exécution nécessite une utilisation intensive du réseau, mais ils peuvent être utiles pour les applications réseau simples.  
  
 Après qu’un <xref:System.Net.Sockets.Socket> a été défini pour écouter un point de terminaison à l’aide des méthodes <xref:System.Net.Sockets.Socket.Bind%2A> et <xref:System.Net.Sockets.Socket.Listen%2A>, il est prêt à accepter les demandes de connexion entrantes à l’aide de la méthode <xref:System.Net.Sockets.Socket.Accept%2A>. L’exécution de l’application est interrompue jusqu’à la réception d’une demande de connexion après l’appel de la méthode **Accept**.  
  
 Après la réception d’une demande de connexion, **Accept** retourne une nouvelle instance **Socket** qui est associée au client qui se connecte. L’exemple suivant lit les données reçues du client, les affiche sur la console et les renvoie au client. Le **Socket** ne spécifie aucun protocole de messagerie, donc la chaîne « \<EOF> » marque la fin des données du message. L’exemple suppose qu’un **Socket** nommé `listener` a été initialisé et associé à un point de terminaison.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d’un socket serveur asynchrone](using-an-asynchronous-server-socket.md)
- [Exemple de socket serveur synchrone](synchronous-server-socket-example.md)
- [écoute avec des sockets](listening-with-sockets.md)
