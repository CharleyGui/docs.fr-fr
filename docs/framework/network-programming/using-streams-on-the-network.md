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
# <a name="using-streams-on-the-network"></a><span data-ttu-id="700e1-104">Utilisation de flux sur le réseau</span><span class="sxs-lookup"><span data-stu-id="700e1-104">Using Streams on the Network</span></span>

<span data-ttu-id="700e1-105">Dans .NET Framework, les ressources réseau sont représentées sous forme de flux.</span><span class="sxs-lookup"><span data-stu-id="700e1-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="700e1-106">.NET Framework traite les flux de manière générique, ce qui offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="700e1-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="700e1-107">L’envoi et la réception des données web s’effectuent à l’aide de la même technique.</span><span class="sxs-lookup"><span data-stu-id="700e1-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="700e1-108">Quel que soit le contenu réel du fichier (HTML, XML ou autre format), votre application utilise <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> et <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> pour envoyer et recevoir des données.</span><span class="sxs-lookup"><span data-stu-id="700e1-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="700e1-109">La compatibilité avec les flux est garantie dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="700e1-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="700e1-110">Les flux sont utilisés dans l’ensemble de .NET Framework, qui a une infrastructure complète pour les gérer.</span><span class="sxs-lookup"><span data-stu-id="700e1-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="700e1-111">Par exemple, vous pouvez modifier une application qui lit les données XML à partir d’un <xref:System.IO.FileStream> pour qu’elle les lise à partir d’un <xref:System.Net.Sockets.NetworkStream> à la place, simplement en modifiant les quelques lignes de code qui initialisent le flux.</span><span class="sxs-lookup"><span data-stu-id="700e1-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="700e1-112">Les principales différences entre la classe **NetworkStream** et les autres flux sont les suivantes : **NetworkStream** n’est pas identifiable par une recherche, la propriété <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> retourne toujours **false**, et les méthodes <xref:System.Net.Sockets.NetworkStream.Seek%2A> et <xref:System.Net.Sockets.NetworkStream.Position%2A> lèvent une exception <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="700e1-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="700e1-113">Les données sont traitées au fur et à mesure qu’elles arrivent.</span><span class="sxs-lookup"><span data-stu-id="700e1-113">Processing of data as it arrives.</span></span> <span data-ttu-id="700e1-114">Les flux fournissent l’accès aux données dès qu’elles sont reçues du réseau, au lieu de forcer votre application à attendre la fin de la réception d’un jeu de données entier.</span><span class="sxs-lookup"><span data-stu-id="700e1-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="700e1-115">L’espace de noms <xref:System.Net.Sockets> contient une classe **NetworkStream** qui implémente la classe <xref:System.IO.Stream> spécifiquement pour une utilisation avec les ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="700e1-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="700e1-116">Les classes dans l’espace de noms <xref:System.Net.Sockets> utilisent la classe **NetworkStream** pour représenter les flux.</span><span class="sxs-lookup"><span data-stu-id="700e1-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="700e1-117">Pour envoyer des données sur le réseau à l’aide du flux retourné, appelez <xref:System.Net.WebRequest.GetRequestStream%2A> sur votre <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="700e1-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="700e1-118">**WebRequest** enverra des en-têtes de demande au serveur. Ensuite, vous pouvez envoyer des données à la ressource réseau en appelant la <xref:System.IO.Stream.BeginWrite%2A> <xref:System.IO.Stream.EndWrite%2A> méthode, ou <xref:System.IO.Stream.Write%2A> sur le flux retourné.</span><span class="sxs-lookup"><span data-stu-id="700e1-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="700e1-119">Avec certains protocoles, tels que HTTP, vous devez définir des propriétés spécifiques au protocole avant d’envoyer des données.</span><span class="sxs-lookup"><span data-stu-id="700e1-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="700e1-120">L’exemple de code suivant montre comment définir les propriétés du protocole HTTP pour l’envoi de données.</span><span class="sxs-lookup"><span data-stu-id="700e1-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="700e1-121">Il suppose que la variable `sendData` contient les données à envoyer et que la variable `sendLength` représente le nombre d’octets de données à envoyer.</span><span class="sxs-lookup"><span data-stu-id="700e1-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="700e1-122">Pour recevoir des données du réseau, appelez <xref:System.Net.WebResponse.GetResponseStream%2A> sur votre <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="700e1-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="700e1-123">Vous pouvez ensuite lire les données de la ressource réseau en appelant la méthode <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A> ou <xref:System.IO.Stream.Read%2A> sur le flux retourné.</span><span class="sxs-lookup"><span data-stu-id="700e1-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="700e1-124">Quand vous utilisez des flux issus de ressources réseau, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="700e1-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="700e1-125">La propriété **CanSeek** retourne toujours **false**, car la classe **NetworkStream** ne peut pas changer la position dans le flux.</span><span class="sxs-lookup"><span data-stu-id="700e1-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="700e1-126">Les méthodes **Seek** et **Position** lèvent une exception **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="700e1-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="700e1-127">Quand vous utilisez **WebRequest** et **WebResponse**, les instances de flux créées en appelant **GetResponseStream** sont en lecture seule et celles créées en appelant **GetRequestStream** sont en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="700e1-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="700e1-128">Utilisez la classe <xref:System.IO.StreamReader> pour faciliter l’encodage.</span><span class="sxs-lookup"><span data-stu-id="700e1-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="700e1-129">L’exemple de code suivant utilise un **StreamReader** pour lire un flux encodé en ASCII à partir d’un **WebResponse** (l’exemple n’affiche pas l’étape de création de la demande).</span><span class="sxs-lookup"><span data-stu-id="700e1-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="700e1-130">L’appel à **GetResponse** peut être bloqué si les ressources réseau ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="700e1-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="700e1-131">Vous devez alors envisager d’utiliser une demande asynchrone avec les méthodes <xref:System.Net.WebRequest.BeginGetResponse%2A> et <xref:System.Net.WebRequest.EndGetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="700e1-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="700e1-132">L’appel à **GetRequestStream** peut être bloqué pendant la création de la connexion au serveur.</span><span class="sxs-lookup"><span data-stu-id="700e1-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="700e1-133">Vous devez alors envisager d’utiliser une demande asynchrone pour le flux avec les méthodes <xref:System.Net.WebRequest.BeginGetRequestStream%2A> et <xref:System.Net.WebRequest.EndGetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="700e1-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="700e1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="700e1-134">See also</span></span>

- [<span data-ttu-id="700e1-135">Procédure : demander des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="700e1-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="700e1-136">Demande de données</span><span class="sxs-lookup"><span data-stu-id="700e1-136">Requesting Data</span></span>](requesting-data.md)
