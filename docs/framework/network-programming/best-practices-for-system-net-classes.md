---
title: Pratiques recommandées pour les classes System.Net
description: Suivez ces recommandations pour utiliser les classes contenues dans System.Net à leur meilleur avantage en termes de programmation .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 170e8cfe0a7d7c911122dafe18b8a5081ceb3d2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250773"
---
# <a name="best-practices-for-systemnet-classes"></a>Pratiques recommandées pour les classes System.Net

Les recommandations suivantes vous aideront à utiliser les classes contenues dans <xref:System.Net> de la manière la plus adéquate :  
  
- Pour connaître les bonnes pratiques d’utilisation de TLS, consultez [Bonnes pratiques du protocole TLS (Transport Layer Security) avec .NET Framework](tls.md).

- Dans la mesure du possible, utilisez <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> au lieu d’effectuer un cast de type vers les classes descendantes. Les applications qui utilisent **WebRequest** et **WebResponse** peuvent tirer parti des nouveaux protocoles Internet sans qu’aucune modification de code étendue ne soit nécessaire.  
  
- Lors de l’écriture d’applications ASP.NET qui s’exécutent sur un serveur à l’aide des classes **System.Net**, il est souvent préférable, du point de vue des performances, d’utiliser les méthodes asynchrones pour <xref:System.Net.WebRequest.GetResponse%2A> et <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
- Le nombre de connexions ouvertes à une ressource Internet peut avoir un impact significatif sur les performances du réseau et le débit. **System.Net** utilise deux connexions par application et par hôte par défaut. La définition de la propriété <xref:System.Net.ServicePoint.ConnectionLimit%2A> dans <xref:System.Net.ServicePoint> pour votre application peut augmenter ce nombre pour un hôte particulier. La définition de la propriété <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> peut augmenter cette valeur par défaut pour tous les hôtes.  
  
- Quand vous écrivez des protocoles de niveau socket, essayez dans la mesure du possible d’utiliser <xref:System.Net.Sockets.TcpClient> ou <xref:System.Net.Sockets.UdpClient> au lieu d’écrire directement dans un <xref:System.Net.Sockets.Socket>. Ces deux classes clientes encapsulent la création de sockets TCP et UDP sans qu’il vous soit nécessaire de gérer les détails de la connexion.  
  
- Lors de l’accès à des sites qui nécessitent des informations d’identification, utilisez la classe <xref:System.Net.CredentialCache> pour créer un cache d’informations d’identification, plutôt que de les fournir avec chaque requête. La classe **CredentialCache** recherche dans le cache les informations d’identification appropriées à présenter avec une requête, ce qui vous évite d’avoir à créer et à présenter des informations d’identification basées sur l’URL.  
  
## <a name="see-also"></a>Voir aussi

- [Programmation réseau dans le .NET Framework](index.md)
