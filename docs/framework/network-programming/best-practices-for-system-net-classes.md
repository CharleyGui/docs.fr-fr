---
title: Pratiques recommandées pour les classes System.Net
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
ms.openlocfilehash: 57d0c3640c65d425ded63f53e32416053c3eb926
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624663"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="c37fa-102">Pratiques recommandées pour les classes System.Net</span><span class="sxs-lookup"><span data-stu-id="c37fa-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="c37fa-103">Les recommandations suivantes vous aideront à utiliser les classes contenues dans <xref:System.Net> de la manière la plus adéquate :</span><span class="sxs-lookup"><span data-stu-id="c37fa-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="c37fa-104">Pour connaître les bonnes pratiques d’utilisation de TLS, consultez [Bonnes pratiques du protocole TLS (Transport Layer Security) avec .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="c37fa-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="c37fa-105">Dans la mesure du possible, utilisez <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> au lieu d’effectuer un cast de type vers les classes descendantes.</span><span class="sxs-lookup"><span data-stu-id="c37fa-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="c37fa-106">Les applications qui utilisent **WebRequest** et **WebResponse** peuvent tirer parti des nouveaux protocoles Internet sans qu’aucune modification de code étendue ne soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c37fa-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="c37fa-107">Lors de l’écriture d’applications ASP.NET qui s’exécutent sur un serveur à l’aide des classes **System.Net**, il est souvent préférable, du point de vue des performances, d’utiliser les méthodes asynchrones pour <xref:System.Net.WebRequest.GetResponse%2A> et <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="c37fa-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="c37fa-108">Le nombre de connexions ouvertes à une ressource Internet peut avoir un impact significatif sur les performances du réseau et le débit.</span><span class="sxs-lookup"><span data-stu-id="c37fa-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="c37fa-109">**System.Net** utilise deux connexions par application et par hôte par défaut.</span><span class="sxs-lookup"><span data-stu-id="c37fa-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="c37fa-110">La définition de la propriété <xref:System.Net.ServicePoint.ConnectionLimit%2A> dans <xref:System.Net.ServicePoint> pour votre application peut augmenter ce nombre pour un hôte particulier.</span><span class="sxs-lookup"><span data-stu-id="c37fa-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="c37fa-111">La définition de la propriété <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> peut augmenter cette valeur par défaut pour tous les hôtes.</span><span class="sxs-lookup"><span data-stu-id="c37fa-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="c37fa-112">Quand vous écrivez des protocoles de niveau socket, essayez dans la mesure du possible d’utiliser <xref:System.Net.Sockets.TcpClient> ou <xref:System.Net.Sockets.UdpClient> au lieu d’écrire directement dans un <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="c37fa-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="c37fa-113">Ces deux classes clientes encapsulent la création de sockets TCP et UDP sans qu’il vous soit nécessaire de gérer les détails de la connexion.</span><span class="sxs-lookup"><span data-stu-id="c37fa-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="c37fa-114">Lors de l’accès à des sites qui nécessitent des informations d’identification, utilisez la classe <xref:System.Net.CredentialCache> pour créer un cache d’informations d’identification, plutôt que de les fournir avec chaque requête.</span><span class="sxs-lookup"><span data-stu-id="c37fa-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="c37fa-115">La classe **CredentialCache** recherche dans le cache les informations d’identification appropriées à présenter avec une requête, ce qui vous évite d’avoir à créer et à présenter des informations d’identification basées sur l’URL.</span><span class="sxs-lookup"><span data-stu-id="c37fa-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37fa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c37fa-116">See also</span></span>

- [<span data-ttu-id="c37fa-117">Programmation réseau dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c37fa-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
