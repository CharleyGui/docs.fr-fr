---
title: Utilisation de sockets clients
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046959"
---
# <a name="using-client-sockets"></a>Utilisation de sockets clients
Avant de démarrer une conversation via un <xref:System.Net.Sockets.Socket>, vous devez créer un canal de données entre votre application et l’appareil distant. Il existe d’autres protocoles et familles d’adresses réseau, mais cet exemple montre comment créer une connexion TCP/IP à un service distant.  
  
 TCP/IP utilise une adresse réseau et un numéro de port de service pour identifier un service de manière unique. L’adresse réseau identifie un appareil spécifique sur le réseau ; le numéro de port identifie le service spécifique sur cet appareil faisant l’objet de la connexion. La combinaison de l’adresse réseau et du port de service constitue un point de terminaison, qui est représenté par la classe <xref:System.Net.EndPoint> dans .NET Framework. Un descendant du point de terminaison (**EndPoint**) est défini pour chaque famille d’adresses prise en charge. Pour la famille d’adresses IP, il s’agit de la classe <xref:System.Net.IPEndPoint>.  
  
 La classe <xref:System.Net.Dns> fournit des services de nom de domaine aux applications qui utilisent des services Internet TCP/IP. La méthode <xref:System.Net.Dns.Resolve%2A> interroge un serveur DNS pour mapper un nom de domaine convivial (par exemple, « host.contoso.com ») à une adresse Internet numérique (par exemple, 192.168.1.1). **Resolve** retourne un <xref:System.Net.IPHostEntry> qui contient une liste des adresses et alias pour le nom demandé. Dans la plupart des cas, vous pouvez utiliser la première adresse retournée dans le tableau <xref:System.Net.IPHostEntry.AddressList%2A>. Le code suivant obtient un <xref:System.Net.IPAddress> contenant l’adresse IP du serveur host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants. Pour plus d’informations, consultez [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml). Les autres services peuvent avoir un numéro de port compris dans la plage 1 024 à 65 535. Le code suivant combine l’adresse IP du serveur host.contoso.com avec un numéro de port pour créer un point de terminaison distant pour une connexion.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Après avoir déterminé l’adresse de l’appareil distant et sélectionné le port à utiliser pour la connexion, l’application peut essayer d’établir une connexion avec l’appareil distant. L’exemple suivant utilise un **IPEndPoint** existant pour établir une connexion à un appareil distant et intercepte les exceptions qui sont levées.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d’un socket client synchrone](using-a-synchronous-client-socket.md)
- [Utilisation d’un socket client asynchrone](using-an-asynchronous-client-socket.md)
- [Comment : créer un socket](how-to-create-a-socket.md)
- [Sockets](sockets.md)
