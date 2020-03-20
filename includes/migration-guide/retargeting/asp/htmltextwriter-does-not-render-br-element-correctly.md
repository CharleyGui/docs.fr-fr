---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804489"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="b6442-101">HtmlTextWriter n’affiche pas correctement l’élément `<br/>`</span><span class="sxs-lookup"><span data-stu-id="b6442-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b6442-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b6442-102">Details</span></span>|<span data-ttu-id="b6442-103">À partir de .NET Framework 4.6, l’appel de <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> et de <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> avec un élément <code>&lt;BR /&gt;</code> insère correctement un seul <code>&lt;BR /&gt;</code> (au lieu de deux)</span><span class="sxs-lookup"><span data-stu-id="b6442-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="b6442-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b6442-104">Suggestion</span></span>|<span data-ttu-id="b6442-105">Si une application dépendait de la balise <code>&lt;BR /&gt;</code> supplémentaire, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> doit être appelé une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="b6442-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="b6442-106">Notez que ce changement de comportement affecte uniquement les applications qui ciblent .NET Framework 4.6 ou les versions ultérieures. Vous pouvez donc également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="b6442-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="b6442-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="b6442-107">Scope</span></span>|<span data-ttu-id="b6442-108">Edge</span><span class="sxs-lookup"><span data-stu-id="b6442-108">Edge</span></span>|
|<span data-ttu-id="b6442-109">Version</span><span class="sxs-lookup"><span data-stu-id="b6442-109">Version</span></span>|<span data-ttu-id="b6442-110">4.6</span><span class="sxs-lookup"><span data-stu-id="b6442-110">4.6</span></span>|
|<span data-ttu-id="b6442-111">Type</span><span class="sxs-lookup"><span data-stu-id="b6442-111">Type</span></span>|<span data-ttu-id="b6442-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="b6442-112">Retargeting</span></span>|
|<span data-ttu-id="b6442-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="b6442-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
