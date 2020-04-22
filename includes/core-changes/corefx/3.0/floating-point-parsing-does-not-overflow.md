---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021636"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="23d78-101">Les opérations d’analyse des points flottants ne échouent plus ou ne jettent plus de OverflowException</span><span class="sxs-lookup"><span data-stu-id="23d78-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="23d78-102">Les méthodes d’analyse des points <xref:System.OverflowException> flottants `false` ne jettent plus une ou une déclaration <xref:System.Single> lorsqu’elles analysent une chaîne dont la valeur numérique est hors de la portée du type de point flottant. <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="23d78-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="23d78-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="23d78-103">Change description</span></span>

<span data-ttu-id="23d78-104">Dans .NET Core 2.2 et <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Single.Parse%2A?displayProperty=nameWithType> versions <xref:System.OverflowException> antérieures, le et les méthodes jettent un pour les valeurs qui en dehors de la gamme de leur type respectif.</span><span class="sxs-lookup"><span data-stu-id="23d78-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="23d78-105">Les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> et `false` les méthodes reviennent pour les représentations de cordes de valeurs numériques hors de portée.</span><span class="sxs-lookup"><span data-stu-id="23d78-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="23d78-106">En commençant par .NET Core 3.0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>le , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> les méthodes ne manquent plus lors de l’analyse des chaînes numériques hors de portée.</span><span class="sxs-lookup"><span data-stu-id="23d78-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="23d78-107">Au lieu <xref:System.Double> de cela, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> les méthodes <xref:System.Double.MaxValue?displayProperty=nameWithType>d’analyse <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> reviennent pour les <xref:System.Double.MinValue?displayProperty=nameWithType>valeurs qui dépassent , et ils reviennent pour des valeurs qui sont inférieures à .</span><span class="sxs-lookup"><span data-stu-id="23d78-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="23d78-108">De même, les <xref:System.Single> méthodes <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> d’analyse <xref:System.Single.MaxValue?displayProperty=nameWithType>reviennent pour <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> les valeurs qui <xref:System.Single.MinValue?displayProperty=nameWithType>dépassent , et elles reviennent pour des valeurs qui sont inférieures à .</span><span class="sxs-lookup"><span data-stu-id="23d78-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="23d78-109">Ce changement a été apporté pour améliorer la conformité IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="23d78-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="23d78-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="23d78-110">Version introduced</span></span>

<span data-ttu-id="23d78-111">3.0</span><span class="sxs-lookup"><span data-stu-id="23d78-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="23d78-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="23d78-112">Recommended action</span></span>

<span data-ttu-id="23d78-113">Cette modification peut affecter votre code de deux façons :</span><span class="sxs-lookup"><span data-stu-id="23d78-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="23d78-114">Votre code dépend du <xref:System.OverflowException> gestionnaire pour que le gestionnaire s’exécute lorsqu’un débordement se produit.</span><span class="sxs-lookup"><span data-stu-id="23d78-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="23d78-115">Dans ce cas, vous `catch` devez supprimer la déclaration `If` et placer <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> tout `true`code nécessaire dans une déclaration qui teste si ou est .</span><span class="sxs-lookup"><span data-stu-id="23d78-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="23d78-116">Votre code suppose que les valeurs `Infinity`de point flottant ne sont pas .</span><span class="sxs-lookup"><span data-stu-id="23d78-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="23d78-117">Dans ce cas, vous devez ajouter le code nécessaire `PositiveInfinity` `NegativeInfinity`pour vérifier les valeurs de point flottant de et .</span><span class="sxs-lookup"><span data-stu-id="23d78-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="23d78-118">Category</span><span class="sxs-lookup"><span data-stu-id="23d78-118">Category</span></span>

<span data-ttu-id="23d78-119">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="23d78-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23d78-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="23d78-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
