---
title: Demande de données
description: Découvrez comment les protocoles enfichables vous permettent de développer des applications qui utilisent une seule interface pour récupérer des données de plusieurs protocoles.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 87ad0144f57bdca0e0235aea30c4ab450cc890f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279296"
---
# <a name="requesting-data"></a><span data-ttu-id="61c54-103">Demande de données</span><span class="sxs-lookup"><span data-stu-id="61c54-103">Requesting Data</span></span>

<span data-ttu-id="61c54-104">Lorsque vous développez des applications destinées à être exécutées dans l’environnement d’exploitation distribué qu’est l’Internet d’aujourd’hui, il est nécessaire d’employer une méthode facile et efficace pour récupérer les données à partir de ressources de tous types.</span><span class="sxs-lookup"><span data-stu-id="61c54-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="61c54-105">Les protocoles enfichables vous permettent de développer des applications qui utilisent une même interface pour récupérer les données à partir de plusieurs protocoles Internet.</span><span class="sxs-lookup"><span data-stu-id="61c54-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="61c54-106">Chargement et téléchargement de données sur un serveur Internet</span><span class="sxs-lookup"><span data-stu-id="61c54-106">Uploading and Downloading Data from an Internet Server</span></span>  

 <span data-ttu-id="61c54-107">Pour simplifier les transactions de demande et de réponse, la classe <xref:System.Net.WebClient> fournit la méthode la plus simple pour charger des données vers un serveur Internet ou les télécharger à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="61c54-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="61c54-108">**WebClient** fournit des méthodes permettant de charger et de télécharger des fichiers, d’envoyer et de recevoir des flux, et d’envoyer un tampon de données au serveur et de recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="61c54-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="61c54-109">**WebClient** utilise les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> pour établir les connexions vers la ressource Internet, pour que tous les protocoles enfichables inscrits puissent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="61c54-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="61c54-110">Les applications clientes qui doivent effectuer des transactions plus complexes demandent des données aux serveurs à l’aide de la classe **WebRequest** et de ses descendants.</span><span class="sxs-lookup"><span data-stu-id="61c54-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="61c54-111">**WebRequest** encapsule les détails de la connexion au serveur, de l’envoi de la demande et de la réception de la réponse.</span><span class="sxs-lookup"><span data-stu-id="61c54-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="61c54-112">**WebRequest** est une classe abstraite qui définit un ensemble de méthodes et de propriétés qui sont disponibles pour toutes les applications qui utilisent des protocoles enfichables.</span><span class="sxs-lookup"><span data-stu-id="61c54-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="61c54-113">Les descendants de **WebRequest**, tels que <xref:System.Net.HttpWebRequest>, implémentent les propriétés et les méthodes définies par **WebRequest** d’une manière qui est cohérente avec celle du protocole sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="61c54-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="61c54-114">La classe **WebRequest** crée des instances de descendants de **WebRequest** spécifiques au protocole, à l’aide de la valeur de l’URI passée à sa méthode <xref:System.Net.WebRequest.Create%2A> pour déterminer l’instance de classe dérivée qui doit être créée.</span><span class="sxs-lookup"><span data-stu-id="61c54-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="61c54-115">Les applications indiquent quel descendant de **WebRequest** doit être utilisé pour traiter une requête en inscrivant le constructeur du descendant avec la méthode <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61c54-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="61c54-116">Une requête est envoyée à la ressource Internet en appelant la méthode <xref:System.Net.WebRequest.GetResponse%2A> dans le **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="61c54-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="61c54-117">La méthode **GetResponse** construit la requête spécifique au protocole à partir des propriétés de **WebRequest**, établit la connexion entre le socket TCP ou UDP et le serveur, et envoie la requête.</span><span class="sxs-lookup"><span data-stu-id="61c54-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="61c54-118">Pour les requêtes qui envoient des données au serveur, telles que les requêtes HTTP **Post** ou FTP **Put**, la méthode <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> fournit un flux réseau dans lequel envoyer les données.</span><span class="sxs-lookup"><span data-stu-id="61c54-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="61c54-119">La méthode **GetResponse** retourne un **WebResponse** spécifique au protocole qui correspond au **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="61c54-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="61c54-120">La classe **WebResponse** est également une classe abstraite qui définit des méthodes et des propriétés qui sont disponibles pour toutes les applications qui utilisent des protocoles enfichables.</span><span class="sxs-lookup"><span data-stu-id="61c54-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="61c54-121">Les descendants de **WebResponse** implémentent ces propriétés et ces méthodes pour le protocole sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="61c54-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="61c54-122">La classe <xref:System.Net.HttpWebResponse>, par exemple, implémente la classe **WebResponse** pour le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="61c54-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="61c54-123">Les données retournées par le serveur sont présentées à l’application dans le flux retourné par la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61c54-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="61c54-124">Vous pouvez utiliser ce flux comme tout autre flux, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="61c54-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="61c54-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61c54-125">See also</span></span>

- [<span data-ttu-id="61c54-126">Programmation réseau dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61c54-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="61c54-127">Procédure : demander une page web et récupérer les résultats sous forme de flux</span><span class="sxs-lookup"><span data-stu-id="61c54-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="61c54-128">Procédure : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="61c54-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
