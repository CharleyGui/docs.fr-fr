---
title: Utilisation des services UDP
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
ms.openlocfilehash: 477095ada6e44f66cbc60cd80375da9a87f38e39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180597"
---
# <a name="using-udp-services"></a>Utilisation des services UDP
La classe <xref:System.Net.Sockets.UdpClient> communique avec les services réseau à l’aide d’UDP. Les méthodes et propriétés de la classe <xref:System.Net.Sockets.UdpClient> assurent l’abstraction des informations nécessaires pour créer un <xref:System.Net.Sockets.Socket> permettant l’envoi et la réception de données avec le protocole UDP.

UDP (User Datagram Protocol) est un protocole simple qui essaie de fournir les données à un hôte distant le plus efficacement possible. Toutefois, comme le protocole UDP est un protocole non connecté, les datagrammes UDP envoyés au point de terminaison distant ne sont pas assurés d’arriver, ou d’arriver dans la même séquence que celle dans laquelle ils ont été envoyés. Les applications qui utilisent le protocole UDP doivent être en mesure de gérer les datagrammes manquants, en double et hors séquence.

Pour envoyer un datagramme avec une connexion UDP, vous devez connaître l’adresse de l’appareil réseau qui héberge le service dont vous avez besoin, ainsi que le numéro de port UDP utilisé par ce service pour communiquer. L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants (consultez [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Les services qui ne figurent pas dans la liste de l’IANA peuvent avoir des numéros de port compris dans la plage 1 024 à 65 535.

Des adresses réseau spéciales sont utilisées pour prendre en charge les messages de diffusion UDP sur les réseaux IP. L’exemple suivant utilise la famille d’adresses IP version 4 pour Internet.

Les adresses IP version 4 spécifient les adresses réseau sur 32 bits. Pour les adresses de classe C utilisant un masque de sous-réseau 255.255.255.0, ces bits sont divisés en quatre octets. Au format décimal, les quatre octets s’écrivent selon la notation connue de quatre nombres séparés par un point (par exemple, 192.168.100.2). Les deux premiers octets (192.168 dans cet exemple) forment le numéro du réseau, le troisième octet (100) définit le sous-réseau et le dernier octet (2) est l’identificateur de l’hôte.

Quand tous les bits d’une adresse IP sont définis à la valeur 1 ou à la valeur 255.255.255.255, ils constituent une adresse de diffusion limitée. L’envoi d’un datagramme UDP à cette adresse remet le message à n’importe quel hôte sur le segment réseau local. Étant donné que les routeurs ne transfèrent jamais les messages envoyés à cette adresse, seuls les hôtes sur le segment réseau reçoivent le message de diffusion.

Les messages de diffusion peuvent être dirigés vers des parties spécifiques d’un réseau en définissant tous les bits de l’identificateur de l’hôte. Par exemple, pour envoyer un message de diffusion à tous les hôtes sur le réseau identifié par les adresses IP commençant par 192.168.1, utilisez l’adresse 192.168.1.255.

L’exemple de code suivant utilise un <xref:System.Net.Sockets.UdpClient> pour écouter les datagrammes UDP sur le port 11 000. Le client reçoit une chaîne de message et écrit le message sur la console.

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

L’exemple de code suivant utilise un <xref:System.Net.Sockets.Socket> pour envoyer les datagrammes UDP à l’adresse de diffusion 192.168.1.255 dirigée sur le port 11 000. Le client envoie la chaîne de message spécifiée sur la ligne de commande.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
