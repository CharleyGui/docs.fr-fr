---
title: Exemple de socket client synchrone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sockets, code examples
- synchronous client sockets
- sockets, synchronous client sockets
ms.assetid: 2c7d5be7-2221-467c-a839-5744ec4d576d
ms.openlocfilehash: 70c4f26e3b4fc1c3dcb4c34e8858525b7f1660c3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047187"
---
# <a name="synchronous-client-socket-example"></a><span data-ttu-id="d6579-102">Exemple de socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="d6579-102">Synchronous Client Socket Example</span></span>
<span data-ttu-id="d6579-103">L’exemple de programme suivant crée un client qui se connecte à un serveur.</span><span class="sxs-lookup"><span data-stu-id="d6579-103">The following example program creates a client that connects to a server.</span></span> <span data-ttu-id="d6579-104">Le client est créé avec un socket synchrone. L’exécution de l’application cliente est donc suspendue jusqu’à ce que le serveur retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="d6579-104">The client is built with a synchronous socket, so execution of the client application is suspended until the server returns a response.</span></span> <span data-ttu-id="d6579-105">L’application envoie une chaîne au serveur, puis affiche la chaîne retournée par le serveur sur la console.</span><span class="sxs-lookup"><span data-stu-id="d6579-105">The application sends a string to the server and then displays the string returned by the server on the console.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class SynchronousSocketClient  
  
    Public Shared Sub Main()  
        ' Data buffer for incoming data.  
        Dim bytes(1024) As Byte  
  
        ' Connect to a remote device.  
  
        ' Establish the remote endpoint for the socket.  
        ' This example uses port 11000 on the local computer.  
        Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim remoteEP As New IPEndPoint(ipAddress, 11000)  
  
        ' Create a TCP/IP socket.  
        Dim sender As New Socket(ipAddress.AddressFamily, _  
            SocketType.Stream, ProtocolType.Tcp)  
  
        ' Connect the socket to the remote endpoint.  
        sender.Connect(remoteEP)  
  
        Console.WriteLine("Socket connected to {0}", _  
            sender.RemoteEndPoint.ToString())  
  
        ' Encode the data string into a byte array.  
        Dim msg As Byte() = _  
            Encoding.ASCII.GetBytes("This is a test<EOF>")  
  
        ' Send the data through the socket.  
        Dim bytesSent As Integer = sender.Send(msg)  
  
        ' Receive the response from the remote device.  
        Dim bytesRec As Integer = sender.Receive(bytes)  
        Console.WriteLine("Echoed test = {0}", _  
            Encoding.ASCII.GetString(bytes, 0, bytesRec))  
  
        ' Release the socket.  
        sender.Shutdown(SocketShutdown.Both)  
        sender.Close()  
    End Sub  
  
End Class 'SynchronousSocketClient  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class SynchronousSocketClient {  
  
    public static void StartClient() {  
        // Data buffer for incoming data.  
        byte[] bytes = new byte[1024];  
  
        // Connect to a remote device.  
        try {  
            // Establish the remote endpoint for the socket.  
            // This example uses port 11000 on the local computer.  
            IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
            IPAddress ipAddress = ipHostInfo.AddressList[0];  
            IPEndPoint remoteEP = new IPEndPoint(ipAddress,11000);  
  
            // Create a TCP/IP  socket.  
            Socket sender = new Socket(ipAddress.AddressFamily,   
                SocketType.Stream, ProtocolType.Tcp );  
  
            // Connect the socket to the remote endpoint. Catch any errors.  
            try {  
                sender.Connect(remoteEP);  
  
                Console.WriteLine("Socket connected to {0}",  
                    sender.RemoteEndPoint.ToString());  
  
                // Encode the data string into a byte array.  
                byte[] msg = Encoding.ASCII.GetBytes("This is a test<EOF>");  
  
                // Send the data through the socket.  
                int bytesSent = sender.Send(msg);  
  
                // Receive the response from the remote device.  
                int bytesRec = sender.Receive(bytes);  
                Console.WriteLine("Echoed test = {0}",  
                    Encoding.ASCII.GetString(bytes,0,bytesRec));  
  
                // Release the socket.  
                sender.Shutdown(SocketShutdown.Both);  
                sender.Close();  
  
            } catch (ArgumentNullException ane) {  
                Console.WriteLine("ArgumentNullException : {0}",ane.ToString());  
            } catch (SocketException se) {  
                Console.WriteLine("SocketException : {0}",se.ToString());  
            } catch (Exception e) {  
                Console.WriteLine("Unexpected exception : {0}", e.ToString());  
            }  
  
        } catch (Exception e) {  
            Console.WriteLine( e.ToString());  
        }  
    }  
  
    public static int Main(String[] args) {  
        StartClient();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6579-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6579-106">See also</span></span>

- [<span data-ttu-id="d6579-107">Exemple de socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="d6579-107">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="d6579-108">Utilisation d’un socket client synchrone</span><span class="sxs-lookup"><span data-stu-id="d6579-108">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="d6579-109">Exemples de code de socket</span><span class="sxs-lookup"><span data-stu-id="d6579-109">Socket Code Examples</span></span>](socket-code-examples.md)
