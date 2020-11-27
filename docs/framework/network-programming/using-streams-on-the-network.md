---
title: Utilisation de flux sur le réseau
description: Le .NET Framework représente des ressources réseau sous forme de flux. La classe NetworkStream implémente la classe Stream pour une utilisation avec les ressources réseau.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: c59e4aa2edad7b28203cfce5f568f8ccb8558dbb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263111"
---
# <a name="using-streams-on-the-network"></a>Utilisation de flux sur le réseau

Dans .NET Framework, les ressources réseau sont représentées sous forme de flux. .NET Framework traite les flux de manière générique, ce qui offre les avantages suivants :  
  
- L’envoi et la réception des données web s’effectuent à l’aide de la même technique. Quel que soit le contenu réel du fichier (HTML, XML ou autre format), votre application utilise <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> et <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> pour envoyer et recevoir des données.  
  
- La compatibilité avec les flux est garantie dans .NET Framework. Les flux sont utilisés dans l’ensemble de .NET Framework, qui a une infrastructure complète pour les gérer. Par exemple, vous pouvez modifier une application qui lit les données XML à partir d’un <xref:System.IO.FileStream> pour qu’elle les lise à partir d’un <xref:System.Net.Sockets.NetworkStream> à la place, simplement en modifiant les quelques lignes de code qui initialisent le flux. Les principales différences entre la classe **NetworkStream** et les autres flux sont les suivantes : **NetworkStream** n’est pas identifiable par une recherche, la propriété <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> retourne toujours **false**, et les méthodes <xref:System.Net.Sockets.NetworkStream.Seek%2A> et <xref:System.Net.Sockets.NetworkStream.Position%2A> lèvent une exception <xref:System.NotSupportedException>.  
  
- Les données sont traitées au fur et à mesure qu’elles arrivent. Les flux fournissent l’accès aux données dès qu’elles sont reçues du réseau, au lieu de forcer votre application à attendre la fin de la réception d’un jeu de données entier.  
  
 L’espace de noms <xref:System.Net.Sockets> contient une classe **NetworkStream** qui implémente la classe <xref:System.IO.Stream> spécifiquement pour une utilisation avec les ressources réseau. Les classes dans l’espace de noms <xref:System.Net.Sockets> utilisent la classe **NetworkStream** pour représenter les flux.  
  
 Pour envoyer des données sur le réseau à l’aide du flux retourné, appelez <xref:System.Net.WebRequest.GetRequestStream%2A> sur votre <xref:System.Net.WebRequest>. **WebRequest** enverra des en-têtes de demande au serveur. Ensuite, vous pouvez envoyer des données à la ressource réseau en appelant la <xref:System.IO.Stream.BeginWrite%2A> <xref:System.IO.Stream.EndWrite%2A> méthode, ou <xref:System.IO.Stream.Write%2A> sur le flux retourné. Avec certains protocoles, tels que HTTP, vous devez définir des propriétés spécifiques au protocole avant d’envoyer des données. L’exemple de code suivant montre comment définir les propriétés du protocole HTTP pour l’envoi de données. Il suppose que la variable `sendData` contient les données à envoyer et que la variable `sendLength` représente le nombre d’octets de données à envoyer.  
  
```csharp  
HttpWebRequest request =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 Pour recevoir des données du réseau, appelez <xref:System.Net.WebResponse.GetResponseStream%2A> sur votre <xref:System.Net.WebResponse>. Vous pouvez ensuite lire les données de la ressource réseau en appelant la méthode <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A> ou <xref:System.IO.Stream.Read%2A> sur le flux retourné.  
  
 Quand vous utilisez des flux issus de ressources réseau, gardez à l’esprit les points suivants :  
  
- La propriété **CanSeek** retourne toujours **false**, car la classe **NetworkStream** ne peut pas changer la position dans le flux. Les méthodes **Seek** et **Position** lèvent une exception **NotSupportedException**.  
  
- Quand vous utilisez **WebRequest** et **WebResponse**, les instances de flux créées en appelant **GetResponseStream** sont en lecture seule et celles créées en appelant **GetRequestStream** sont en écriture seule.  
  
- Utilisez la classe <xref:System.IO.StreamReader> pour faciliter l’encodage. L’exemple de code suivant utilise un **StreamReader** pour lire un flux encodé en ASCII à partir d’un **WebResponse** (l’exemple n’affiche pas l’étape de création de la demande).  
  
- L’appel à **GetResponse** peut être bloqué si les ressources réseau ne sont pas disponibles. Vous devez alors envisager d’utiliser une demande asynchrone avec les méthodes <xref:System.Net.WebRequest.BeginGetResponse%2A> et <xref:System.Net.WebRequest.EndGetResponse%2A>.  
  
- L’appel à **GetRequestStream** peut être bloqué pendant la création de la connexion au serveur. Vous devez alors envisager d’utiliser une demande asynchrone pour le flux avec les méthodes <xref:System.Net.WebRequest.BeginGetRequestStream%2A> et <xref:System.Net.WebRequest.EndGetRequestStream%2A>.  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : demander des données à l’aide de la classe WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Demande de données](requesting-data.md)
