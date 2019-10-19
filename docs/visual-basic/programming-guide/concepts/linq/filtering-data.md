---
title: Filtrage des données (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 27765247daa2155e685b1cd2bfccebb3216ca672
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582439"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="074bd-102">Filtrage des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074bd-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="074bd-103">Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="074bd-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="074bd-104">Cette opération est également appelée « sélection ».</span><span class="sxs-lookup"><span data-stu-id="074bd-104">It is also known as selection.</span></span>

<span data-ttu-id="074bd-105">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="074bd-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="074bd-106">Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="074bd-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="074bd-108">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="074bd-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="074bd-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="074bd-109">Methods</span></span>

|<span data-ttu-id="074bd-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="074bd-110">Method Name</span></span>|<span data-ttu-id="074bd-111">Description</span><span class="sxs-lookup"><span data-stu-id="074bd-111">Description</span></span>|<span data-ttu-id="074bd-112">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="074bd-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="074bd-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="074bd-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="074bd-114">OfType</span><span class="sxs-lookup"><span data-stu-id="074bd-114">OfType</span></span>|<span data-ttu-id="074bd-115">Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="074bd-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="074bd-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="074bd-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="074bd-117">Où</span><span class="sxs-lookup"><span data-stu-id="074bd-117">Where</span></span>|<span data-ttu-id="074bd-118">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="074bd-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="074bd-119">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="074bd-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="074bd-120">L’exemple suivant utilise la `Where` pour filtrer à partir d’un tableau les chaînes qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="074bd-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="074bd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="074bd-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="074bd-122">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074bd-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="074bd-123">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="074bd-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="074bd-124">Guide pratique : filtrer les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="074bd-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="074bd-125">Comment : interroger les métadonnées d’un assembly avec la réflexion (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074bd-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="074bd-126">Comment : interroger des fichiers ayant un attribut ou un nom spécifié (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074bd-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="074bd-127">Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074bd-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
