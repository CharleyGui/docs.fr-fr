---
title: Utilisation des services TCP
description: La classe TcpClient extrait les détails pour créer un socket pour demander et recevoir des données à l’aide du protocole TCP. Utilisez .NET Framework la gestion de flux pour lire et écrire des données.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: 329701e8f11ca7f87c40ee8b2cc6a337435242b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501961"
---
# <a name="using-tcp-services"></a><span data-ttu-id="a1c5a-104">Utilisation des services TCP</span><span class="sxs-lookup"><span data-stu-id="a1c5a-104">Using TCP Services</span></span>

<span data-ttu-id="a1c5a-105">La classe <xref:System.Net.Sockets.TcpClient> demande des données d’une ressource Internet à l’aide de TCP.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-105">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="a1c5a-106">Les méthodes et propriétés de **TcpClient** assurent l’abstraction des informations nécessaires pour créer un <xref:System.Net.Sockets.Socket> permettant l’envoi et la réception de données avec le protocole TCP.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-106">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="a1c5a-107">La connexion à l’appareil distant étant représentée sous forme de flux, les données peuvent être lues et écrites à l’aide des techniques de gestion des flux de données de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-107">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="a1c5a-108">Le protocole TCP établit une connexion à un point de terminaison distant, puis il utilise cette connexion pour envoyer et recevoir des paquets de données.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-108">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="a1c5a-109">TCP est chargé de s’assurer que les paquets de données sont envoyés au point de terminaison et assemblés dans le bon ordre lors de leur réception.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-109">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="a1c5a-110">Pour établir une connexion TCP, vous devez connaître l’adresse de l’appareil réseau qui héberge le service dont vous avez besoin, ainsi que le numéro de port TCP utilisé par ce service pour communiquer.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-110">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="a1c5a-111">L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants (consultez [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="a1c5a-111">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="a1c5a-112">Les services qui ne figurent pas dans la liste de l’IANA peuvent avoir des numéros de port compris dans la plage 1 024 à 65 535.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-112">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="a1c5a-113">L’exemple suivant illustre la configuration d’un **TcpClient** pour la connexion à un serveur de temps sur le port TCP 13 :</span><span class="sxs-lookup"><span data-stu-id="a1c5a-113">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeClient
    Private const portNum As Integer = 13
    Private const hostName As String = "host.contoso.com"

    ' Entry point  that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Try
            Dim client As New TcpClient(hostName, portNum)

            Dim ns As NetworkStream = client.GetStream()

            Dim bytes(1024) As Byte
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)

            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))

        Catch e As Exception
            Console.WriteLine(e.ToString())
        End Try

        client.Close()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="a1c5a-114"><xref:System.Net.Sockets.TcpListener>permet de surveiller un port TCP pour les demandes entrantes, puis de créer un **Socket** ou un **TcpClient** qui gère la connexion au client.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-114"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="a1c5a-115">La méthode <xref:System.Net.Sockets.TcpListener.Start%2A> active l’écoute sur le port et la méthode <xref:System.Net.Sockets.TcpListener.Stop%2A> la désactive.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-115">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="a1c5a-116">La méthode <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> accepte les demandes de connexion entrantes et crée un **TcpClient** qui gère la demande. La méthode <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> accepte les demandes de connexion entrantes et crée un **Socket** pour gérer la demande.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-116">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="a1c5a-117">L’exemple suivant montre comment créer un serveur de temps réseau en utilisant un **TcpListener** pour surveiller le port TCP 13.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-117">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="a1c5a-118">Quand une demande de connexion entrante est acceptée, le serveur de temps répond en retournant la date et l’heure actuelles du serveur hôte.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-118">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

        listener.Start()

        While Not done
            Console.Write("Waiting for connection...")
            Dim client As TcpClient = listener.AcceptTcpClient()

            Console.WriteLine("Connection accepted.")
            Dim ns As NetworkStream = client.GetStream()

            Dim byteTime As Byte() = _
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())

            Try
                ns.Write(byteTime, 0, byteTime.Length)
                ns.Close()
                client.Close()
            Catch e As Exception
                Console.WriteLine(e.ToString())
            End Try
        End While

        listener.Stop()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
