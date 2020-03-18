---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198421"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="e05b7-101">HTTP : Changements dans l’infrastructure du corps d’intervention</span><span class="sxs-lookup"><span data-stu-id="e05b7-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="e05b7-102">L’infrastructure soutenant un organisme de réponse HTTP a changé.</span><span class="sxs-lookup"><span data-stu-id="e05b7-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="e05b7-103">Si vous utilisez `HttpResponse` directement, vous ne devriez pas avoir besoin d’apporter des modifications de code.</span><span class="sxs-lookup"><span data-stu-id="e05b7-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="e05b7-104">Lire la suite si vous `HttpResponse.Body` enveloppez, `HttpContext.Features`remplacez ou accédez .</span><span class="sxs-lookup"><span data-stu-id="e05b7-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e05b7-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e05b7-105">Version introduced</span></span>

<span data-ttu-id="e05b7-106">3.0</span><span class="sxs-lookup"><span data-stu-id="e05b7-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e05b7-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="e05b7-107">Old behavior</span></span>

<span data-ttu-id="e05b7-108">Il y avait trois API associées à l’organisme de réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="e05b7-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="e05b7-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="e05b7-109">New behavior</span></span>

<span data-ttu-id="e05b7-110">Si vous `HttpResponse.Body`remplacez, il `IHttpResponseBodyFeature` remplace l’ensemble par `StreamResponseBodyFeature` un emballage autour de votre flux donné en utilisant pour fournir des implémentations par défaut pour toutes les API attendues.</span><span class="sxs-lookup"><span data-stu-id="e05b7-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="e05b7-111">Le réglage du flux d’origine renvoie ce changement.</span><span class="sxs-lookup"><span data-stu-id="e05b7-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e05b7-112">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="e05b7-112">Reason for change</span></span>

<span data-ttu-id="e05b7-113">La motivation est de combiner les API du corps de réponse en une seule nouvelle interface de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e05b7-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e05b7-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e05b7-114">Recommended action</span></span>

<span data-ttu-id="e05b7-115">Utilisez `IHttpResponseBodyFeature` où vous `IHttpResponseFeature.Body` `IHttpSendFileFeature`utilisiez auparavant, , ou `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="e05b7-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="e05b7-116">Category</span><span class="sxs-lookup"><span data-stu-id="e05b7-116">Category</span></span>

<span data-ttu-id="e05b7-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e05b7-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e05b7-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="e05b7-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
