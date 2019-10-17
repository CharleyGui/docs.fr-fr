---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393925"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="8ece4-101">Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="8ece4-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="8ece4-102">Dans les versions antérieures, Kestrel a ajouté les en-têtes de code de fin en bloc HTTP/1.1 dans la collection d’en-têtes de demande lorsque le corps de la demande a été lu jusqu’à la fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="8ece4-103">Ce comportement est dû à des problèmes d’ambiguïté entre les en-têtes et les codes de fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="8ece4-104">La décision a été prise de déplacer les codes de fin vers une nouvelle collection.</span><span class="sxs-lookup"><span data-stu-id="8ece4-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="8ece4-105">Les codes de fin de requête HTTP/2 n’étaient pas disponibles dans ASP.NET Core 2,2, mais ils sont désormais également disponibles dans ce nouveau regroupement dans ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ece4-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="8ece4-106">De nouvelles méthodes d’extension de requête ont été ajoutées pour accéder à ces codes de fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="8ece4-107">Les codes de fin HTTP/1.1 sont disponibles une fois que le corps de la demande a été lu dans son intégralité.</span><span class="sxs-lookup"><span data-stu-id="8ece4-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="8ece4-108">Les codes de fin HTTP/2 sont disponibles une fois qu’ils sont reçus du client.</span><span class="sxs-lookup"><span data-stu-id="8ece4-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="8ece4-109">Le client n’enverra pas les codes de fin tant que le corps de la demande n’a pas été au moins mis en mémoire tampon par le serveur.</span><span class="sxs-lookup"><span data-stu-id="8ece4-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="8ece4-110">Vous devrez peut-être lire le corps de la demande pour libérer de l’espace dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8ece4-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="8ece4-111">Les codes de fin sont toujours disponibles si vous lisez le corps de la demande à la fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="8ece4-112">Les remorques marquent la fin du corps.</span><span class="sxs-lookup"><span data-stu-id="8ece4-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8ece4-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8ece4-113">Version introduced</span></span>

<span data-ttu-id="8ece4-114">3,0</span><span class="sxs-lookup"><span data-stu-id="8ece4-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8ece4-115">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="8ece4-115">Old behavior</span></span>

<span data-ttu-id="8ece4-116">Les en-têtes de demande de fin sont ajoutés à la collection `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="8ece4-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8ece4-117">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="8ece4-117">New behavior</span></span>

<span data-ttu-id="8ece4-118">Les en-têtes de demande de fin **ne sont pas présents** dans la collection `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="8ece4-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="8ece4-119">Utilisez les méthodes d’extension suivantes sur `HttpRequest` pour y accéder :</span><span class="sxs-lookup"><span data-stu-id="8ece4-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="8ece4-120">`GetDeclaredTrailers()`-obtient l’en-tête « code de fin » de la demande qui répertorie les codes de fin à attendre après le corps.</span><span class="sxs-lookup"><span data-stu-id="8ece4-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="8ece4-121">`SupportsTrailers()`-indique si la demande prend en charge la réception des en-têtes de code de fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="8ece4-122">`CheckTrailersAvailable()`-détermine si la requête prend en charge les codes de fin et si elles sont disponibles pour la lecture.</span><span class="sxs-lookup"><span data-stu-id="8ece4-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="8ece4-123">`GetTrailer(string trailerName)`-obtient l’en-tête de fin demandé à partir de la réponse.</span><span class="sxs-lookup"><span data-stu-id="8ece4-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8ece4-124">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="8ece4-124">Reason for change</span></span>

<span data-ttu-id="8ece4-125">Les codes de fin sont une fonctionnalité clé dans des scénarios tels que gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ece4-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="8ece4-126">La fusion des codes de fin dans les en-têtes de demande était confuse pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8ece4-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8ece4-127">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8ece4-127">Recommended action</span></span>

<span data-ttu-id="8ece4-128">Utilisez les méthodes d’extension liées à la remorque sur `HttpRequest` pour accéder aux codes de fin.</span><span class="sxs-lookup"><span data-stu-id="8ece4-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="8ece4-129">Category</span><span class="sxs-lookup"><span data-stu-id="8ece4-129">Category</span></span>

<span data-ttu-id="8ece4-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8ece4-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8ece4-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="8ece4-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
