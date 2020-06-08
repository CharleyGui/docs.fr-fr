---
title: programmation de protocoles enfichables
description: Découvrez comment les classes WebRequest et WebResponse abstraites prennent en charge les protocoles enfichables, qui permettent à une application d’obtenir des données sans spécifier de protocole.
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
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502195"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="19483-103">programmation de protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="19483-103">Programming Pluggable Protocols</span></span>
<span data-ttu-id="19483-104">Les classes abstraites <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> fournissent la base des protocoles enfichables.</span><span class="sxs-lookup"><span data-stu-id="19483-104">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="19483-105">En dérivant de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> les classes spécifiques au protocole, une application peut demander des données à une ressource Internet et lire la réponse sans spécifier le protocole utilisé.</span><span class="sxs-lookup"><span data-stu-id="19483-105">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="19483-106">Avant de pouvoir créer un <xref:System.Net.WebRequest> spécifique au protocole, vous devez inscrire sa méthode Create.</span><span class="sxs-lookup"><span data-stu-id="19483-106">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="19483-107">Utilisez la méthode statique <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> de <xref:System.Net.WebRequest> pour inscrire un descendant de <xref:System.Net.WebRequest> afin de gérer un groupe de requêtes envoyées à un schéma Internet particulier, à un schéma et à un serveur, ou à un schéma, un serveur et un chemin.</span><span class="sxs-lookup"><span data-stu-id="19483-107">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="19483-108">Dans la plupart des cas, vous pouvez envoyer et recevoir des données à l’aide des méthodes et des propriétés de la classe <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="19483-108">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="19483-109">Toutefois, si vous avez besoin d’accéder aux propriétés spécifiques au protocole, vous pouvez caster un <xref:System.Net.WebRequest> en une instance spécifique de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="19483-109">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="19483-110">Pour tirer parti des protocoles enfichables, vos descendants <xref:System.Net.WebRequest> doivent fournir une transaction par défaut de type requête/réponse qui ne nécessite pas la définition de propriétés spécifiques au protocole.</span><span class="sxs-lookup"><span data-stu-id="19483-110">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="19483-111">Par exemple, la classe <xref:System.Net.HttpWebRequest>, qui implémente la classe <xref:System.Net.WebRequest> pour le protocole HTTP, fournit une requête `GET` par défaut et retourne un <xref:System.Net.HttpWebResponse> qui contient le flux retourné à partir du serveur web.</span><span class="sxs-lookup"><span data-stu-id="19483-111">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19483-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19483-112">See also</span></span>

- [<span data-ttu-id="19483-113">Dérivation à partir de WebRequest</span><span class="sxs-lookup"><span data-stu-id="19483-113">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="19483-114">Dérivation à partir de WebResponse</span><span class="sxs-lookup"><span data-stu-id="19483-114">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="19483-115">Programmation réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="19483-115">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="19483-116">Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole</span><span class="sxs-lookup"><span data-stu-id="19483-116">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
