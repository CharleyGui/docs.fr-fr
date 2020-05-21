---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721625"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="09630-101">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="09630-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="09630-102">Les méthodes d’analyse à virgule flottante ne lèvent plus d’exception <xref:System.OverflowException> ou retournent `false` lorsqu’elles analysent une chaîne dont la valeur numérique est en dehors de la plage du <xref:System.Single> <xref:System.Double> type à virgule flottante ou.</span><span class="sxs-lookup"><span data-stu-id="09630-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="09630-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="09630-103">Change description</span></span>

<span data-ttu-id="09630-104">Dans .NET Core 2,2 et les versions antérieures, <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Single.Parse%2A?displayProperty=nameWithType> méthodes et lèvent un <xref:System.OverflowException> pour les valeurs qui se trouvent en dehors de la plage de leur type respectif.</span><span class="sxs-lookup"><span data-stu-id="09630-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="09630-105">Les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> méthodes et retournent `false` pour les représentations sous forme de chaîne de valeurs numériques hors limites.</span><span class="sxs-lookup"><span data-stu-id="09630-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="09630-106">À compter de .net Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> méthodes,, <xref:System.Single.Parse%2A?displayProperty=nameWithType> et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> n’échouent plus lors de l’analyse de chaînes numériques hors limites.</span><span class="sxs-lookup"><span data-stu-id="09630-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="09630-107">Au lieu de cela, les <xref:System.Double> méthodes d’analyse retournent <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> des valeurs qui dépassent <xref:System.Double.MaxValue?displayProperty=nameWithType> , et elles retournent <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> des valeurs inférieures à <xref:System.Double.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="09630-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="09630-108">De même, les <xref:System.Single> méthodes d’analyse retournent <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pour les valeurs qui dépassent <xref:System.Single.MaxValue?displayProperty=nameWithType> , et elles retournent <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> des valeurs inférieures à <xref:System.Single.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="09630-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="09630-109">Cette modification a été apportée pour améliorer la conformité IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="09630-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="09630-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="09630-110">Version introduced</span></span>

<span data-ttu-id="09630-111">3.0</span><span class="sxs-lookup"><span data-stu-id="09630-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09630-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="09630-112">Recommended action</span></span>

<span data-ttu-id="09630-113">Cette modification peut avoir un impact sur votre code de deux manières :</span><span class="sxs-lookup"><span data-stu-id="09630-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="09630-114">Votre code dépend du gestionnaire du <xref:System.OverflowException> à exécuter lorsqu’un dépassement de capacité se produit.</span><span class="sxs-lookup"><span data-stu-id="09630-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="09630-115">Dans ce cas, vous devez supprimer l' `catch` instruction et placer le code nécessaire dans une `If` instruction qui teste si <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> a `true` la valeur.</span><span class="sxs-lookup"><span data-stu-id="09630-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="09630-116">Votre code suppose que les valeurs à virgule flottante ne le sont pas `Infinity` .</span><span class="sxs-lookup"><span data-stu-id="09630-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="09630-117">Dans ce cas, vous devez ajouter le code nécessaire pour vérifier les valeurs à virgule flottante de `PositiveInfinity` et `NegativeInfinity` .</span><span class="sxs-lookup"><span data-stu-id="09630-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="09630-118">Category</span><span class="sxs-lookup"><span data-stu-id="09630-118">Category</span></span>

<span data-ttu-id="09630-119">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="09630-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09630-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="09630-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
