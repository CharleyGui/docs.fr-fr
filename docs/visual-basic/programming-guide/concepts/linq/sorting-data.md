---
title: Tri des données
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f1d4d8afb9b6e176a7ac048ba3270ecafdce24c9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350588"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="f8700-102">Tri des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8700-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="f8700-103">Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="f8700-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="f8700-104">Le premier critère de tri effectue un tri principal sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="f8700-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="f8700-105">En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.</span><span class="sxs-lookup"><span data-stu-id="f8700-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="f8700-106">L’illustration suivante montre les résultats d’une opération de tri alphabétique sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="f8700-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="f8700-108">Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="f8700-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="f8700-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f8700-109">Methods</span></span>

|<span data-ttu-id="f8700-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="f8700-110">Method Name</span></span>|<span data-ttu-id="f8700-111">Description</span><span class="sxs-lookup"><span data-stu-id="f8700-111">Description</span></span>|<span data-ttu-id="f8700-112">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8700-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f8700-113">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f8700-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="f8700-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="f8700-114">OrderBy</span></span>|<span data-ttu-id="f8700-115">Trie les valeurs dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f8700-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="f8700-116">OrderByDescending</span></span>|<span data-ttu-id="f8700-117">Trie les valeurs dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f8700-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f8700-118">ThenBy</span></span>|<span data-ttu-id="f8700-119">Effectue un tri secondaire dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f8700-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="f8700-120">ThenByDescending</span></span>|<span data-ttu-id="f8700-121">Effectue un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f8700-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="f8700-122">Reverse</span></span>|<span data-ttu-id="f8700-123">Inverse l’ordre des éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="f8700-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="f8700-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="f8700-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f8700-125">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="f8700-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="f8700-126">Exemples de tri principal</span><span class="sxs-lookup"><span data-stu-id="f8700-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="f8700-127">Tri principal croissant</span><span class="sxs-lookup"><span data-stu-id="f8700-127">Primary Ascending Sort</span></span>

<span data-ttu-id="f8700-128">L’exemple suivant montre comment utiliser la clause `Order By` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a><span data-ttu-id="f8700-129">Tri principal décroissant</span><span class="sxs-lookup"><span data-stu-id="f8700-129">Primary Descending Sort</span></span>

<span data-ttu-id="f8700-130">L’exemple suivant montre comment utiliser la clause `Order By Descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a><span data-ttu-id="f8700-131">Exemples de tri secondaire</span><span class="sxs-lookup"><span data-stu-id="f8700-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="f8700-132">Tri secondaire croissant</span><span class="sxs-lookup"><span data-stu-id="f8700-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="f8700-133">L’exemple suivant montre comment utiliser la clause `Order By` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="f8700-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="f8700-134">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a><span data-ttu-id="f8700-135">Tri secondaire décroissant</span><span class="sxs-lookup"><span data-stu-id="f8700-135">Secondary Descending Sort</span></span>

<span data-ttu-id="f8700-136">L’exemple suivant montre comment utiliser la clause `Order By Descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="f8700-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="f8700-137">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="f8700-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a><span data-ttu-id="f8700-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8700-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f8700-139">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8700-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f8700-140">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="f8700-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="f8700-141">Guide pratique : trier les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="f8700-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="f8700-142">Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8700-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
