---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198421"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="b7aa7-101">HTTP : modifications de l’infrastructure du corps de la réponse</span><span class="sxs-lookup"><span data-stu-id="b7aa7-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="b7aa7-102">L’infrastructure de stockage d’un corps de réponse HTTP a changé.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="b7aa7-103">Si vous utilisez `HttpResponse` directement, vous ne devez pas apporter de modifications au code.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="b7aa7-104">En savoir plus si vous encapsulez ou remplacez `HttpResponse.Body` ou que vous accédez à `HttpContext.Features`.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b7aa7-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b7aa7-105">Version introduced</span></span>

<span data-ttu-id="b7aa7-106">3,0</span><span class="sxs-lookup"><span data-stu-id="b7aa7-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b7aa7-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="b7aa7-107">Old behavior</span></span>

<span data-ttu-id="b7aa7-108">Trois API sont associées au corps de la réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="b7aa7-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="b7aa7-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="b7aa7-109">New behavior</span></span>

<span data-ttu-id="b7aa7-110">Si vous remplacez `HttpResponse.Body`, il remplace l’intégralité de `IHttpResponseBodyFeature` par un wrapper autour de votre flux donné à l’aide de `StreamResponseBodyFeature` pour fournir des implémentations par défaut pour toutes les API attendues.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="b7aa7-111">La réinitialisation du flux d’origine rétablit cette modification.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b7aa7-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="b7aa7-112">Reason for change</span></span>

<span data-ttu-id="b7aa7-113">La motivation consiste à combiner les API de corps de réponse en une seule nouvelle interface de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b7aa7-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b7aa7-114">Recommended action</span></span>

<span data-ttu-id="b7aa7-115">Utilisez `IHttpResponseBodyFeature` là où vous utilisiez précédemment `IHttpResponseFeature.Body`, `IHttpSendFileFeature` ou `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="b7aa7-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="b7aa7-116">Category</span><span class="sxs-lookup"><span data-stu-id="b7aa7-116">Category</span></span>

<span data-ttu-id="b7aa7-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7aa7-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b7aa7-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="b7aa7-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
