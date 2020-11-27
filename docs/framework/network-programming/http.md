---
title: HTTP
description: En savoir plus sur la prise en charge complète du protocole HTTP fourni par le .NET Framework à l’aide des classes HttpWebRequest et HttpWebResponse.
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: 62c4ddb7e4b904be501ed2938692bce405c7e5f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253399"
---
# <a name="http"></a><span data-ttu-id="d95f6-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="d95f6-103">HTTP</span></span>

<span data-ttu-id="d95f6-104">Avec les classes <xref:System.Net.HttpWebRequest> et <xref:System.Net.HttpWebResponse>, le .NET Framework offre une prise en charge complète du protocole HTTP sur lequel repose la majeure partie du trafic Internet global.</span><span class="sxs-lookup"><span data-stu-id="d95f6-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="d95f6-105">Ces classes, dérivées de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse>, sont retournées par défaut dès que la méthode statique <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> détecte un URI commençant par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="d95f6-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="d95f6-106">Dans la plupart des cas, les classes **WebRequest** et **WebResponse** fournissent tous les éléments nécessaires pour effectuer une demande mais, si vous avez besoin d’un accès aux fonctionnalités spécifiques à HTTP exposées en tant que propriétés, vous pouvez effectuer un cast du type de ces classes en **HttpWebRequest** ou **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="d95f6-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="d95f6-107">**HttpWebRequest** et **HttpWebResponse** encapsulent une transaction de demande et réponse HTTP standard et fournissent l’accès aux en-têtes HTTP communs.</span><span class="sxs-lookup"><span data-stu-id="d95f6-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="d95f6-108">Ces classes prennent également en charge la plupart des fonctionnalités HTTP 1.1, y compris le traitement « pipeline », l’envoi et la réception des données en bloc, l’authentification, la pré-authentification, le chiffrement, la prise en charge de proxy, la validation du certificat de serveur et la gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="d95f6-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="d95f6-109">Les en-têtes personnalisés et les en-têtes non fournis par le biais de propriétés peuvent être stockés dans la propriété **Headers** qui permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="d95f6-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="d95f6-110">**HttpWebRequest** est la classe par défaut utilisée par **WebRequest**. Vous n’avez pas besoin de l’inscrire pour pouvoir passer un URI à la méthode **WebRequest.Create**.</span><span class="sxs-lookup"><span data-stu-id="d95f6-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="d95f6-111">Vous pouvez configurer votre application pour qu’elle suive automatiquement les redirections HTTP, en définissant la propriété <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> sur **true** (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="d95f6-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="d95f6-112">L’application redirigera les demandes, et la propriété <xref:System.Net.HttpWebResponse.ResponseUri%2A> de **HttpWebResponse** contiendra la ressource web qui a répondu à la demande.</span><span class="sxs-lookup"><span data-stu-id="d95f6-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="d95f6-113">Si vous définissez **AllowAutoRedirect** sur **false**, votre application doit être en mesure de traiter les redirections en tant qu’erreurs de protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="d95f6-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="d95f6-114">Les applications obtiennent des erreurs de protocole HTTP quand elles interceptent un <xref:System.Net.WebException> avec un <xref:System.Net.WebException.Status%2A> défini à la valeur <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="d95f6-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="d95f6-115">La propriété <xref:System.Net.WebException.Response%2A> contient la **WebResponse** envoyée par le serveur et indique l’erreur HTTP rencontrée.</span><span class="sxs-lookup"><span data-stu-id="d95f6-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d95f6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d95f6-116">See also</span></span>

- [<span data-ttu-id="d95f6-117">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="d95f6-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="d95f6-118">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="d95f6-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="d95f6-119">Procédure : accéder aux propriétés spécifiques à HTTP</span><span class="sxs-lookup"><span data-stu-id="d95f6-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
