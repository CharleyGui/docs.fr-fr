---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496710"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="8dfa4-101">Correctif ASP.NET sur la gestion de InputAttributes et LabelAttributes du contrôle WebForms CheckBox</span><span class="sxs-lookup"><span data-stu-id="8dfa4-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="8dfa4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8dfa4-102">Details</span></span>

<span data-ttu-id="8dfa4-103">Pour les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> qui sont ajoutés programmatiquement à un contrôle <xref:System.Web.UI.WebControls.CheckBox> WebForms sont perdus après la publication (postback).</span><span class="sxs-lookup"><span data-stu-id="8dfa4-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="8dfa4-104">Pour les applications qui ciblent .NET Framework 4.8 ou versions ultérieures, ils sont conservés après la publication (postback).</span><span class="sxs-lookup"><span data-stu-id="8dfa4-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8dfa4-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8dfa4-105">Suggestion</span></span>

<span data-ttu-id="8dfa4-106">Pour obtenir le bon comportement de restauration des attributs lors de la publication (postback), définissez <code>targetFrameworkVersion</code> sur 4.8 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="8dfa4-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="8dfa4-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8dfa4-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="8dfa4-108">La définir avec une version antérieure ou ne pas la définir du tout revient à conserver l’ancien comportement incorrect.</span><span class="sxs-lookup"><span data-stu-id="8dfa4-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="8dfa4-109">Name</span><span class="sxs-lookup"><span data-stu-id="8dfa4-109">Name</span></span>    | <span data-ttu-id="8dfa4-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="8dfa4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8dfa4-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="8dfa4-111">Scope</span></span>   |<span data-ttu-id="8dfa4-112">Unknown</span><span class="sxs-lookup"><span data-stu-id="8dfa4-112">Unknown</span></span>|
|<span data-ttu-id="8dfa4-113">Version</span><span class="sxs-lookup"><span data-stu-id="8dfa4-113">Version</span></span>|<span data-ttu-id="8dfa4-114">4.8</span><span class="sxs-lookup"><span data-stu-id="8dfa4-114">4.8</span></span>|
|<span data-ttu-id="8dfa4-115">Type</span><span class="sxs-lookup"><span data-stu-id="8dfa4-115">Type</span></span>|<span data-ttu-id="8dfa4-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8dfa4-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8dfa4-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="8dfa4-117">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
