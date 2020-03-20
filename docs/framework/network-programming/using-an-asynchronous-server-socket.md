---
title: Utilisation d’un socket serveur asynchrone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 467804e685d800643c421ed1aad040a842b42886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180635"
---
# <a name="using-an-asynchronous-server-socket"></a>Utilisation d’un socket serveur asynchrone
Les sockets serveur asynchrones utilisent le modèle de programmation asynchrone de .NET Framework pour traiter les demandes de service réseau. La classe <xref:System.Net.Sockets.Socket> respecte la convention de nommage standard de .NET Framework pour les méthodes asynchrones. Par exemple, la méthode synchrone <xref:System.Net.Sockets.Socket.Accept%2A> correspond aux méthodes asynchrones <xref:System.Net.Sockets.Socket.BeginAccept%2A> et <xref:System.Net.Sockets.Socket.EndAccept%2A>.  
  
 Un socket serveur asynchrone nécessite une méthode pour commencer à accepter les demandes de connexion du réseau, une méthode de rappel pour gérer les demandes de connexion et commencer à recevoir des données du réseau, et une méthode de rappel pour terminer la réception des données. Toutes ces méthodes sont décrites plus loin dans cette section.  
  
 Dans l’exemple suivant, pour commencer à accepter les demandes de connexion du réseau, la méthode `StartListening` initialise le **Socket**, puis elle utilise la méthode **BeginAccept** pour commencer à accepter les nouvelles connexions. La méthode de rappel d’acceptation est appelée quand une nouvelle demande de connexion est reçue sur le socket. Elle est chargée d’obtenir l’instance **Socket** qui va gérer la connexion et de passer ce **Socket** au thread qui va traiter la demande. La méthode de rappel d’acceptation implémente le délégué <xref:System.AsyncCallback>. Elle retourne une valeur void et accepte un seul paramètre de type <xref:System.IAsyncResult>. L’exemple suivant illustre une méthode de rappel d’acceptation.  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 La méthode **BeginAccept** accepte deux paramètres, un délégué **AsyncCallback** qui pointe vers la méthode de rappel d’acceptation et un objet qui sert à passer les informations d’état à la méthode de rappel. Dans l’exemple suivant, l’écoute **Socket** est passée à la méthode de rappel via le paramètre d’*état*. Cet exemple crée un délégué **AsyncCallback** et démarre l’acceptation des connexions à partir du réseau.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Les sockets asynchrones utilisent des threads du pool de threads système pour traiter les connexions entrantes. Un thread est chargé d’accepter les connexions, un autre thread de la gestion de chaque connexion entrante et un autre thread de la réception des données provenant de la connexion. Il peut s’agir du même thread, en fonction du thread qui a été assigné par le pool de threads. Dans l’exemple suivant, la classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> interrompt l’exécution du thread principal et signale à ce thread la reprise possible de l’exécution.  
  
 L’exemple suivant montre une méthode asynchrone qui crée un socket TCP/IP asynchrone sur l’ordinateur local et commence à accepter des connexions. Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone`, que la méthode est membre d’une classe nommée `SocketListener` et qu’une méthode de rappel nommée `AcceptCallback` est définie.  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 La méthode de rappel d’acceptation (`AcceptCallback` dans l’exemple précédent) est chargée de signaler au thread d’application principal la reprise possible de l’exécution, d’établir la connexion avec le client et de démarrer la lecture asynchrone des données du client. L’exemple suivant montre la première partie d’une implémentation de la méthode `AcceptCallback`. Cette section de la méthode indique au thread d’application principal qu’il peut reprendre l’exécution et établir la connexion au client. Il suppose l’utilisation d’un **ManualResetEvent** global nommé `allDone`.  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 La lecture des données reçues d’un socket client nécessite l’utilisation d’un objet d’état qui passe les valeurs entre les appels asynchrones. L’exemple suivant implémente un objet d’état pour la réception d’une chaîne à partir du client distant. Il contient des champs pour le socket client, une mémoire tampon pour recevoir les données et un <xref:System.Text.StringBuilder> pour la création de la chaîne de données envoyée par le client. Le fait que ces champs soient placés dans l’objet d’état permet à leurs valeurs d’être conservées entre les appels pour lire les données reçues du socket client.  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 La section de la méthode `AcceptCallback` qui démarre la réception des données à partir du socket client initialise d’abord une instance de la classe `StateObject`, puis appelle la méthode <xref:System.Net.Sockets.Socket.BeginReceive%2A> pour démarrer la lecture asynchrone des données reçues du socket client.  
  
 L’exemple suivant montre la méthode `AcceptCallback` complète. Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone,`, que la classe `StateObject` est définie et que la méthode `ReadCallback` est définie dans une classe nommée `SocketListener`.  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 La dernière méthode à implémenter pour le socket serveur asynchrone est la méthode de rappel de lecture qui retourne les données envoyées par le client. Comme la méthode de rappel d’acceptation, la méthode de rappel de lecture est un délégué **AsyncCallback**. Cette méthode lit un ou plusieurs octets de données provenant du socket client, les stocke dans la mémoire tampon de données, puis appelle de nouveau la méthode **BeginReceive** jusqu’à la fin de la réception des données envoyées par le client. Une fois que l’intégralité du message du client a été lue, la chaîne est affichée sur la console et le socket serveur qui gère la connexion au client est fermé.  
  
 L’exemple suivant implémente la méthode `ReadCallback`. Il suppose que la classe `StateObject` est définie.  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d’un socket serveur synchrone](using-a-synchronous-server-socket.md)
- [Exemple de socket serveur asynchrone](asynchronous-server-socket-example.md)
- [Thread](../../standard/threading/index.md)
- [Écoute avec des sockets](listening-with-sockets.md)
