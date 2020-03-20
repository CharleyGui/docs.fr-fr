---
title: Dérivation à partir de WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048582"
---
# <a name="deriving-from-webresponse"></a>Dérivation à partir de WebResponse
La classe <xref:System.Net.WebResponse> est une classe de base abstraite qui fournit les méthodes et les propriétés de base pour la création d’une réponse propre au protocole qui correspond au modèle de protocole enfichable .NET Framework. Les applications qui utilisent la classe <xref:System.Net.WebRequest> pour demander des données à des ressources reçoivent les réponses dans un **WebResponse**. Les descendants **WebResponse** propres au protocole doivent implémenter les membres abstraits de la classe **WebResponse**.  
  
 La classe **WebRequest** associée doit créer des descendants **WebResponse**. Par exemple, les instances de <xref:System.Net.HttpWebResponse> sont créées uniquement suite à l’appel de <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> ou <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Chaque **WebResponse** contient le résultat d’une requête envoyée à une ressource et n’est pas destiné à être réutilisé.  
  
## <a name="contentlength-property"></a>Propriété ContentLength  
 La propriété <xref:System.Net.WebResponse.ContentLength%2A> indique le nombre d’octets de données qui sont disponibles dans le flux retourné par la méthode <xref:System.Net.WebResponse.GetResponseStream%2A>. La propriété **ContentLength** n’indique pas le nombre d’octets d’informations d’en-tête ou de métadonnées retournés par le serveur ; elle n’indique que le nombre d’octets de données dans la ressource demandée proprement dite.  
  
## <a name="contenttype-property"></a>Propriété ContentType  
 La propriété <xref:System.Net.WebResponse.ContentType%2A> fournit toutes les informations spéciales que votre protocole vous oblige à envoyer au client pour identifier le type de contenu envoyé par le serveur. Il s’agit généralement du type de contenu MIME des données retournées.  
  
## <a name="headers-property"></a>Propriété Headers  
 La propriété <xref:System.Net.WebResponse.Headers%2A> contient une collection arbitraire de paires nom/valeur de métadonnées associées à la réponse. Toutes les métadonnées nécessaires au protocole qui peuvent être exprimées sous forme de paire nom/valeur peuvent être incluses dans la propriété **Headers**.  
  
 Vous n’êtes pas obligé d’utiliser la propriété **Headers** pour utiliser des métadonnées d’en-tête. Les métadonnées propres au protocole peuvent être exposées en tant que propriétés ; par exemple, la propriété <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> expose l’en-tête HTTP **Last-Modified**. Quand vous exposez des métadonnées d’en-tête en tant que propriété, vous ne devez pas autoriser la définition de la même propriété à l’aide de la propriété **Headers**.  
  
## <a name="responseuri-property"></a>Propriété ResponseUri  
 La propriété <xref:System.Net.WebResponse.ResponseUri%2A> contient l’URI de la ressource qui a réellement fourni la réponse. Pour les protocoles qui ne prennent pas en charge la redirection, **ResponseUri** est identique à la propriété <xref:System.Net.WebRequest.RequestUri%2A> de la **WebRequest** qui a créé la réponse. Si le protocole prend en charge la redirection de la requête, **ResponseUri** contient l’URI de la réponse.  
  
## <a name="close-method"></a>Close, méthode  
 La méthode <xref:System.Net.WebResponse.Close%2A> ferme toutes les connexions établies par la requête et la réponse, et nettoie les ressources utilisées par la réponse. La méthode **Close** ferme toutes les instances de flux utilisées par la réponse, mais elle ne lève pas d’exception si le flux de réponse a été fermé précédemment par un appel à la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.  
  
## <a name="getresponsestream-method"></a>Méthode GetResponseStream  
 La méthode <xref:System.Net.WebResponse.GetResponseStream%2A> retourne un flux contenant la réponse retournée par la ressource demandée. Le flux de réponse contient uniquement les données retournées par la ressource ; les en-têtes ou les métadonnées incluses dans la réponse doivent être supprimée de la réponse et exposées à l’application par le biais de propriétés propres au protocole ou de la propriété **Headers**.  
  
 L’instance de flux retournée par la méthode **GetResponseStream** appartient à l’application et peut être fermée sans fermer le **WebResponse**. Par convention, l’appel de la méthode **WebResponse.Close** ferme également le flux retourné par **GetResponse**.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [programmation de protocoles enfichables](programming-pluggable-protocols.md)
- [Dérivation à partir de WebRequest](deriving-from-webrequest.md)
