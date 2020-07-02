---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620076"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="02d2b-101">WF sérialise désormais différemment les objets DateTimes Expressions.Literal&lt;T&gt; (il arrête les analyseurs XAML personnalisés)</span><span class="sxs-lookup"><span data-stu-id="02d2b-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="02d2b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="02d2b-102">Details</span></span>

<span data-ttu-id="02d2b-103">L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=fullName> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=fullName>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="02d2b-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="02d2b-104">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="02d2b-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="02d2b-105">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="02d2b-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="02d2b-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="02d2b-106">Suggestion</span></span>

<span data-ttu-id="02d2b-107">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="02d2b-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="02d2b-108">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="02d2b-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="02d2b-109">Nom</span><span class="sxs-lookup"><span data-stu-id="02d2b-109">Name</span></span>    | <span data-ttu-id="02d2b-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="02d2b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="02d2b-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="02d2b-111">Scope</span></span>   |<span data-ttu-id="02d2b-112">Edge</span><span class="sxs-lookup"><span data-stu-id="02d2b-112">Edge</span></span>|
|<span data-ttu-id="02d2b-113">Version</span><span class="sxs-lookup"><span data-stu-id="02d2b-113">Version</span></span>|<span data-ttu-id="02d2b-114">4,5</span><span class="sxs-lookup"><span data-stu-id="02d2b-114">4.5</span></span>|
|<span data-ttu-id="02d2b-115">Type</span><span class="sxs-lookup"><span data-stu-id="02d2b-115">Type</span></span>|<span data-ttu-id="02d2b-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="02d2b-116">Runtime</span></span>|
