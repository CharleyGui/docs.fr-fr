---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496872"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="8a813-101">WF sérialise désormais différemment les objets DateTimes Expressions.Literal&lt;T&gt; (il arrête les analyseurs XAML personnalisés)</span><span class="sxs-lookup"><span data-stu-id="8a813-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="8a813-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8a813-102">Details</span></span>

<span data-ttu-id="8a813-103">L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=fullName> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=fullName>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8a813-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="8a813-104">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="8a813-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="8a813-105">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="8a813-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8a813-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8a813-106">Suggestion</span></span>

<span data-ttu-id="8a813-107">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="8a813-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="8a813-108">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="8a813-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="8a813-109">Name</span><span class="sxs-lookup"><span data-stu-id="8a813-109">Name</span></span>    | <span data-ttu-id="8a813-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="8a813-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8a813-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="8a813-111">Scope</span></span>   |<span data-ttu-id="8a813-112">Edge</span><span class="sxs-lookup"><span data-stu-id="8a813-112">Edge</span></span>|
|<span data-ttu-id="8a813-113">Version</span><span class="sxs-lookup"><span data-stu-id="8a813-113">Version</span></span>|<span data-ttu-id="8a813-114">4,5</span><span class="sxs-lookup"><span data-stu-id="8a813-114">4.5</span></span>|
|<span data-ttu-id="8a813-115">Type</span><span class="sxs-lookup"><span data-stu-id="8a813-115">Type</span></span>|<span data-ttu-id="8a813-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8a813-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8a813-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="8a813-117">Affected APIs</span></span>

<span data-ttu-id="8a813-118">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8a813-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
