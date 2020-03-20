---
title: dérivation de WebRequest
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
ms.openlocfilehash: 6bee864f8d24076d16f226c29d61801e856739d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048604"
---
# <a name="deriving-from-webrequest"></a>dérivation de WebRequest
La classe <xref:System.Net.WebRequest> est une classe de base abstraite qui fournit les méthodes et les propriétés de base pour la création d’un gestionnaire de demande propre au protocole qui correspond au modèle de protocole enfichable .NET Framework. Les applications qui utilisent la classe **WebRequest** peuvent demander des données à l’aide de n’importe quel protocole pris en charge, sans avoir besoin de spécifier le protocole utilisé.  
  
 Deux critères doivent être remplis pour qu’une classe propre au protocole soit utilisée comme protocole enfichable : la classe doit implémenter l’interface <xref:System.Net.IWebRequestCreate> et elle doit s’inscrire auprès de la méthode <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType>. La classe doit remplacer toutes les propriétés et les méthodes abstraites de **WebRequest** pour fournir l’interface enfichable.  
  
 Les instances de **WebRequest** sont destinées à un usage unique ; si vous souhaitez exécuter une autre requête, créez un nouveau **WebRequest**. **WebRequest** prend en charge l’interface <xref:System.Runtime.Serialization.ISerializable> pour permettre aux développeurs de sérialiser un modèle **WebRequest** puis de recréer le modèle pour des requêtes supplémentaires.  
  
## <a name="iwebrequest-create-method"></a>Méthode IWebRequest Create  
 La méthode <xref:System.Net.IWebRequestCreate.Create%2A> est chargée d’initialiser une nouvelle instance de la classe propre au protocole. Quand un nouveau **WebRequest** est créé, la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> fait correspondre l’URI demandé avec les préfixes URI inscrits auprès de la méthode **RegisterPrefix**. La méthode **Create** du descendant propre au protocole approprié doit retourner une instance initialisée du descendant capable d’effectuer une transaction de requête/réponse standard pour le protocole sans avoir besoin de champs propres au protocole modifiés.  
  
## <a name="connectiongroupname-property"></a>Propriété ConnectionGroupName  
 La propriété <xref:System.Net.WebRequest.ConnectionGroupName%2A> sert à nommer un groupe de connexions à une ressource afin que plusieurs requêtes puissent être effectuées sur une même connexion. Pour implémenter le partage de connexion, vous devez utiliser une méthode de groupement et d’assignation des connexions propre au protocole. Par exemple, la classe <xref:System.Net.ServicePointManager> fournie implémente le partage de connexion pour la classe <xref:System.Net.HttpWebRequest>. La classe **ServicePointManager** crée un <xref:System.Net.ServicePoint> qui fournit une connexion à un serveur spécifique pour chaque groupe de connexions.  
  
## <a name="contentlength-property"></a>Propriété ContentLength  
 La propriété <xref:System.Net.WebRequest.ContentLength%2A> spécifie le nombre d’octets de données qui seront envoyés au serveur lors du chargement des données.  
  
 En règle générale, la propriété <xref:System.Net.WebRequest.Method%2A> doit être définie pour indiquer qu’un chargement a lieu quand la propriété **ContentLength** a une valeur supérieure à zéro.  
  
## <a name="contenttype-property"></a>Propriété ContentType  
 La propriété <xref:System.Net.WebRequest.ContentType%2A> fournit toutes les informations spéciales que votre protocole vous oblige à envoyer au serveur pour identifier le type de contenu que vous envoyez. Il s’agit généralement du type de contenu MIME des données chargées.  
  
## <a name="credentials-property"></a>Propriété Credentials  
 La propriété <xref:System.Net.WebRequest.Credentials%2A> contient les informations nécessaires pour authentifier la requête auprès du serveur. Vous devez implémenter les détails du processus d’authentification pour votre protocole. La classe <xref:System.Net.AuthenticationManager> est chargée d’authentifier les requêtes et de fournir un jeton d’authentification. La classe qui fournit les informations d’identification utilisées par votre protocole doit implémenter l’interface <xref:System.Net.ICredentials>.  
  
## <a name="headers-property"></a>Propriété Headers  
 La propriété <xref:System.Net.WebRequest.Headers%2A> contient une collection arbitraire de paires nom/valeur de métadonnées associées à la requête. Toutes les métadonnées nécessaires au protocole qui peuvent être exprimées sous forme de paire nom/valeur peuvent être incluses dans la propriété **Headers**. En général, vous devez définir ces informations avant d’appeler la méthode <xref:System.Net.WebRequest.GetRequestStream%2A> ou <xref:System.Net.WebRequest.GetResponse%2A> ; une fois que la requête a été effectuée, les métadonnées sont considérées comme étant en lecture seule.  
  
 Vous n’êtes pas obligé d’utiliser la propriété **Headers** pour utiliser des métadonnées d’en-tête. Les métadonnées propres au protocole peuvent être exposées en tant que propriétés ; par exemple, la propriété <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> expose l’en-tête HTTP **User-Agent**. Quand vous exposez des métadonnées d’en-tête en tant que propriété, vous ne devez pas autoriser la définition de la même propriété à l’aide de la propriété **Headers**.  
  
## <a name="method-property"></a>Propriété Method  
 La propriété <xref:System.Net.WebRequest.Method%2A> contient le verbe ou l’action que la requête souhaite que le serveur effectue. La valeur par défaut de la propriété **Method** doit activer une action de requête/réponse standard sans qu’il soit obligatoire de définir des propriétés propres au protocole. Par exemple, la méthode <xref:System.Net.HttpWebResponse.Method%2A> est GET par défaut, ce qui demande une ressource à un serveur web et retourne la réponse.  
  
 En règle générale, la propriété **ContentLength** doit être affectée d’une valeur supérieure à zéro quand la propriété **Method** a comme valeur un verbe ou une action qui indique qu’un chargement a lieu.  
  
## <a name="preauthenticate-property"></a>Propriété PreAuthenticate  
 Les applications définissent la propriété <xref:System.Net.WebRequest.PreAuthenticate%2A> pour indiquer que des informations d’authentification doivent être envoyées avec la requête initiale au lieu d’attendre une demande d’authentification. La propriété **PreAuthenticate** n’est significative que si le protocole prend en charge les informations d’identification d’authentification envoyées avec la requête initiale.  
  
## <a name="proxy-property"></a>Propriété Proxy  
 La propriété <xref:System.Net.WebRequest.Proxy%2A> contient une interface <xref:System.Net.IWebProxy> qui est utilisée pour accéder à la ressource demandée. La propriété **Proxy** n’est significative que si votre protocole prend en charge les requêtes en proxy. Vous devez définir le proxy par défaut s’il est requis par votre protocole.  
  
 Dans certains environnements, comme derrière un pare-feu d’entreprise, il est possible que votre protocole doive utiliser un proxy. Dans ce cas, vous devez implémenter l’interface **IWebProxy** pour créer une classe proxy qui fonctionne pour votre protocole.  
  
## <a name="requesturi-property"></a>Propriété RequestUri  
 La propriété <xref:System.Net.WebRequest.RequestUri%2A> contient l’URI qui a été passée à la méthode **WebRequest.Create**. Elle est en lecture seule et ne peut pas être modifiée une fois le **WebRequest** créé. Si votre protocole prend en charge la redirection, la réponse peut provenir d’une ressource identifiée par un autre URI. Si vous avez besoin de fournir l’accès à l’URI qui a répondu, vous devez fournir une propriété supplémentaire contenant cet URI.  
  
## <a name="timeout-property"></a>Propriété du délai d'attente  
 La propriété <xref:System.Net.WebRequest.Timeout%2A> contient la durée, en millisecondes, à attendre avant l’expiration de la requête et la levée d’une exception. **Timeout** s’applique uniquement aux requêtes synchrones effectuées avec la méthode <xref:System.Net.WebRequest.GetResponse%2A> ; les requêtes asynchrones doivent utiliser la méthode <xref:System.Net.WebRequest.Abort%2A> pour annuler une requête en attente.  
  
 La définition de la propriété **Timeout** n’est significative que si la classe propre au protocole implémente un processus de délai d’attente.  
  
## <a name="abort-method"></a>Abort, méthode  
 La méthode <xref:System.Net.WebRequest.Abort%2A> annule une requête asynchrone à un serveur en attente. Une fois la requête annulée, l’appel à **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, **BeginGetRequestStream** ou **EndGetRequestStream** lève une <xref:System.Net.WebException> avec la propriété <xref:System.Net.WebException.Status%2A> définie sur <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Méthodes BeginGetRequestStream et EndGetRequestStream  
 La méthode <xref:System.Net.WebRequest.BeginGetRequestStream%2A> démarre une requête asynchrone pour le flux utilisé pour charger des données sur le serveur. La méthode <xref:System.Net.WebRequest.EndGetRequestStream%2A> termine la requête asynchrone et retourne le flux demandé. Ces méthodes implémentent la méthode **GetRequestStream** à l’aide du modèle asynchrone .NET Framework standard.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Méthodes BeginGetResponse et EndGetResponse  
 La méthode <xref:System.Net.WebRequest.BeginGetResponse%2A> démarre une requête asynchrone à un serveur. La méthode <xref:System.Net.WebRequest.EndGetResponse%2A> termine la requête asynchrone et retourne la réponse demandée. Ces méthodes implémentent la méthode **GetResponse** à l’aide du modèle asynchrone .NET Framework standard.  
  
## <a name="getrequeststream-method"></a>Méthode GetRequestStream  
 La méthode <xref:System.Net.WebRequest.GetRequestStream%2A> retourne un flux utilisé pour écrire des données sur le serveur demandé. Le flux retourné doit être un flux en écriture seule qui n’effectue pas de recherche ; il doit s’agir d’un flux de données unidirectionnel qui est écrit sur le serveur. Le flux retourne la valeur false pour les propriétés <xref:System.IO.Stream.CanRead%2A> et <xref:System.IO.Stream.CanSeek%2A>, et la valeur true pour la propriété <xref:System.IO.Stream.CanWrite%2A>.  
  
 La méthode **GetRequestStream** ouvre généralement une connexion au serveur et, avant de retourner le flux, envoie des informations d’en-tête qui indiquent que des données sont envoyées au serveur. Étant donné que **GetRequestStream** démarre la requête, la définition de propriétés **Header** ou de la propriété **ContentLength** n’est généralement pas autorisée après avoir appelé **GetRequestStream**.  
  
## <a name="getresponse-method"></a>Méthode GetResponse  
 La méthode <xref:System.Net.WebRequest.GetResponse%2A> retourne un descendant propre au protocole de la classe <xref:System.Net.WebResponse> qui représente la réponse du serveur. À moins que la requête ait déjà été initiée par la méthode **GetRequestStream**, la méthode **GetResponse** crée une connexion à la ressource identifiée par **RequestUri**, envoie des informations d’en-tête indiquant le type de requête effectuée, puis reçoit la réponse de la ressource.  
  
 Une fois la méthode **GetResponse** appelée, toutes les propriétés doivent être considérées en lecture seule. Les instances de **WebRequest** sont destinées à un usage unique ; si vous souhaitez effectuer une autre requête, vous devez créer un nouveau **WebRequest**.  
  
 La méthode **GetResponse** est responsable de la création d’un descendant **WebResponse** approprié pour contenir la réponse entrante.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [programmation de protocoles enfichables](programming-pluggable-protocols.md)
- [Dérivation à partir de WebResponse](deriving-from-webresponse.md)
