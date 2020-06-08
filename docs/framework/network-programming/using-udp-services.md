---
title: Utilisation des services UDP
description: La classe UdpClient extrait les détails pour créer un socket pour demander et recevoir des données à l’aide du protocole UDP dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
ms.openlocfilehash: 4c2e88492f737800151d30097719d7d011054a5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501948"
---
# <a name="use-udp-services"></a><span data-ttu-id="0d8b6-103">Utiliser les services UDP</span><span class="sxs-lookup"><span data-stu-id="0d8b6-103">Use UDP services</span></span>

<span data-ttu-id="0d8b6-104">La classe <xref:System.Net.Sockets.UdpClient> communique avec les services réseau à l’aide d’UDP.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-104">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="0d8b6-105">Les méthodes et propriétés de la classe <xref:System.Net.Sockets.UdpClient> assurent l’abstraction des informations nécessaires pour créer un <xref:System.Net.Sockets.Socket> permettant l’envoi et la réception de données avec le protocole UDP.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-105">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="0d8b6-106">UDP (User Datagram Protocol) est un protocole simple qui essaie de fournir les données à un hôte distant le plus efficacement possible.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-106">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="0d8b6-107">Toutefois, comme le protocole UDP est un protocole non connecté, les datagrammes UDP envoyés au point de terminaison distant ne sont pas assurés d’arriver, ou d’arriver dans la même séquence que celle dans laquelle ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-107">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="0d8b6-108">Les applications qui utilisent le protocole UDP doivent être en mesure de gérer les datagrammes manquants, en double et hors séquence.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-108">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="0d8b6-109">Pour envoyer un datagramme avec une connexion UDP, vous devez connaître l’adresse de l’appareil réseau qui héberge le service dont vous avez besoin, ainsi que le numéro de port UDP utilisé par ce service pour communiquer.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-109">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="0d8b6-110">L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants (voir le [nom du service et le Registre du numéro de port du protocole de transport](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="0d8b6-110">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="0d8b6-111">Les services qui ne sont pas dans la liste IANA peuvent avoir des numéros de port compris dans la plage 1 024 à 65 535.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-111">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="0d8b6-112">Des adresses réseau spéciales sont utilisées pour prendre en charge les messages de diffusion UDP sur les réseaux IP.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-112">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="0d8b6-113">L’exemple suivant utilise la famille d’adresses IP version 4 pour Internet.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-113">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="0d8b6-114">Les adresses IP version 4 spécifient les adresses réseau sur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-114">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="0d8b6-115">Pour les adresses de classe C utilisant un masque de sous-réseau 255.255.255.0, ces bits sont divisés en quatre octets.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-115">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="0d8b6-116">Au format décimal, les quatre octets s’écrivent selon la notation connue de quatre nombres séparés par un point (par exemple, 192.168.100.2).</span><span class="sxs-lookup"><span data-stu-id="0d8b6-116">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="0d8b6-117">Les deux premiers octets (192.168 dans cet exemple) forment le numéro du réseau, le troisième octet (100) définit le sous-réseau et le dernier octet (2) est l’identificateur de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-117">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="0d8b6-118">Quand tous les bits d’une adresse IP sont définis à la valeur 1 ou à la valeur 255.255.255.255, ils constituent une adresse de diffusion limitée.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-118">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="0d8b6-119">L’envoi d’un datagramme UDP à cette adresse remet le message à n’importe quel hôte sur le segment réseau local.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-119">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="0d8b6-120">Étant donné que les routeurs ne transfèrent jamais les messages envoyés à cette adresse, seuls les hôtes sur le segment réseau reçoivent le message de diffusion.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-120">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="0d8b6-121">Les messages de diffusion peuvent être dirigés vers des parties spécifiques d’un réseau en définissant tous les bits de l’identificateur de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-121">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="0d8b6-122">Par exemple, pour envoyer un message de diffusion à tous les hôtes sur le réseau identifié par les adresses IP commençant par 192.168.1, utilisez l’adresse 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-122">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="0d8b6-123">L’exemple de code suivant utilise un <xref:System.Net.Sockets.UdpClient> pour écouter les datagrammes UDP sur le port 11 000.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-123">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="0d8b6-124">Le client reçoit une chaîne de message et écrit le message sur la console.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-124">The client receives a message string and writes the message to the console.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000

   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener

   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
End Class 'UDPListener
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class UDPListener
{
    private const int listenPort = 11000;

    private static void StartListener()
    {
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);

        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);

                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }

    public static void Main()
    {
        StartListener();
    }
}
```

<span data-ttu-id="0d8b6-125">L’exemple de code suivant utilise un <xref:System.Net.Sockets.Socket> pour envoyer les datagrammes UDP à l’adresse de diffusion 192.168.1.255 dirigée sur le port 11 000.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-125">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="0d8b6-126">Le client envoie la chaîne de message spécifiée sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0d8b6-126">The client sends the message string specified on the command line.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("192.168.1.255");

        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);

        s.SendTo(sendbuf, ep);

        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0d8b6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d8b6-127">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
