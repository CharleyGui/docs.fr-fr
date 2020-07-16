---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401976"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="00730-101">Sécurité : encodage du nom du cookie supprimé</span><span class="sxs-lookup"><span data-stu-id="00730-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="00730-102">La [norme de cookie http](https://tools.ietf.org/html/rfc6265#section-4.1.1) autorise uniquement des caractères spécifiques dans les noms et les valeurs des cookies.</span><span class="sxs-lookup"><span data-stu-id="00730-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="00730-103">Pour prendre en charge les caractères non autorisés, ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="00730-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="00730-104">Encode lors de la création d’un cookie de réponse.</span><span class="sxs-lookup"><span data-stu-id="00730-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="00730-105">Décode lors de la lecture d’un cookie de requête.</span><span class="sxs-lookup"><span data-stu-id="00730-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="00730-106">Dans ASP.NET Core 5,0, ce comportement d’encodage a changé en réponse à un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="00730-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="00730-107">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="00730-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00730-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="00730-108">Version introduced</span></span>

<span data-ttu-id="00730-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="00730-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="00730-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="00730-110">Old behavior</span></span>

<span data-ttu-id="00730-111">Les noms de cookie de réponse sont encodés.</span><span class="sxs-lookup"><span data-stu-id="00730-111">Response cookie names are encoded.</span></span> <span data-ttu-id="00730-112">Les noms des cookies de la demande sont décodés.</span><span class="sxs-lookup"><span data-stu-id="00730-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="00730-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="00730-113">New behavior</span></span>

<span data-ttu-id="00730-114">L’encodage et le décodage des noms de cookies ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="00730-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="00730-115">Pour les [versions antérieures prises en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de ASP.net Core, l’équipe envisage de limiter le problème de décodage sur place.</span><span class="sxs-lookup"><span data-stu-id="00730-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="00730-116">En outre, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> l’appel de avec un nom de cookie non valide lève une exception de type <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="00730-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="00730-117">L’encodage et le décodage des valeurs de cookie restent inchangés.</span><span class="sxs-lookup"><span data-stu-id="00730-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="00730-118">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="00730-118">Reason for change</span></span>

<span data-ttu-id="00730-119">Un problème a été découvert dans [plusieurs infrastructures Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span><span class="sxs-lookup"><span data-stu-id="00730-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="00730-120">L’encodage et le décodage pourraient permettre à une personne malveillante de contourner une fonctionnalité de sécurité appelée [préfixes de cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) en usurpant des préfixes réservés comme `__Host-` avec des valeurs encodées comme `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="00730-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="00730-121">L’attaque nécessite une exploitation secondaire pour injecter les cookies usurpés, tels qu’une vulnérabilité de script entre sites (XSS), dans le site Web.</span><span class="sxs-lookup"><span data-stu-id="00730-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="00730-122">Ces préfixes ne sont pas utilisés par défaut dans les ASP.NET Core ou les `Microsoft.Owin` bibliothèques ou les modèles.</span><span class="sxs-lookup"><span data-stu-id="00730-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00730-123">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="00730-123">Recommended action</span></span>

<span data-ttu-id="00730-124">Si vous déplacez des projets vers ASP.NET Core 5,0 ou version ultérieure, assurez-vous que leurs noms de cookie sont conformes aux spécifications de [jeton](https://tools.ietf.org/html/rfc2616#section-2.2): caractères ASCII, à l’exclusion des contrôles et des séparateurs `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="00730-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="00730-125">L’utilisation de caractères non-ASCII dans les noms de cookie ou d’autres en-têtes HTTP peut provoquer une exception du serveur ou un arrondi incorrectement effectué par le client.</span><span class="sxs-lookup"><span data-stu-id="00730-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="00730-126">Category</span><span class="sxs-lookup"><span data-stu-id="00730-126">Category</span></span>

<span data-ttu-id="00730-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00730-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00730-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="00730-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
