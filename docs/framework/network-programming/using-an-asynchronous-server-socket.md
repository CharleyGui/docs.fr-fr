---
title: Utilisation d’un socket serveur asynchrone
description: Cet exemple montre un socket serveur asynchrone. La classe Socket utilise .NET Framework programmation asynchrone pour traiter les demandes de service réseau.
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
ms.openlocfilehash: 6800a1973d9eb65bbb7520f9db7a8f431656c685
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265204"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="8bcfd-104">Utilisation d’un socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="8bcfd-104">Using an Asynchronous Server Socket</span></span>

<span data-ttu-id="8bcfd-105">Les sockets serveur asynchrones utilisent le modèle de programmation asynchrone de .NET Framework pour traiter les demandes de service réseau.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="8bcfd-106">La classe <xref:System.Net.Sockets.Socket> respecte la convention de nommage standard de .NET Framework pour les méthodes asynchrones. Par exemple, la méthode synchrone <xref:System.Net.Sockets.Socket.Accept%2A> correspond aux méthodes asynchrones <xref:System.Net.Sockets.Socket.BeginAccept%2A> et <xref:System.Net.Sockets.Socket.EndAccept%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="8bcfd-107">Un socket serveur asynchrone nécessite une méthode pour commencer à accepter les demandes de connexion du réseau, une méthode de rappel pour gérer les demandes de connexion et commencer à recevoir des données du réseau, et une méthode de rappel pour terminer la réception des données.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="8bcfd-108">Toutes ces méthodes sont décrites plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="8bcfd-109">Dans l’exemple suivant, pour commencer à accepter les demandes de connexion du réseau, la méthode `StartListening` initialise le **Socket**, puis elle utilise la méthode **BeginAccept** pour commencer à accepter les nouvelles connexions.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="8bcfd-110">La méthode de rappel d’acceptation est appelée quand une nouvelle demande de connexion est reçue sur le socket.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="8bcfd-111">Elle est chargée d’obtenir l’instance **Socket** qui va gérer la connexion et de passer ce **Socket** au thread qui va traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="8bcfd-112">La méthode de rappel d’acceptation implémente le délégué <xref:System.AsyncCallback>. Elle retourne une valeur void et accepte un seul paramètre de type <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="8bcfd-113">L’exemple suivant illustre une méthode de rappel d’acceptation.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-113">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="8bcfd-114">La méthode **BeginAccept** accepte deux paramètres, un délégué **AsyncCallback** qui pointe vers la méthode de rappel d’acceptation et un objet qui sert à passer les informations d’état à la méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="8bcfd-115">Dans l’exemple suivant, l’écoute **Socket** est passée à la méthode de rappel via le paramètre d’*état*.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="8bcfd-116">Cet exemple crée un délégué **AsyncCallback** et démarre l’acceptation des connexions à partir du réseau.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="8bcfd-117">Les sockets asynchrones utilisent des threads du pool de threads système pour traiter les connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="8bcfd-118">Un thread est chargé d’accepter les connexions, un autre thread de la gestion de chaque connexion entrante et un autre thread de la réception des données provenant de la connexion.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="8bcfd-119">Il peut s’agir du même thread, en fonction du thread qui a été assigné par le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="8bcfd-120">Dans l’exemple suivant, la classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> interrompt l’exécution du thread principal et signale à ce thread la reprise possible de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="8bcfd-121">L’exemple suivant montre une méthode asynchrone qui crée un socket TCP/IP asynchrone sur l’ordinateur local et commence à accepter des connexions.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="8bcfd-122">Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone`, que la méthode est membre d’une classe nommée `SocketListener` et qu’une méthode de rappel nommée `AcceptCallback` est définie.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="8bcfd-123">La méthode de rappel d’acceptation (`AcceptCallback` dans l’exemple précédent) est chargée de signaler au thread d’application principal la reprise possible de l’exécution, d’établir la connexion avec le client et de démarrer la lecture asynchrone des données du client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="8bcfd-124">L’exemple suivant montre la première partie d’une implémentation de la méthode `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="8bcfd-125">Cette section de la méthode indique au thread d’application principal qu’il peut reprendre l’exécution et établir la connexion au client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="8bcfd-126">Il suppose l’utilisation d’un **ManualResetEvent** global nommé `allDone`.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="8bcfd-127">La lecture des données reçues d’un socket client nécessite l’utilisation d’un objet d’état qui passe les valeurs entre les appels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="8bcfd-128">L’exemple suivant implémente un objet d’état pour la réception d’une chaîne à partir du client distant.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="8bcfd-129">Il contient des champs pour le socket client, une mémoire tampon pour recevoir les données et un <xref:System.Text.StringBuilder> pour la création de la chaîne de données envoyée par le client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="8bcfd-130">Le fait que ces champs soient placés dans l’objet d’état permet à leurs valeurs d’être conservées entre les appels pour lire les données reçues du socket client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="8bcfd-131">La section de la méthode `AcceptCallback` qui démarre la réception des données à partir du socket client initialise d’abord une instance de la classe `StateObject`, puis appelle la méthode <xref:System.Net.Sockets.Socket.BeginReceive%2A> pour démarrer la lecture asynchrone des données reçues du socket client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="8bcfd-132">L’exemple suivant montre la méthode `AcceptCallback` complète.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="8bcfd-133">Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone,`, que la classe `StateObject` est définie et que la méthode `ReadCallback` est définie dans une classe nommée `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="8bcfd-134">La dernière méthode à implémenter pour le socket serveur asynchrone est la méthode de rappel de lecture qui retourne les données envoyées par le client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="8bcfd-135">Comme la méthode de rappel d’acceptation, la méthode de rappel de lecture est un délégué **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="8bcfd-136">Cette méthode lit un ou plusieurs octets de données provenant du socket client, les stocke dans la mémoire tampon de données, puis appelle de nouveau la méthode **BeginReceive** jusqu’à la fin de la réception des données envoyées par le client.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="8bcfd-137">Une fois que l’intégralité du message du client a été lue, la chaîne est affichée sur la console et le socket serveur qui gère la connexion au client est fermé.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="8bcfd-138">L’exemple suivant implémente la méthode `ReadCallback`.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="8bcfd-139">Il suppose que la classe `StateObject` est définie.</span><span class="sxs-lookup"><span data-stu-id="8bcfd-139">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8bcfd-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bcfd-140">See also</span></span>

- [<span data-ttu-id="8bcfd-141">Utilisation d’un socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="8bcfd-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="8bcfd-142">Exemple de sockets serveur asynchrones</span><span class="sxs-lookup"><span data-stu-id="8bcfd-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="8bcfd-143">Thread</span><span class="sxs-lookup"><span data-stu-id="8bcfd-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="8bcfd-144">écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="8bcfd-144">Listening with Sockets</span></span>](listening-with-sockets.md)
