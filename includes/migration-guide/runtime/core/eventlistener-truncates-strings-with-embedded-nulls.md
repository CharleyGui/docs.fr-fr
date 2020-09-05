---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497391"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="b04f5-101">EventListener tronque les chaînes comportant des valeurs Null incorporées</span><span class="sxs-lookup"><span data-stu-id="b04f5-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="b04f5-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b04f5-102">Details</span></span>

<span data-ttu-id="b04f5-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> tronque les chaînes comportant des valeurs null incorporées.</span><span class="sxs-lookup"><span data-stu-id="b04f5-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="b04f5-104">Les caractères Null ne sont pas pris en charge par la classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b04f5-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="b04f5-105">La modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> pour lire des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus et qui utilisent des caractères Null comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="b04f5-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b04f5-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b04f5-106">Suggestion</span></span>

<span data-ttu-id="b04f5-107">Les données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> doivent être, si possible, mises à jour pour ne pas utiliser les caractères Null incorporés.</span><span class="sxs-lookup"><span data-stu-id="b04f5-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="b04f5-108">Name</span><span class="sxs-lookup"><span data-stu-id="b04f5-108">Name</span></span>    | <span data-ttu-id="b04f5-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="b04f5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b04f5-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="b04f5-110">Scope</span></span>   |<span data-ttu-id="b04f5-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b04f5-111">Edge</span></span>|
|<span data-ttu-id="b04f5-112">Version</span><span class="sxs-lookup"><span data-stu-id="b04f5-112">Version</span></span>|<span data-ttu-id="b04f5-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b04f5-113">4.5.1</span></span>|
|<span data-ttu-id="b04f5-114">Type</span><span class="sxs-lookup"><span data-stu-id="b04f5-114">Type</span></span>|<span data-ttu-id="b04f5-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b04f5-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b04f5-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="b04f5-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->
