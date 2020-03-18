---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393925"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="fbdac-101">Kestrel: En-têtes de remorque de demande déplacé à la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="fbdac-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="fbdac-102">Dans les versions précédentes, Kestrel a ajouté HTTP/1.1 en-têtes de remorque en morceaux dans la collection d’en-têtes de demande lorsque le corps de demande a été lu à la fin.</span><span class="sxs-lookup"><span data-stu-id="fbdac-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="fbdac-103">Ce comportement a suscité des inquiétudes quant à l’ambiguïté entre les en-têtes et les remorques.</span><span class="sxs-lookup"><span data-stu-id="fbdac-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="fbdac-104">La décision a été prise de déplacer les remorques vers une nouvelle collection.</span><span class="sxs-lookup"><span data-stu-id="fbdac-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="fbdac-105">Les remorques de demande HTTP/2 n’étaient pas disponibles dans ASP.NET Core 2.2, mais sont maintenant également disponibles dans cette nouvelle collection dans ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fbdac-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="fbdac-106">De nouvelles méthodes d’extension de demande ont été ajoutées pour accéder à ces remorques.</span><span class="sxs-lookup"><span data-stu-id="fbdac-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="fbdac-107">LES remorques HTTP/1.1 sont disponibles une fois que l’ensemble du corps de demande a été lu.</span><span class="sxs-lookup"><span data-stu-id="fbdac-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="fbdac-108">Les bandes-annonces HTTP/2 sont disponibles une fois reçues du client.</span><span class="sxs-lookup"><span data-stu-id="fbdac-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="fbdac-109">Le client n’enverra pas les remorques jusqu’à ce que l’ensemble du corps de demande a été au moins tamponné par le serveur.</span><span class="sxs-lookup"><span data-stu-id="fbdac-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="fbdac-110">Vous devrez peut-être lire le corps de demande pour libérer l’espace tampon.</span><span class="sxs-lookup"><span data-stu-id="fbdac-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="fbdac-111">Les remorques sont toujours disponibles si vous lisez le corps de demande jusqu’à la fin.</span><span class="sxs-lookup"><span data-stu-id="fbdac-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="fbdac-112">Les remorques marquent la fin du corps.</span><span class="sxs-lookup"><span data-stu-id="fbdac-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fbdac-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fbdac-113">Version introduced</span></span>

<span data-ttu-id="fbdac-114">3.0</span><span class="sxs-lookup"><span data-stu-id="fbdac-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fbdac-115">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="fbdac-115">Old behavior</span></span>

<span data-ttu-id="fbdac-116">Les en-têtes de remorque `HttpRequest.Headers` de demande seraient ajoutés à la collection.</span><span class="sxs-lookup"><span data-stu-id="fbdac-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fbdac-117">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="fbdac-117">New behavior</span></span>

<span data-ttu-id="fbdac-118">Les en-têtes de bande-annonce de demande **ne sont pas présents** dans la `HttpRequest.Headers` collection.</span><span class="sxs-lookup"><span data-stu-id="fbdac-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="fbdac-119">Utilisez les méthodes `HttpRequest` d’extension suivantes pour y accéder :</span><span class="sxs-lookup"><span data-stu-id="fbdac-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="fbdac-120">`GetDeclaredTrailers()`- Obtient la demande "Bande-annonce" en-tête qui énumère les remorques à attendre après le corps.</span><span class="sxs-lookup"><span data-stu-id="fbdac-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="fbdac-121">`SupportsTrailers()`- Indique si la demande prend en charge la réception des en-têtes de remorque.</span><span class="sxs-lookup"><span data-stu-id="fbdac-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="fbdac-122">`CheckTrailersAvailable()`- Détermine si la demande prend en charge les remorques et si elles sont disponibles pour la lecture.</span><span class="sxs-lookup"><span data-stu-id="fbdac-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="fbdac-123">`GetTrailer(string trailerName)`- Obtient l’en-tête demandé de la réponse.</span><span class="sxs-lookup"><span data-stu-id="fbdac-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fbdac-124">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="fbdac-124">Reason for change</span></span>

<span data-ttu-id="fbdac-125">Les bandes-annonces sont une caractéristique clé dans des scénarios comme gRPC.</span><span class="sxs-lookup"><span data-stu-id="fbdac-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="fbdac-126">La fusion des remorques pour demander des en-têtes était déroutant pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbdac-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fbdac-127">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fbdac-127">Recommended action</span></span>

<span data-ttu-id="fbdac-128">Utilisez les méthodes d’extension liées à la remorque pour `HttpRequest` accéder aux remorques.</span><span class="sxs-lookup"><span data-stu-id="fbdac-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="fbdac-129">Category</span><span class="sxs-lookup"><span data-stu-id="fbdac-129">Category</span></span>

<span data-ttu-id="fbdac-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fbdac-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fbdac-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="fbdac-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
