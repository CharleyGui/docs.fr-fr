---
ms.openlocfilehash: 3c32d2e13447f8fd9aa6b185b5fc7e60f9e1bb61
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496187"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="962dc-101">Prise en charge d’une notation d’URI relatif spéciale quand des caractères Unicode sont présents</span><span class="sxs-lookup"><span data-stu-id="962dc-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="962dc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="962dc-102">Details</span></span>

<span data-ttu-id="962dc-103"><xref:System.Uri> ne lève plus d’exception <xref:System.NullReferenceException> lors de l’appel <xref:System.Uri.TryCreate%2A> de sur certains URI relatifs contenant du Unicode.</span><span class="sxs-lookup"><span data-stu-id="962dc-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="962dc-104">La reproduction la plus simple du <xref:System.NullReferenceException> est ci-dessous, avec les deux instructions équivalentes :</span><span class="sxs-lookup"><span data-stu-id="962dc-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="962dc-105"><xref:System.NullReferenceException> ne peut être reproduite que si les conditions suivantes sont réunies :</span><span class="sxs-lookup"><span data-stu-id="962dc-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="962dc-106">Vous devez spécifier l’URI comme étant relatif en le faisant précéder de « http: » sans le faire suivre de « // ».</span><span class="sxs-lookup"><span data-stu-id="962dc-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="962dc-107">L’URI doit contenir des symboles non réservés ou Unicode encodés en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="962dc-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="962dc-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="962dc-108">Suggestion</span></span>

<span data-ttu-id="962dc-109">Les utilisateurs qui dépendent de ce comportement pour interdire les URI relatifs doivent spécifier <xref:System.UriKind.Absolute?displayProperty=nameWithType> à la place quand ils créent un URI.</span><span class="sxs-lookup"><span data-stu-id="962dc-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="962dc-110">Name</span><span class="sxs-lookup"><span data-stu-id="962dc-110">Name</span></span>    | <span data-ttu-id="962dc-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="962dc-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="962dc-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="962dc-112">Scope</span></span>   |<span data-ttu-id="962dc-113">Edge</span><span class="sxs-lookup"><span data-stu-id="962dc-113">Edge</span></span>|
|<span data-ttu-id="962dc-114">Version</span><span class="sxs-lookup"><span data-stu-id="962dc-114">Version</span></span>|<span data-ttu-id="962dc-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="962dc-115">4.7.2</span></span>|
|<span data-ttu-id="962dc-116">Type</span><span class="sxs-lookup"><span data-stu-id="962dc-116">Type</span></span>|<span data-ttu-id="962dc-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="962dc-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="962dc-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="962dc-118">Affected APIs</span></span>

- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)`
- `M:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)`
- `M:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)`

-->
