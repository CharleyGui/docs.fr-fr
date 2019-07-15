---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804489"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="696ff-101">HtmlTextWriter n’effectue pas correctement le rendu de l’élément `<br/>`</span><span class="sxs-lookup"><span data-stu-id="696ff-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="696ff-102">Détails</span><span class="sxs-lookup"><span data-stu-id="696ff-102">Details</span></span>|<span data-ttu-id="696ff-103">À compter de la version 4.6 du .NET Framework, l’appel de <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> et <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> avec un élément <code>&lt;BR /&gt;</code> aboutit à l’insertion d’un seul <code>&lt;BR /&gt;</code> (au lieu de deux).</span><span class="sxs-lookup"><span data-stu-id="696ff-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="696ff-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="696ff-104">Suggestion</span></span>|<span data-ttu-id="696ff-105">Si une application dépendait de la balise <code>&lt;BR /&gt;</code> supplémentaire, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> doit être appelé une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="696ff-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="696ff-106">Notez que ce changement de comportement affecte uniquement les applications qui ciblent .NET Framework 4.6 ou les versions ultérieures. Vous pouvez donc également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="696ff-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="696ff-107">Portée</span><span class="sxs-lookup"><span data-stu-id="696ff-107">Scope</span></span>|<span data-ttu-id="696ff-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="696ff-108">Edge</span></span>|
|<span data-ttu-id="696ff-109">Version</span><span class="sxs-lookup"><span data-stu-id="696ff-109">Version</span></span>|<span data-ttu-id="696ff-110">4.6</span><span class="sxs-lookup"><span data-stu-id="696ff-110">4.6</span></span>|
|<span data-ttu-id="696ff-111">Type</span><span class="sxs-lookup"><span data-stu-id="696ff-111">Type</span></span>|<span data-ttu-id="696ff-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="696ff-112">Retargeting</span></span>|
|<span data-ttu-id="696ff-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="696ff-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

