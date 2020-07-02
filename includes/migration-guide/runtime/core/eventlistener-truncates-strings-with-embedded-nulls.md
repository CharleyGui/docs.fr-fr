---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619967"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="11341-101">EventListener tronque les chaînes comportant des valeurs Null incorporées</span><span class="sxs-lookup"><span data-stu-id="11341-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="11341-102">Détails</span><span class="sxs-lookup"><span data-stu-id="11341-102">Details</span></span>

<span data-ttu-id="11341-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> tronque les chaînes comportant des valeurs null incorporées.</span><span class="sxs-lookup"><span data-stu-id="11341-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="11341-104">Les caractères Null ne sont pas pris en charge par la classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="11341-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="11341-105">La modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> pour lire des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus et qui utilisent des caractères Null comme délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="11341-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="11341-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="11341-106">Suggestion</span></span>

<span data-ttu-id="11341-107">Les données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> doivent être, si possible, mises à jour pour ne pas utiliser les caractères Null incorporés.</span><span class="sxs-lookup"><span data-stu-id="11341-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="11341-108">Nom</span><span class="sxs-lookup"><span data-stu-id="11341-108">Name</span></span>    | <span data-ttu-id="11341-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="11341-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="11341-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="11341-110">Scope</span></span>   |<span data-ttu-id="11341-111">Edge</span><span class="sxs-lookup"><span data-stu-id="11341-111">Edge</span></span>|
|<span data-ttu-id="11341-112">Version</span><span class="sxs-lookup"><span data-stu-id="11341-112">Version</span></span>|<span data-ttu-id="11341-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="11341-113">4.5.1</span></span>|
|<span data-ttu-id="11341-114">Type</span><span class="sxs-lookup"><span data-stu-id="11341-114">Type</span></span>|<span data-ttu-id="11341-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="11341-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11341-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="11341-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
