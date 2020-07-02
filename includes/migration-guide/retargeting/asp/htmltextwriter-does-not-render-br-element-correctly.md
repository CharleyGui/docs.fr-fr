---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615651"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="5a8f6-101">HtmlTextWriter n’affiche pas correctement l’élément `<br/>`</span><span class="sxs-lookup"><span data-stu-id="5a8f6-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="5a8f6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5a8f6-102">Details</span></span>

<span data-ttu-id="5a8f6-103">À partir de .NET Framework 4.6, l’appel de <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> et de <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> avec un élément `<BR />` insère correctement un seul `<BR />` (au lieu de deux)</span><span class="sxs-lookup"><span data-stu-id="5a8f6-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a8f6-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5a8f6-104">Suggestion</span></span>

<span data-ttu-id="5a8f6-105">Si une application dépendait de la balise `<BR />` supplémentaire, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> doit être appelé une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="5a8f6-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="5a8f6-106">Notez que ce changement de comportement affecte uniquement les applications qui ciblent .NET Framework 4.6 ou les versions ultérieures. Vous pouvez donc également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="5a8f6-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="5a8f6-107">Nom</span><span class="sxs-lookup"><span data-stu-id="5a8f6-107">Name</span></span>    | <span data-ttu-id="5a8f6-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="5a8f6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a8f6-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="5a8f6-109">Scope</span></span>   | <span data-ttu-id="5a8f6-110">Edge</span><span class="sxs-lookup"><span data-stu-id="5a8f6-110">Edge</span></span>        |
| <span data-ttu-id="5a8f6-111">Version</span><span class="sxs-lookup"><span data-stu-id="5a8f6-111">Version</span></span> | <span data-ttu-id="5a8f6-112">4.6</span><span class="sxs-lookup"><span data-stu-id="5a8f6-112">4.6</span></span>         |
| <span data-ttu-id="5a8f6-113">Type</span><span class="sxs-lookup"><span data-stu-id="5a8f6-113">Type</span></span>    | <span data-ttu-id="5a8f6-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5a8f6-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5a8f6-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="5a8f6-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
