---
title: Utilisation d’un socket client asynchrone
description: Cet exemple montre un socket client asynchrone. .NET Framework la programmation asynchrone permet à une application de continuer à s’exécuter pendant le traitement d’une connexion.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: af5379533e51e7488d673359dc24268c6329c082
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265217"
---
# <a name="using-an-asynchronous-client-socket"></a>Utilisation d’un socket client asynchrone

Un socket client asynchrone n’interrompt pas l’exécution de l’application durant les opérations réseau. Au lieu de cela, il utilise le modèle de programmation asynchrone standard de .NET Framework pour traiter la connexion réseau sur un thread pendant que l’application continue de s’exécuter sur le thread d’origine. Les sockets asynchrones sont appropriés pour les applications qui utilisent le réseau de manière intensive ou qui ne peuvent pas être interrompues en attendant la fin des opérations réseau.  
  
 La classe <xref:System.Net.Sockets.Socket> respecte la convention de nommage du .NET Framework pour les méthodes asynchrones. Par exemple, la méthode synchrone <xref:System.Net.Sockets.Socket.Receive%2A> correspond aux méthodes asynchrones <xref:System.Net.Sockets.Socket.BeginReceive%2A> et <xref:System.Net.Sockets.Socket.EndReceive%2A>.  
  
 Les opérations asynchrones nécessitent une méthode de rappel pour retourner le résultat de l’opération. Si votre application n’a pas besoin de connaître le résultat, la méthode de rappel n’est pas utile. L’exemple de code dans cette section montre comment utiliser une méthode pour démarrer une connexion à un appareil réseau, une méthode de rappel pour terminer la connexion, une méthode pour démarrer l’envoi des données, une méthode de rappel pour terminer l’envoi, une méthode pour démarrer la réception des données et une méthode de rappel pour terminer la réception des données.  
  
 Les sockets asynchrones utilisent plusieurs threads du pool de threads système pour traiter les connexions réseau. Un seul thread est chargé du démarrage de l’envoi ou de la réception des données. Les autres threads terminent la connexion à l’appareil réseau et l’envoi ou la réception des données. Dans les exemples suivants, les instances de la classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sont utilisées pour interrompre l’exécution du thread principal et signaler à ce thread la reprise possible de l’exécution.  
  
 Dans l’exemple suivant, pour connecter un socket asynchrone à un appareil réseau, la méthode `Connect` initialise un **Socket**, puis appelle la méthode <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType>, en passant un point de terminaison distant qui représente le périphérique réseau, la méthode de rappel de connexion, ainsi qu’un objet d’état (le **Socket** client) qui sert à passer les informations d’état entre les appels asynchrones. L’exemple implémente la méthode `Connect` qui connecte le **Socket** spécifié au point de terminaison spécifié. Il suppose l’utilisation d’un **ManualResetEvent** global nommé `connectDone`.  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 La méthode de rappel de connexion `ConnectCallback` implémente le délégué <xref:System.AsyncCallback>. Elle démarre une connexion à l’appareil distant quand celui-ci est disponible et signale au thread d’application que la connexion est établie en définissant le **ManualResetEvent** `connectDone`. Le code suivant implémente la méthode `ConnectCallback`.  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 L’exemple de méthode `Send` encode la chaîne de données spécifiée au format ASCII, puis l’envoie de façon asynchrone à l’appareil réseau représenté par le socket spécifié. L’exemple suivant implémente la méthode `Send`.  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 La méthode de rappel d’envoi `SendCallback` implémente le délégué <xref:System.AsyncCallback>. Elle envoie les données dès que l’appareil réseau est prêt à les recevoir. L’exemple suivant illustre l’implémentation de la méthode `SendCallback`. Il suppose l’utilisation d’un **ManualResetEvent** global nommé `sendDone`.  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 La lecture des données reçues d’un socket client nécessite l’utilisation d’un objet d’état qui passe les valeurs entre les appels asynchrones. La classe suivante est un exemple d’objet d’état permettant de recevoir des données d’un socket client. Cet objet contient des champs pour le socket client, une mémoire tampon pour les données reçues et un <xref:System.Text.StringBuilder> pour stocker la chaîne de données entrante. Le fait que ces champs soient placés dans l’objet d’état permet à leurs valeurs d’être conservées entre les appels pour lire les données reçues du socket client.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 L’exemple de méthode `Receive` définit l’objet d’état, puis appelle la méthode **BeginReceive** pour lire les données du socket client de manière asynchrone. L’exemple suivant implémente la méthode `Receive`.  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 La méthode de rappel de réception `ReceiveCallback` implémente le délégué **AsyncCallback**. Elle reçoit les données de l’appareil réseau et crée une chaîne de message. Elle lit un ou plusieurs octets de données provenant du réseau, les stocke dans la mémoire tampon de données, puis appelle de nouveau la méthode **BeginReceive** jusqu’à la fin de la réception des données envoyées par le client. Une fois qu’elle a lu toutes les données reçues du client, la méthode `ReceiveCallback` signale au thread d’application que l’opération est terminée en définissant le **ManualResetEvent** `sendDone`.  
  
 L’exemple de code suivant implémente la méthode `ReceiveCallback`. Il suppose l’utilisation d’une chaîne globale nommée `response` qui contient la chaîne reçue et d’un **ManualResetEvent** global nommé `receiveDone`. Le serveur doit arrêter le socket client normalement pour terminer la session réseau.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d’un socket client synchrone](using-a-synchronous-client-socket.md)
- [écoute avec des sockets](listening-with-sockets.md)
- [Exemple de socket client asynchrone](asynchronous-client-socket-example.md)
