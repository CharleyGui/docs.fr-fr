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
ms.openlocfilehash: 19350d685a81d56657ca0a117d61b50ae24fab6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502182"
---
# <a name="requesting-data"></a>Demande de données
Lorsque vous développez des applications destinées à être exécutées dans l’environnement d’exploitation distribué qu’est l’Internet d’aujourd’hui, il est nécessaire d’employer une méthode facile et efficace pour récupérer les données à partir de ressources de tous types. Les protocoles enfichables vous permettent de développer des applications qui utilisent une même interface pour récupérer les données à partir de plusieurs protocoles Internet.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Chargement et téléchargement de données sur un serveur Internet  
 Pour simplifier les transactions de demande et de réponse, la classe <xref:System.Net.WebClient> fournit la méthode la plus simple pour charger des données vers un serveur Internet ou les télécharger à partir de celui-ci. **WebClient** fournit des méthodes permettant de charger et de télécharger des fichiers, d’envoyer et de recevoir des flux, et d’envoyer un tampon de données au serveur et de recevoir une réponse. **WebClient** utilise les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> pour établir les connexions vers la ressource Internet, pour que tous les protocoles enfichables inscrits puissent être utilisés.  
  
 Les applications clientes qui doivent effectuer des transactions plus complexes demandent des données aux serveurs à l’aide de la classe **WebRequest** et de ses descendants. **WebRequest** encapsule les détails de la connexion au serveur, de l’envoi de la demande et de la réception de la réponse. **WebRequest** est une classe abstraite qui définit un ensemble de méthodes et de propriétés qui sont disponibles pour toutes les applications qui utilisent des protocoles enfichables. Les descendants de **WebRequest**, tels que <xref:System.Net.HttpWebRequest>, implémentent les propriétés et les méthodes définies par **WebRequest** d’une manière qui est cohérente avec celle du protocole sous-jacent.  
  
 La classe **WebRequest** crée des instances de descendants de **WebRequest** spécifiques au protocole, à l’aide de la valeur de l’URI passée à sa méthode <xref:System.Net.WebRequest.Create%2A> pour déterminer l’instance de classe dérivée qui doit être créée. Les applications indiquent quel descendant de **WebRequest** doit être utilisé pour traiter une requête en inscrivant le constructeur du descendant avec la méthode <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType>.  
  
 Une requête est envoyée à la ressource Internet en appelant la méthode <xref:System.Net.WebRequest.GetResponse%2A> dans le **WebRequest**. La méthode **GetResponse** construit la requête spécifique au protocole à partir des propriétés de **WebRequest**, établit la connexion entre le socket TCP ou UDP et le serveur, et envoie la requête. Pour les requêtes qui envoient des données au serveur, telles que les requêtes HTTP **Post** ou FTP **Put**, la méthode <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> fournit un flux réseau dans lequel envoyer les données.  
  
 La méthode **GetResponse** retourne un **WebResponse** spécifique au protocole qui correspond au **WebRequest**.  
  
 La classe **WebResponse** est également une classe abstraite qui définit des méthodes et des propriétés qui sont disponibles pour toutes les applications qui utilisent des protocoles enfichables. Les descendants de **WebResponse** implémentent ces propriétés et ces méthodes pour le protocole sous-jacent. La classe <xref:System.Net.HttpWebResponse>, par exemple, implémente la classe **WebResponse** pour le protocole HTTP.  
  
 Les données retournées par le serveur sont présentées à l’application dans le flux retourné par la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>. Vous pouvez utiliser ce flux comme tout autre flux, comme indiqué dans l’exemple suivant.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Voir aussi

- [Programmation réseau dans .NET Framework](index.md)
- [Guide pratique pour demander une page web et récupérer les résultats sous forme de flux](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Comment : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
