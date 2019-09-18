---
title: programmation de protocoles enfichables
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047399"
---
# <a name="programming-pluggable-protocols"></a>programmation de protocoles enfichables
Les classes abstraites <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> fournissent la base des protocoles enfichables. En dérivant de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> les classes spécifiques au protocole, une application peut demander des données à une ressource Internet et lire la réponse sans spécifier le protocole utilisé.  
  
 Avant de pouvoir créer un <xref:System.Net.WebRequest> spécifique au protocole, vous devez inscrire sa méthode Create. Utilisez la méthode statique <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> de <xref:System.Net.WebRequest> pour inscrire un descendant de <xref:System.Net.WebRequest> afin de gérer un groupe de requêtes envoyées à un schéma Internet particulier, à un schéma et à un serveur, ou à un schéma, un serveur et un chemin.  
  
 Dans la plupart des cas, vous pouvez envoyer et recevoir des données à l’aide des méthodes et des propriétés de la classe <xref:System.Net.WebRequest>. Toutefois, si vous avez besoin d’accéder aux propriétés spécifiques au protocole, vous pouvez caster un <xref:System.Net.WebRequest> en une instance spécifique de la classe dérivée.  
  
 Pour tirer parti des protocoles enfichables, vos descendants <xref:System.Net.WebRequest> doivent fournir une transaction par défaut de type requête/réponse qui ne nécessite pas la définition de propriétés spécifiques au protocole. Par exemple, la classe <xref:System.Net.HttpWebRequest>, qui implémente la classe <xref:System.Net.WebRequest> pour le protocole HTTP, fournit une requête `GET` par défaut et retourne un <xref:System.Net.HttpWebResponse> qui contient le flux retourné à partir du serveur web.  
  
## <a name="see-also"></a>Voir aussi

- [Dérivation de WebRequest](deriving-from-webrequest.md)
- [Dérivation à partir de WebResponse](deriving-from-webresponse.md)
- [Programmation réseau dans le .NET Framework](index.md)
- [Guide pratique : caster une classe WebRequest en vue d’accéder aux propriétés spécifiques au protocole](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
