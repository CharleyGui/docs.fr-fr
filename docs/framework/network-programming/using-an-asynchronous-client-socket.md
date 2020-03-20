---
title: Utilisation d’un socket client asynchrone
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
ms.openlocfilehash: 748745ca6799005dccdbfcbcc37a8c2a38f2a88e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180649"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="60e93-102">Utilisation d’un socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="60e93-102">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="60e93-103">Un socket client asynchrone n’interrompt pas l’exécution de l’application durant les opérations réseau.</span><span class="sxs-lookup"><span data-stu-id="60e93-103">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="60e93-104">Au lieu de cela, il utilise le modèle de programmation asynchrone standard de .NET Framework pour traiter la connexion réseau sur un thread pendant que l’application continue de s’exécuter sur le thread d’origine.</span><span class="sxs-lookup"><span data-stu-id="60e93-104">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="60e93-105">Les sockets asynchrones sont appropriés pour les applications qui utilisent le réseau de manière intensive ou qui ne peuvent pas être interrompues en attendant la fin des opérations réseau.</span><span class="sxs-lookup"><span data-stu-id="60e93-105">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="60e93-106">La classe <xref:System.Net.Sockets.Socket> respecte la convention de nommage du .NET Framework pour les méthodes asynchrones. Par exemple, la méthode synchrone <xref:System.Net.Sockets.Socket.Receive%2A> correspond aux méthodes asynchrones <xref:System.Net.Sockets.Socket.BeginReceive%2A> et <xref:System.Net.Sockets.Socket.EndReceive%2A>.</span><span class="sxs-lookup"><span data-stu-id="60e93-106">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="60e93-107">Les opérations asynchrones nécessitent une méthode de rappel pour retourner le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="60e93-107">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="60e93-108">Si votre application n’a pas besoin de connaître le résultat, la méthode de rappel n’est pas utile.</span><span class="sxs-lookup"><span data-stu-id="60e93-108">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="60e93-109">L’exemple de code dans cette section montre comment utiliser une méthode pour démarrer une connexion à un appareil réseau, une méthode de rappel pour terminer la connexion, une méthode pour démarrer l’envoi des données, une méthode de rappel pour terminer l’envoi, une méthode pour démarrer la réception des données et une méthode de rappel pour terminer la réception des données.</span><span class="sxs-lookup"><span data-stu-id="60e93-109">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="60e93-110">Les sockets asynchrones utilisent plusieurs threads du pool de threads système pour traiter les connexions réseau.</span><span class="sxs-lookup"><span data-stu-id="60e93-110">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="60e93-111">Un seul thread est chargé du démarrage de l’envoi ou de la réception des données. Les autres threads terminent la connexion à l’appareil réseau et l’envoi ou la réception des données.</span><span class="sxs-lookup"><span data-stu-id="60e93-111">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="60e93-112">Dans les exemples suivants, les instances de la classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sont utilisées pour interrompre l’exécution du thread principal et signaler à ce thread la reprise possible de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="60e93-112">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="60e93-113">Dans l’exemple suivant, pour connecter un socket asynchrone à un appareil réseau, la méthode `Connect` initialise un **Socket**, puis appelle la méthode <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType>, en passant un point de terminaison distant qui représente le périphérique réseau, la méthode de rappel de connexion, ainsi qu’un objet d’état (le **Socket** client) qui sert à passer les informations d’état entre les appels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="60e93-113">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="60e93-114">L’exemple implémente la méthode `Connect` qui connecte le **Socket** spécifié au point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="60e93-114">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="60e93-115">Il suppose l’utilisation d’un **ManualResetEvent** global nommé `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="60e93-115">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="60e93-116">La méthode de rappel de connexion `ConnectCallback` implémente le délégué <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="60e93-116">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="60e93-117">Elle démarre une connexion à l’appareil distant quand celui-ci est disponible et signale au thread d’application que la connexion est établie en définissant le **ManualResetEvent** `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="60e93-117">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="60e93-118">Le code suivant implémente la méthode `ConnectCallback`.</span><span class="sxs-lookup"><span data-stu-id="60e93-118">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="60e93-119">L’exemple de méthode `Send` encode la chaîne de données spécifiée au format ASCII, puis l’envoie de façon asynchrone à l’appareil réseau représenté par le socket spécifié.</span><span class="sxs-lookup"><span data-stu-id="60e93-119">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="60e93-120">L’exemple suivant implémente la méthode `Send`.</span><span class="sxs-lookup"><span data-stu-id="60e93-120">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="60e93-121">La méthode de rappel d’envoi `SendCallback` implémente le délégué <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="60e93-121">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="60e93-122">Elle envoie les données dès que l’appareil réseau est prêt à les recevoir.</span><span class="sxs-lookup"><span data-stu-id="60e93-122">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="60e93-123">L’exemple suivant illustre l’implémentation de la méthode `SendCallback`.</span><span class="sxs-lookup"><span data-stu-id="60e93-123">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="60e93-124">Il suppose l’utilisation d’un **ManualResetEvent** global nommé `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="60e93-124">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="60e93-125">La lecture des données reçues d’un socket client nécessite l’utilisation d’un objet d’état qui passe les valeurs entre les appels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="60e93-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="60e93-126">La classe suivante est un exemple d’objet d’état permettant de recevoir des données d’un socket client.</span><span class="sxs-lookup"><span data-stu-id="60e93-126">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="60e93-127">Cet objet contient des champs pour le socket client, une mémoire tampon pour les données reçues et un <xref:System.Text.StringBuilder> pour stocker la chaîne de données entrante.</span><span class="sxs-lookup"><span data-stu-id="60e93-127">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="60e93-128">Le fait que ces champs soient placés dans l’objet d’état permet à leurs valeurs d’être conservées entre les appels pour lire les données reçues du socket client.</span><span class="sxs-lookup"><span data-stu-id="60e93-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="60e93-129">L’exemple de méthode `Receive` définit l’objet d’état, puis appelle la méthode **BeginReceive** pour lire les données du socket client de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="60e93-129">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="60e93-130">L’exemple suivant implémente la méthode `Receive`.</span><span class="sxs-lookup"><span data-stu-id="60e93-130">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="60e93-131">La méthode de rappel de réception `ReceiveCallback` implémente le délégué **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="60e93-131">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="60e93-132">Elle reçoit les données de l’appareil réseau et crée une chaîne de message.</span><span class="sxs-lookup"><span data-stu-id="60e93-132">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="60e93-133">Elle lit un ou plusieurs octets de données provenant du réseau, les stocke dans la mémoire tampon de données, puis appelle de nouveau la méthode **BeginReceive** jusqu’à la fin de la réception des données envoyées par le client.</span><span class="sxs-lookup"><span data-stu-id="60e93-133">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="60e93-134">Une fois qu’elle a lu toutes les données reçues du client, la méthode `ReceiveCallback` signale au thread d’application que l’opération est terminée en définissant le **ManualResetEvent** `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="60e93-134">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="60e93-135">L’exemple de code suivant implémente la méthode `ReceiveCallback`.</span><span class="sxs-lookup"><span data-stu-id="60e93-135">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="60e93-136">Il suppose l’utilisation d’une chaîne globale nommée `response` qui contient la chaîne reçue et d’un **ManualResetEvent** global nommé `receiveDone`.</span><span class="sxs-lookup"><span data-stu-id="60e93-136">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="60e93-137">Le serveur doit arrêter le socket client normalement pour terminer la session réseau.</span><span class="sxs-lookup"><span data-stu-id="60e93-137">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60e93-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60e93-138">See also</span></span>

- [<span data-ttu-id="60e93-139">Utilisation d’un socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="60e93-139">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="60e93-140">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="60e93-140">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="60e93-141">Exemple de socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="60e93-141">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
