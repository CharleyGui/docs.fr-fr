---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621069"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="3e267-101">Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents</span><span class="sxs-lookup"><span data-stu-id="3e267-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="3e267-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3e267-102">Details</span></span>

<span data-ttu-id="3e267-103"><xref:System.Uri>ne lève plus d’exception <xref:System.NullReferenceException> lors de l’appel <xref:System.Uri.TryCreate%2A> de sur certains URI relatifs contenant du Unicode.</span><span class="sxs-lookup"><span data-stu-id="3e267-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="3e267-104">La reproduction la plus simple du <xref:System.NullReferenceException> est ci-dessous, avec les deux instructions équivalentes :</span><span class="sxs-lookup"><span data-stu-id="3e267-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="3e267-105"><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :</span><span class="sxs-lookup"><span data-stu-id="3e267-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="3e267-106">Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</span><span class="sxs-lookup"><span data-stu-id="3e267-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="3e267-107">L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="3e267-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="3e267-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3e267-108">Suggestion</span></span>

<span data-ttu-id="3e267-109">Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.</span><span class="sxs-lookup"><span data-stu-id="3e267-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="3e267-110">Nom</span><span class="sxs-lookup"><span data-stu-id="3e267-110">Name</span></span>    | <span data-ttu-id="3e267-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="3e267-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e267-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="3e267-112">Scope</span></span>   |<span data-ttu-id="3e267-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3e267-113">Edge</span></span>|
|<span data-ttu-id="3e267-114">Version</span><span class="sxs-lookup"><span data-stu-id="3e267-114">Version</span></span>|<span data-ttu-id="3e267-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3e267-115">4.7.2</span></span>|
|<span data-ttu-id="3e267-116">Type</span><span class="sxs-lookup"><span data-stu-id="3e267-116">Type</span></span>|<span data-ttu-id="3e267-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="3e267-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e267-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="3e267-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
