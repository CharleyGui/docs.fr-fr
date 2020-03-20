---
title: Introduction aux protocoles enfichables
ms.date: 03/30/2017
helpviewer_keywords:
- data requests, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- URI
- Windows Sockets
- request/response model
- sending data, pluggable protocols
- pluggable protocols
- WebClient class, about WebClient class
- pluggable protocols, about pluggable protocols
- Internet, pluggable protocols
- path identifiers
- Uniform Resource Identifier
- application development [.NET Framework], pluggable protocols
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
- server identifiers
- scheme identifiers
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
ms.openlocfilehash: 72b47b8159f9f6f0dc3a19c5cbf94335507d9e7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047862"
---
# <a name="introducing-pluggable-protocols"></a>Introduction aux protocoles enfichables
Microsoft .NET Framework fournit une implémentation en couche, extensible et managée de services Internet que vous pouvez intégrer rapidement et facilement à vos applications. Les classes d’accès à Internet disponibles dans les espaces de noms <xref:System.Net> et <xref:System.Net.Sockets> permettent d’implémenter des applications Internet et web.  
  
## <a name="internet-applications"></a>Applications Internet  
 Les applications Internet se répartissent globalement en deux catégories : les applications clientes qui demandent des informations et les applications serveur qui répondent aux demandes d’informations effectuées par les clients. L’application client-serveur Internet connue est le World Wide Web, où les internautes utilisent des navigateurs pour accéder aux documents et autres données qui sont stockés sur des serveurs web dans le monde entier.  
  
 Les applications ne se limitent pas à un seul de ces rôles. Par exemple, un serveur d’applications de niveau intermédiaire standard répond aux demandes des clients en demandant lui-aussi des données à un autre serveur. Dans ce cas, ce serveur agit à la fois comme serveur et comme client.  
  
 L’application cliente effectue une demande en identifiant la ressource Internet demandée ainsi que le protocole de communication à utiliser pour la demande et la réponse. Si nécessaire, le client fournit aussi les données supplémentaires requises pour effectuer la demande, telles que les informations sur l’emplacement du proxy ou les informations d’authentification (nom d’utilisateur, mot de passe, etc.). Une fois que la demande est prête, elle est envoyée au serveur.  
  
## <a name="identifying-resources"></a>Identification des ressources  
 .NET Framework utilise un URI (Uniform Resource Identifier) pour identifier la ressource Internet demandée et le protocole de communication utilisé. L’URI se compose de trois ou quatre parties : l’identificateur de schéma, qui identifie le protocole de communication utilisé pour la demande et la réponse ; l’identificateur de serveur, constitué d’un nom d’hôte DNS ou d’une adresse TCP qui identifie de façon unique le serveur sur Internet ; l’identificateur de chemin d’accès, qui indique l’emplacement des informations demandées sur le serveur ; et une chaîne de requête facultative, qui passe les informations du client au serveur. Par exemple, l’URI `http://www.contoso.com/whatsnew.aspx?date=today` est formé de l’identificateur de schéma `http`, de l’identificateur de serveur `www.contoso.com`, du chemin d’accès `/whatsnew.aspx` et de la chaîne de requête `?date=today`.  
  
 Une fois que le serveur a reçu la demande et traité la réponse, il retourne la réponse à l’application cliente. La réponse inclut des informations supplémentaires, telles que le type du contenu (texte brut ou données XML, par exemple).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Demandes et réponses dans .NET Framework  
 .NET Framework utilise des classes spécifiques pour fournir les trois éléments d’informations nécessaires pour accéder à des ressources Internet selon un modèle de type demande-réponse : la classe <xref:System.Uri>, qui contient l’URI de la ressource Internet recherchée ; la classe <xref:System.Net.WebRequest>, qui contient une demande pour la ressource ; et la classe <xref:System.Net.WebResponse>, qui fournit un conteneur pour la réponse entrante.  
  
 Les applications clientes créent des instances `WebRequest` en passant l’URI de la ressource réseau à la méthode <xref:System.Net.WebRequest.Create%2A>. Cette méthode statique crée une instance `WebRequest` pour un protocole spécifique (HTTP, par exemple). L’instance `WebRequest` retournée fournit l’accès aux propriétés qui contrôlent à la fois la demande envoyée au serveur et l’accès au flux de données qui est transmis quand la demande est effectuée. La méthode <xref:System.Net.WebRequest.GetResponse%2A> sur `WebRequest` envoie la demande de l’application cliente au serveur identifié dans l’URI. Si la réponse risque d’être différée, la demande peut être effectuée de façon asynchrone sur **WebRequest**, à l’aide de la méthode <xref:System.Net.WebRequest.BeginGetResponse%2A>, et la réponse peut être retournée ultérieurement avec la méthode <xref:System.Net.WebRequest.EndGetResponse%2A>.  
  
 Les méthodes **GetResponse** et **EndGetResponse** retournent un **WebResponse** qui fournit l’accès aux données retournées par le serveur. Comme ces données sont retournées à l’application sous forme de flux par la méthode <xref:System.Net.WebResponse.GetResponseStream%2A>, elles peuvent être utilisées n’importe où dans l’application où des flux de données sont utilisés.  
  
 Les classes **WebRequest** et **WebResponse** constituent la base des protocoles enfichables, une implémentation de services réseau qui vous permet de développer des applications faisant appel à des ressources Internet, sans vous soucier des informations spécifiques au protocole utilisé par chaque ressource. Les classes descendantes de **WebRequest** sont inscrites avec la classe **WebRequest** pour gérer les informations utilisées pour établir les connexions aux ressources Internet.  
  
 Par exemple, la classe <xref:System.Net.HttpWebRequest> gère les informations de connexion à une ressource Internet à l’aide du protocole HTTP. Par défaut, quand la méthode **WebRequest.Create** détecte un URI qui commence par « http: » ou « https: » (les identificateurs des protocoles HTTP et HTTPS), le **WebRequest** retourné peut être utilisé en l’état, ou son type peut être converti en **HttpWebRequest** pour accéder aux propriétés spécifiques au protocole. Dans la plupart des cas, le **WebRequest** fournit toutes les informations nécessaires pour effectuer une demande.  
  
 Tous les protocoles pouvant être représentés sous forme de transaction de type demande-réponse peuvent être utilisés dans un **WebRequest**. Vous pouvez dériver des classes spécifiques au protocole à partir de **WebRequest** et **WebResponse** et inscrire ensuite les classes dérivées pour une utilisation par l’application à l’aide de la méthode <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> statique.  
  
 Quand une autorisation du client est requise pour les demandes Internet, la propriété <xref:System.Net.WebRequest.Credentials%2A> de **WebRequest** fournit les informations d’identification nécessaires. Ces informations d’identification se composent simplement de la paire nom/mot de passe pour l’authentification HTTP de base ou Digest, ou de l’ensemble nom/mot de passe/domaine pour l’authentification NTLM ou Kerberos. Une instance <xref:System.Net.NetworkCredential> peut stocker un seul ensemble d’informations d’identification, alors qu’une instance <xref:System.Net.CredentialCache> peut en stocker plusieurs simultanément. **CredentialCache** utilise l’URI de la demande ainsi que le schéma d’authentification que le serveur prend en charge pour déterminer quelles informations d’identification envoyer au serveur.  
  
## <a name="simple-requests-with-webclient"></a>Demandes simples avec WebClient  
 Pour les applications se limitant à effectuer des demandes simples de ressources Internet, la classe <xref:System.Net.WebClient> fournit les méthodes standard permettant d’échanger des données avec un serveur Internet. Comme la classe **WebClient** repose sur la classe **WebRequest** pour fournir l’accès aux ressources Internet, la classe **WebClient** peut utiliser n’importe quel protocole enfichable inscrit.  
  
 Pour les applications qui ne peuvent pas utiliser le modèle de demande/ réponse, ou pour les applications qui ont <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>besoin <xref:System.Net.Sockets.UdpClient> d’écouter sur le réseau ainsi que d’envoyer des demandes, l’espace de nom **System.Net.Sockets** fournit le , , et les classes. Ces classes gèrent les informations utilisées pour établir des connexions à l’aide de différents protocoles de transport et exposent les connexions réseau à l’application sous forme de flux.  
  
 Les classes **System.Net.Sockets** seront utiles aux développeurs qui sont familiarisés avec l’interface Windows Sockets ou à ceux qui recherchent le contrôle offert par la programmation au niveau du socket. Les classes **System.Net.Sockets** constituent un point de transition entre le code managé et le code natif dans les classes **System.Net**. Dans la plupart des cas, les classes **System.Net.Sockets** marshalent les données dans les classes équivalentes Windows 32 bits, et gèrent toutes les vérifications de sécurité nécessaires.  
  
## <a name="see-also"></a>Voir aussi

- [programmation de protocoles enfichables](programming-pluggable-protocols.md)
- [Programmation réseau dans .NET Framework](index.md)
- [Exemples de programmation réseau](network-programming-samples.md)
