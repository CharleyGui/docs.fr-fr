---
title: Exemple de socket client asynchrone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous client sockets
- sockets, code examples
- sockets, asynchronous client sockets
ms.assetid: d4ac53a0-b50b-4232-9726-d47d25fcc38a
ms.openlocfilehash: 9cf8ffff1b219614cd57b56af48d72c03ac63dda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180926"
---
# <a name="asynchronous-client-socket-example"></a><span data-ttu-id="cf7f8-102">Exemple de socket client asynchrone</span><span class="sxs-lookup"><span data-stu-id="cf7f8-102">Asynchronous Client Socket Example</span></span>
<span data-ttu-id="cf7f8-103">L’exemple de programme suivant crée un client qui se connecte à un serveur.</span><span class="sxs-lookup"><span data-stu-id="cf7f8-103">The following example program creates a client that connects to a server.</span></span> <span data-ttu-id="cf7f8-104">Le client est créé avec un socket asynchrone. L’exécution de l’application cliente n’est donc pas suspendue pendant que le serveur retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="cf7f8-104">The client is built with an asynchronous socket, so execution of the client application is not suspended while the server returns a response.</span></span> <span data-ttu-id="cf7f8-105">L’application envoie une chaîne au serveur, puis affiche la chaîne retournée par le serveur sur la console.</span><span class="sxs-lookup"><span data-stu-id="cf7f8-105">The application sends a string to the server and then displays the string returned by the server on the console.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.Text  
  
' State object for receiving data from remote device.  
  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing  
    ' Size of receive buffer.  
    Public Const BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(BufferSize) As Byte  
    ' Received data string.  
    Public sb As New StringBuilder  
End Class 'StateObject  
  
Public Class AsynchronousClient  
    ' The port number for the remote device.  
    Private Const port As Integer = 11000  
  
    ' ManualResetEvent instances signal completion.  
    Private Shared connectDone As New ManualResetEvent(False)  
    Private Shared sendDone As New ManualResetEvent(False)  
    Private Shared receiveDone As New ManualResetEvent(False)  
  
    ' The response from the remote device.  
    Private Shared response As String = String.Empty  
  
    Public Shared Sub Main()  
        ' Establish the remote endpoint for the socket.  
        ' For this example use local machine.  
        Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim remoteEP As New IPEndPoint(ipAddress, port)  
  
        ' Create a TCP/IP socket.  
        Dim client As New Socket(ipAddress.AddressFamily, SocketType.Stream, ProtocolType.Tcp)  
  
        ' Connect to the remote endpoint.  
        client.BeginConnect(remoteEP, New AsyncCallback(AddressOf ConnectCallback), client)  
  
        ' Wait for connect.  
        connectDone.WaitOne()  
  
        ' Send test data to the remote device.  
        Send(client, "This is a test<EOF>")  
        sendDone.WaitOne()  
  
        ' Receive the response from the remote device.  
        Receive(client)  
        receiveDone.WaitOne()  
  
        ' Write the response to the console.  
        Console.WriteLine("Response received : {0}", response)  
  
        ' Release the socket.  
        client.Shutdown(SocketShutdown.Both)  
        client.Close()  
    End Sub 'Main  
  
    Private Shared Sub ConnectCallback(ByVal ar As IAsyncResult)  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    End Sub 'ConnectCallback  
  
    Private Shared Sub Receive(ByVal client As Socket)  
  
        ' Create the state object.  
        Dim state As New StateObject  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0, New AsyncCallback(AddressOf ReceiveCallback), state)  
    End Sub 'Receive  
  
    Private Shared Sub ReceiveCallback(ByVal ar As IAsyncResult)  
  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, bytesRead))  
  
            ' Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0, New AsyncCallback(AddressOf ReceiveCallback), state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    End Sub 'ReceiveCallback  
  
    Private Shared Sub Send(ByVal client As Socket, ByVal data As String)  
        ' Convert the string data to byte data using ASCII encoding.  
        Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
        ' Begin sending the data to the remote device.  
        client.BeginSend(byteData, 0, byteData.Length, 0, New AsyncCallback(AddressOf SendCallback), client)  
    End Sub 'Send  
  
    Private Shared Sub SendCallback(ByVal ar As IAsyncResult)  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    End Sub 'SendCallback  
End Class 'AsynchronousClient  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Threading;  
using System.Text;  
  
// State object for receiving data from remote device.  
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
  
public class AsynchronousClient {  
    // The port number for the remote device.  
    private const int port = 11000;  
  
    // ManualResetEvent instances signal completion.  
    private static ManualResetEvent connectDone =
        new ManualResetEvent(false);  
    private static ManualResetEvent sendDone =
        new ManualResetEvent(false);  
    private static ManualResetEvent receiveDone =
        new ManualResetEvent(false);  
  
    // The response from the remote device.  
    private static String response = String.Empty;  
  
    private static void StartClient() {  
        // Connect to a remote device.  
        try {  
            // Establish the remote endpoint for the socket.  
            // The name of the
            // remote device is "host.contoso.com".  
            IPHostEntry ipHostInfo = Dns.GetHostEntry("host.contoso.com");  
            IPAddress ipAddress = ipHostInfo.AddressList[0];  
            IPEndPoint remoteEP = new IPEndPoint(ipAddress, port);  
  
            // Create a TCP/IP socket.  
            Socket client = new Socket(ipAddress.AddressFamily,  
                SocketType.Stream, ProtocolType.Tcp);  
  
            // Connect to the remote endpoint.  
            client.BeginConnect( remoteEP,
                new AsyncCallback(ConnectCallback), client);  
            connectDone.WaitOne();  
  
            // Send test data to the remote device.  
            Send(client,"This is a test<EOF>");  
            sendDone.WaitOne();  
  
            // Receive the response from the remote device.  
            Receive(client);  
            receiveDone.WaitOne();  
  
            // Write the response to the console.  
            Console.WriteLine("Response received : {0}", response);  
  
            // Release the socket.  
            client.Shutdown(SocketShutdown.Both);  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
    }  
  
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
  
                // Get the rest of the data.  
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
  
    private static void Send(Socket client, String data) {  
        // Convert the string data to byte data using ASCII encoding.  
        byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
        // Begin sending the data to the remote device.  
        client.BeginSend(byteData, 0, byteData.Length, 0,  
            new AsyncCallback(SendCallback), client);  
    }  
  
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
  
    public static int Main(String[] args) {  
        StartClient();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf7f8-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf7f8-106">See also</span></span>

- [<span data-ttu-id="cf7f8-107">Exemple de socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="cf7f8-107">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="cf7f8-108">Utilisation d’un socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="cf7f8-108">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="cf7f8-109">Exemples de code de socket</span><span class="sxs-lookup"><span data-stu-id="cf7f8-109">Socket Code Examples</span></span>](socket-code-examples.md)
