---
title: Opérations de projection
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 4795bdaba53949b34fe380ea9c51025ce43c40db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396335"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="98fe0-102">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fe0-102">Projection Operations (Visual Basic)</span></span>

<span data-ttu-id="98fe0-103">La projection désigne l’opération de transformation d’un objet en une nouvelle forme qui se compose souvent uniquement des propriétés à utiliser ensuite.</span><span class="sxs-lookup"><span data-stu-id="98fe0-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="98fe0-104">À l'aide de la projection, vous pouvez créer un nouveau type qui est généré à partir de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="98fe0-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="98fe0-105">Vous pouvez projeter une propriété et effectuer une fonction mathématique sur celle-ci.</span><span class="sxs-lookup"><span data-stu-id="98fe0-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="98fe0-106">Vous pouvez également projeter l’objet d’origine sans le modifier.</span><span class="sxs-lookup"><span data-stu-id="98fe0-106">You can also project the original object without changing it.</span></span>

<span data-ttu-id="98fe0-107">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de projection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="98fe0-107">The standard query operator methods that perform projection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="98fe0-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="98fe0-108">Methods</span></span>

|<span data-ttu-id="98fe0-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="98fe0-109">Method Name</span></span>|<span data-ttu-id="98fe0-110">Description</span><span class="sxs-lookup"><span data-stu-id="98fe0-110">Description</span></span>|<span data-ttu-id="98fe0-111">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98fe0-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="98fe0-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="98fe0-112">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="98fe0-113">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="98fe0-113">Select</span></span>|<span data-ttu-id="98fe0-114">Projette les valeurs qui sont basées sur une fonction de transformation.</span><span class="sxs-lookup"><span data-stu-id="98fe0-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|<span data-ttu-id="98fe0-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="98fe0-115">SelectMany</span></span>|<span data-ttu-id="98fe0-116">Projette les séquences de valeurs qui sont basées sur une fonction de transformation, puis les aplatit en une seule séquence.</span><span class="sxs-lookup"><span data-stu-id="98fe0-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="98fe0-117">Utilisation de plusieurs clauses `From`</span><span class="sxs-lookup"><span data-stu-id="98fe0-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="98fe0-118">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="98fe0-118">Query Expression Syntax Examples</span></span>

### <a name="select"></a><span data-ttu-id="98fe0-119">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="98fe0-119">Select</span></span>

<span data-ttu-id="98fe0-120">L’exemple suivant utilise la clause `Select` pour projeter la première lettre de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="98fe0-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a><span data-ttu-id="98fe0-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="98fe0-121">SelectMany</span></span>

<span data-ttu-id="98fe0-122">L’exemple suivant utilise plusieurs `From` clauses pour projeter chaque mot de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="98fe0-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a><span data-ttu-id="98fe0-123">Comparaison de Select et SelectMany</span><span class="sxs-lookup"><span data-stu-id="98fe0-123">Select versus SelectMany</span></span>

<span data-ttu-id="98fe0-124">Les deux clauses `Select()` et `SelectMany()` retournent une valeur de résultat (ou des valeurs) à partir des valeurs sources.</span><span class="sxs-lookup"><span data-stu-id="98fe0-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="98fe0-125">`Select()` retourne une seule valeur de résultat pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="98fe0-126">Le résultat global est donc une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="98fe0-127">En revanche, `SelectMany()` retourne un résultat global unique qui contient des sous-collections concaténées à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="98fe0-128">La fonction de transformation qui est passée comme argument à `SelectMany()` doit retourner une séquence énumérable de valeurs pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="98fe0-129">Ces séquences énumérables sont ensuite concaténées par `SelectMany()` pour créer une seule grande séquence.</span><span class="sxs-lookup"><span data-stu-id="98fe0-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>

<span data-ttu-id="98fe0-130">Les deux illustrations suivantes montrent en quoi les actions de ces deux méthodes sont différentes d’un point de vue conceptuel.</span><span class="sxs-lookup"><span data-stu-id="98fe0-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="98fe0-131">Dans chaque cas, supposons que la fonction (de transformation) du sélecteur sélectionne le tableau de fleurs (Flowers) à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>

<span data-ttu-id="98fe0-132">Cette illustration montre de quelle manière `Select()` retourne une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>

![Graphique montrant l’action de Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)

<span data-ttu-id="98fe0-134">Cette illustration montre de quelle façon `SelectMany()` concatène la séquence intermédiaire de tableaux en une seule valeur de résultat final qui contient chaque valeur de chaque tableau intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="98fe0-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>

![Graphique montrant l’action de SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a><span data-ttu-id="98fe0-136">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="98fe0-136">Code Example</span></span>

<span data-ttu-id="98fe0-137">L’exemple suivant compare le comportement de `Select()` et de `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="98fe0-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="98fe0-138">Le code crée un « bouquet » de fleurs en prenant les deux premiers éléments de chaque liste de noms de fleurs de la collection source.</span><span class="sxs-lookup"><span data-stu-id="98fe0-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="98fe0-139">Dans cet exemple, la « valeur unique » que la fonction de transformation <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> utilise est elle-même une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="98fe0-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="98fe0-140">Cela nécessite d’utiliser la boucle `For Each` supplémentaire pour énumérer chaque chaîne dans chaque sous-séquence.</span><span class="sxs-lookup"><span data-stu-id="98fe0-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a><span data-ttu-id="98fe0-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98fe0-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="98fe0-142">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fe0-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="98fe0-143">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="98fe0-143">Select Clause</span></span>](../../../language-reference/queries/select-clause.md)
- [<span data-ttu-id="98fe0-144">Guide pratique : combiner des données avec des jointures</span><span class="sxs-lookup"><span data-stu-id="98fe0-144">How to: Combine Data with Joins</span></span>](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="98fe0-145">Comment : remplir des collections d’objets à partir de plusieurs sources (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fe0-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="98fe0-146">Guide pratique : retourner un résultat de requête LINQ comme type spécifique</span><span class="sxs-lookup"><span data-stu-id="98fe0-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="98fe0-147">Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fe0-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
