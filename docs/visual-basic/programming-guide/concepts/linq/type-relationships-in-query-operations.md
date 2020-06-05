---
title: Relations des types dans des opérations de requête
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406727"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="830c4-102">Relations des types dans des opérations de requête (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="830c4-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="830c4-103">Les variables utilisées dans les opérations de requête LINQ (Language-Integrated Query) sont fortement typées et doivent être compatibles les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="830c4-103">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="830c4-104">Le typage fort est utilisé dans la source de données, dans la requête elle-même et dans l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="830c4-105">L’illustration suivante identifie les termes utilisés pour décrire une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="830c4-105">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="830c4-106">Pour plus d’informations sur les parties d’une requête, consultez [opérations de requête de base (Visual Basic)](basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="830c4-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![Capture d’écran montrant une requête de pseudocode avec les éléments mis en surbrillance.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="830c4-108">Le type de la variable de portée dans la requête doit être compatible avec le type des éléments dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="830c4-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="830c4-109">Le type de la variable de requête doit être compatible avec l’élément Sequence défini dans la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="830c4-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="830c4-110">Enfin, le type des éléments de séquence doit également être compatible avec le type de la variable de contrôle de boucle utilisé dans l' `For Each` instruction qui exécute la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="830c4-111">Ce typage fort facilite l’identification des erreurs de type au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="830c4-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="830c4-112">Visual Basic rend le typage fort commode en implémentant l’inférence de type local, également appelée *typage implicite*.</span><span class="sxs-lookup"><span data-stu-id="830c4-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="830c4-113">Cette fonctionnalité est utilisée dans l’exemple précédent, et vous verrez qu’elle est utilisée dans les exemples et la documentation LINQ.</span><span class="sxs-lookup"><span data-stu-id="830c4-113">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="830c4-114">Dans Visual Basic, l’inférence de type local est effectuée simplement à l’aide d’une `Dim` instruction sans `As` clause.</span><span class="sxs-lookup"><span data-stu-id="830c4-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="830c4-115">Dans l’exemple suivant, `city` est fortement typé en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="830c4-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="830c4-116">L’inférence de type local fonctionne uniquement lorsque `Option Infer` a la valeur `On` .</span><span class="sxs-lookup"><span data-stu-id="830c4-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="830c4-117">Pour plus d’informations, consultez [instruction Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="830c4-117">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="830c4-118">Toutefois, même si vous utilisez l’inférence de type local dans une requête, les mêmes relations de type sont présentes parmi les variables dans la source de données, la variable de requête et la boucle d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="830c4-119">Il est utile d’avoir une compréhension de base de ces relations de types lorsque vous écrivez des requêtes LINQ, ou d’utiliser les exemples et des exemples de code dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="830c4-119">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="830c4-120">Vous devrez peut-être spécifier un type explicite pour une variable de portée qui ne correspond pas au type retourné par la source de données.</span><span class="sxs-lookup"><span data-stu-id="830c4-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="830c4-121">Vous pouvez spécifier le type de la variable de portée à l’aide d’une `As` clause.</span><span class="sxs-lookup"><span data-stu-id="830c4-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="830c4-122">Toutefois, cela génère une erreur si la conversion est une [conversion restrictive](../../language-features/data-types/widening-and-narrowing-conversions.md) et a la `Option Strict` valeur `On` .</span><span class="sxs-lookup"><span data-stu-id="830c4-122">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="830c4-123">Par conséquent, nous vous recommandons d’effectuer la conversion sur les valeurs récupérées à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="830c4-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="830c4-124">Vous pouvez convertir les valeurs de la source de données en type de variable de portée explicite à l’aide de la <xref:System.Linq.Enumerable.Cast%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="830c4-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="830c4-125">Vous pouvez également effectuer un cast des valeurs sélectionnées dans la `Select` clause en un type explicite différent du type de la variable de portée.</span><span class="sxs-lookup"><span data-stu-id="830c4-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="830c4-126">Ces points sont illustrés dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="830c4-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="830c4-127">Requêtes qui retournent des éléments entiers des données sources</span><span class="sxs-lookup"><span data-stu-id="830c4-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="830c4-128">L’exemple suivant montre une opération de requête LINQ qui retourne une séquence d’éléments sélectionnés à partir des données sources.</span><span class="sxs-lookup"><span data-stu-id="830c4-128">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="830c4-129">La source, `names` , contient un tableau de chaînes et le résultat de la requête est une séquence contenant des chaînes qui commencent par la lettre M.</span><span class="sxs-lookup"><span data-stu-id="830c4-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="830c4-130">Cela est équivalent au code suivant, mais est beaucoup plus petit et plus facile à écrire.</span><span class="sxs-lookup"><span data-stu-id="830c4-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="830c4-131">La dépendance à l’inférence de type local dans les requêtes est le style par défaut dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="830c4-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="830c4-132">Les relations suivantes existent dans les deux exemples de code précédents, que les types soient déterminés implicitement ou explicitement.</span><span class="sxs-lookup"><span data-stu-id="830c4-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="830c4-133">Le type des éléments dans la source de données, `names` , est le type de la variable de portée, `name` , dans la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="830c4-134">Le type de l’objet sélectionné, `name` , détermine le type de la variable de requête, `mNames` .</span><span class="sxs-lookup"><span data-stu-id="830c4-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="830c4-135">Voici `name` une chaîne, donc la variable de requête est IEnumerable (Of String) dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="830c4-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="830c4-136">La requête définie dans `mNames` est exécutée dans la `For Each` boucle.</span><span class="sxs-lookup"><span data-stu-id="830c4-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="830c4-137">La boucle itère au sein du résultat de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="830c4-138">Étant donné que `mNames` , lorsqu’il est exécuté, retourne une séquence de chaînes, la variable d’itération de la boucle, `nm` , est également une chaîne.</span><span class="sxs-lookup"><span data-stu-id="830c4-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="830c4-139">Requêtes qui retournent un champ à partir des éléments sélectionnés</span><span class="sxs-lookup"><span data-stu-id="830c4-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="830c4-140">L’exemple suivant montre une [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] opération de requête qui retourne une séquence contenant une seule partie de chaque élément sélectionné à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="830c4-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="830c4-141">La requête prend une collection d' `Customer` objets comme source de données et projette uniquement la `Name` propriété dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="830c4-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="830c4-142">Étant donné que le nom du client est une chaîne, la requête produit une séquence de chaînes en sortie.</span><span class="sxs-lookup"><span data-stu-id="830c4-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="830c4-143">Les relations entre les variables sont similaires à celles de l’exemple plus simple.</span><span class="sxs-lookup"><span data-stu-id="830c4-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="830c4-144">Le type des éléments dans la source de données, `customers` , est le type de la variable de portée, `cust` , dans la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="830c4-145">Dans cet exemple, ce type est `Customer` .</span><span class="sxs-lookup"><span data-stu-id="830c4-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="830c4-146">L' `Select` instruction retourne la `Name` propriété de chaque `Customer` objet au lieu de l’objet entier.</span><span class="sxs-lookup"><span data-stu-id="830c4-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="830c4-147">Étant donné que `Name` est une chaîne, la variable de requête, `custNames` , sera à nouveau IEnumerable (Of String), et non de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="830c4-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="830c4-148">Étant donné que `custNames` représente une séquence de chaînes, la `For Each` variable d’itération de la boucle, `custName` , doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="830c4-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="830c4-149">Sans inférence de type local, l’exemple précédent serait plus fastidieux à écrire et à comprendre, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="830c4-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="830c4-150">Requêtes qui requièrent des types anonymes</span><span class="sxs-lookup"><span data-stu-id="830c4-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="830c4-151">L’exemple suivant illustre une situation plus complexe.</span><span class="sxs-lookup"><span data-stu-id="830c4-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="830c4-152">Dans l’exemple précédent, il était fastidieux de spécifier explicitement des types pour toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="830c4-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="830c4-153">Dans cet exemple, il est impossible.</span><span class="sxs-lookup"><span data-stu-id="830c4-153">In this example, it is impossible.</span></span> <span data-ttu-id="830c4-154">Au lieu de sélectionner des éléments entiers `Customer` dans la source de données, ou un champ unique à partir de chaque élément, la `Select` clause de cette requête retourne deux propriétés de l’objet d’origine `Customer` : `Name` et `City` .</span><span class="sxs-lookup"><span data-stu-id="830c4-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="830c4-155">En réponse à la `Select` clause, le compilateur définit un type anonyme qui contient ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="830c4-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="830c4-156">Le résultat de l’exécution de `nameCityQuery` la `For Each` boucle est une collection d’instances du nouveau type anonyme.</span><span class="sxs-lookup"><span data-stu-id="830c4-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="830c4-157">Étant donné que le type anonyme n’a pas de nom utilisable, vous ne pouvez pas spécifier le type de `nameCityQuery` ou `custInfo` explicitement.</span><span class="sxs-lookup"><span data-stu-id="830c4-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="830c4-158">Autrement dit, avec un type anonyme, vous n’avez pas de nom de type à utiliser à la place de `String` dans `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="830c4-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="830c4-159">Pour plus d’informations, consultez [types anonymes](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="830c4-159">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="830c4-160">Bien qu’il ne soit pas possible de spécifier des types pour toutes les variables dans l’exemple précédent, les relations restent les mêmes.</span><span class="sxs-lookup"><span data-stu-id="830c4-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="830c4-161">Le type des éléments dans la source de données est de nouveau le type de la variable de portée dans la requête.</span><span class="sxs-lookup"><span data-stu-id="830c4-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="830c4-162">Dans cet exemple, `cust` est une instance de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="830c4-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="830c4-163">Étant donné que l' `Select` instruction produit un type anonyme, la variable de requête, `nameCityQuery` , doit être implicitement typée comme un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="830c4-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="830c4-164">Un type anonyme n’a pas de nom utilisable et, par conséquent, ne peut pas être spécifié explicitement.</span><span class="sxs-lookup"><span data-stu-id="830c4-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="830c4-165">Le type de la variable d’itération dans la `For Each` boucle est le type anonyme créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="830c4-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="830c4-166">Étant donné que le type n’a pas de nom utilisable, le type de la variable d’itération de la boucle doit être déterminé implicitement.</span><span class="sxs-lookup"><span data-stu-id="830c4-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="830c4-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="830c4-167">See also</span></span>

- [<span data-ttu-id="830c4-168">Mise en route de LINQ dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="830c4-168">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="830c4-169">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="830c4-169">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="830c4-170">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="830c4-170">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="830c4-171">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="830c4-171">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="830c4-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="830c4-172">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="830c4-173">Requêtes</span><span class="sxs-lookup"><span data-stu-id="830c4-173">Queries</span></span>](../../../language-reference/queries/index.md)
