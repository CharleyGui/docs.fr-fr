---
title: 'Modification avec rupture : sécurité : encodage du nom du cookie supprimé'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée sécurité : encodage du nom du cookie supprimé'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3cd40d2b04d0cdf0863e3a3fb6d790c2b35692bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761268"
---
# <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="8e9c0-103">Sécurité : encodage du nom du cookie supprimé</span><span class="sxs-lookup"><span data-stu-id="8e9c0-103">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="8e9c0-104">La [norme de cookie http](https://tools.ietf.org/html/rfc6265#section-4.1.1) autorise uniquement des caractères spécifiques dans les noms et les valeurs des cookies.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-104">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="8e9c0-105">Pour prendre en charge les caractères non autorisés, ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="8e9c0-105">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="8e9c0-106">Encode lors de la création d’un cookie de réponse.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-106">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="8e9c0-107">Décode lors de la lecture d’un cookie de requête.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-107">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="8e9c0-108">Dans ASP.NET Core 5,0, ce comportement d’encodage a changé en réponse à un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-108">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="8e9c0-109">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="8e9c0-109">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8e9c0-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8e9c0-110">Version introduced</span></span>

<span data-ttu-id="8e9c0-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="8e9c0-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="8e9c0-112">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="8e9c0-112">Old behavior</span></span>

<span data-ttu-id="8e9c0-113">Les noms de cookie de réponse sont encodés.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-113">Response cookie names are encoded.</span></span> <span data-ttu-id="8e9c0-114">Les noms des cookies de la demande sont décodés.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-114">Request cookie names are decoded.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="8e9c0-115">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="8e9c0-115">New behavior</span></span>

<span data-ttu-id="8e9c0-116">L’encodage et le décodage des noms de cookies ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-116">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="8e9c0-117">Pour les [versions antérieures prises en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de ASP.net Core, l’équipe envisage de limiter le problème de décodage sur place.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-117">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="8e9c0-118">En outre, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> l’appel de avec un nom de cookie non valide lève une exception de type <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="8e9c0-118">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="8e9c0-119">L’encodage et le décodage des valeurs de cookie restent inchangés.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-119">Encoding and decoding of cookie values remains unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8e9c0-120">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="8e9c0-120">Reason for change</span></span>

<span data-ttu-id="8e9c0-121">Un problème a été découvert dans [plusieurs infrastructures Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span><span class="sxs-lookup"><span data-stu-id="8e9c0-121">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="8e9c0-122">L’encodage et le décodage pourraient permettre à une personne malveillante de contourner une fonctionnalité de sécurité appelée [préfixes de cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) en usurpant des préfixes réservés comme `__Host-` avec des valeurs encodées comme `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="8e9c0-122">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="8e9c0-123">L’attaque nécessite une exploitation secondaire pour injecter les cookies usurpés, tels qu’une vulnérabilité de script entre sites (XSS), dans le site Web.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-123">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="8e9c0-124">Ces préfixes ne sont pas utilisés par défaut dans les ASP.NET Core ou les `Microsoft.Owin` bibliothèques ou les modèles.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-124">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8e9c0-125">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8e9c0-125">Recommended action</span></span>

<span data-ttu-id="8e9c0-126">Si vous déplacez des projets vers ASP.NET Core 5,0 ou version ultérieure, assurez-vous que leurs noms de cookie sont conformes aux spécifications de [jeton](https://tools.ietf.org/html/rfc2616#section-2.2): caractères ASCII, à l’exclusion des contrôles et des séparateurs `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="8e9c0-126">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="8e9c0-127">L’utilisation de caractères non-ASCII dans les noms de cookie ou d’autres en-têtes HTTP peut provoquer une exception du serveur ou un arrondi incorrectement effectué par le client.</span><span class="sxs-lookup"><span data-stu-id="8e9c0-127">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8e9c0-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="8e9c0-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
