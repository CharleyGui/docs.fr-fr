---
title: Opérations de requête de base
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266376"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="afd81-102">Opérations de requête de base (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afd81-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="afd81-103">Ce sujet fournit une brève introduction aux expressions de la requête intégrée en langue (LINQ) dans Visual Basic, et à certains des types typiques d’opérations que vous effectuez dans une requête.</span><span class="sxs-lookup"><span data-stu-id="afd81-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="afd81-104">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="afd81-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="afd81-105">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afd81-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="afd81-106">Requêtes</span><span class="sxs-lookup"><span data-stu-id="afd81-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="afd81-107">Procédure pas à pas : écriture de requêtes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afd81-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="afd81-108">Spécifier la source de données (à partir de)</span><span class="sxs-lookup"><span data-stu-id="afd81-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="afd81-109">Dans une requête LINQ, la première étape consiste à spécifier la source de données que vous souhaitez interroger.</span><span class="sxs-lookup"><span data-stu-id="afd81-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="afd81-110">Par conséquent, la `From` clause dans une requête vient toujours en premier.</span><span class="sxs-lookup"><span data-stu-id="afd81-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="afd81-111">Les opérateurs de requête sélectionnent et façonnent le résultat en fonction du type de source.</span><span class="sxs-lookup"><span data-stu-id="afd81-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="afd81-112">La `From` clause spécifie `customers`la source de `cust`données, et une variable de *portée*, .</span><span class="sxs-lookup"><span data-stu-id="afd81-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="afd81-113">La variable de plage est comme une variable d’itération en boucle, sauf que dans une expression de requête, aucune itération réelle ne se produit.</span><span class="sxs-lookup"><span data-stu-id="afd81-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="afd81-114">Lorsque la requête est exécutée, `For Each` souvent en utilisant une boucle, la variable `customers`de plage sert de référence à chaque élément successif dans .</span><span class="sxs-lookup"><span data-stu-id="afd81-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="afd81-115">Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="afd81-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="afd81-116">Pour des exemples de requêtes écrites avec et sans dactylographie explicite, voir [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="afd81-117">Pour plus d’informations `From` sur la façon d’utiliser la clause dans Visual Basic, voir [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="afd81-118">Données filtantes (Où)</span><span class="sxs-lookup"><span data-stu-id="afd81-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="afd81-119">Probablement l’opération de requête la plus courante est l’application d’un filtre sous la forme d’une expression Boolean.</span><span class="sxs-lookup"><span data-stu-id="afd81-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="afd81-120">La requête ne renvoie alors que les éléments pour lesquels l’expression est vraie.</span><span class="sxs-lookup"><span data-stu-id="afd81-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="afd81-121">Une `Where` clause est utilisée pour effectuer le filtrage.</span><span class="sxs-lookup"><span data-stu-id="afd81-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="afd81-122">Le filtre précise quels éléments de la source de données à inclure dans la séquence résultante.</span><span class="sxs-lookup"><span data-stu-id="afd81-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="afd81-123">Dans l’exemple suivant, seuls les clients qui ont une adresse à Londres sont inclus.</span><span class="sxs-lookup"><span data-stu-id="afd81-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="afd81-124">Vous pouvez utiliser des `And` `Or` opérateurs logiques tels `Where` que et combiner des expressions de filtre dans une clause.</span><span class="sxs-lookup"><span data-stu-id="afd81-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="afd81-125">Par exemple, pour ne retourner que les clients qui sont de Londres et dont le nom est Devon, utilisez le code suivant:</span><span class="sxs-lookup"><span data-stu-id="afd81-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="afd81-126">Pour renvoyer les clients de Londres ou de Paris, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afd81-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="afd81-127">Pour plus d’informations `Where` sur la façon d’utiliser la clause dans Visual Basic, voir [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="afd81-128">Données de commande (Ordre par)</span><span class="sxs-lookup"><span data-stu-id="afd81-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="afd81-129">Il est souvent pratique de trier les données retournées dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="afd81-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="afd81-130">La `Order By` clause fera en sorte que les éléments de la séquence retournée seront triés sur un champ ou un champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="afd81-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="afd81-131">Par exemple, la requête suivante trie `Name` les résultats en fonction de la propriété.</span><span class="sxs-lookup"><span data-stu-id="afd81-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="afd81-132">Parce `Name` que c’est une chaîne, les données retournées seront triées par ordre alphabétique, de A à Z.</span><span class="sxs-lookup"><span data-stu-id="afd81-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="afd81-133">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="afd81-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="afd81-134">La valeur `Ascending` par `Ascending` `Descending` défaut est lorsque ni ni est spécifié.</span><span class="sxs-lookup"><span data-stu-id="afd81-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="afd81-135">Pour plus d’informations `Order By` sur la façon d’utiliser la clause dans Visual Basic, voir [Ordre par clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="afd81-136">Sélection des données (Sélectionner)</span><span class="sxs-lookup"><span data-stu-id="afd81-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="afd81-137">La `Select` clause spécifie le formulaire et le contenu des éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="afd81-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="afd81-138">Par exemple, vous pouvez spécifier `Customer` si vos `Customer` résultats seront composés d’objets complets, d’une seule propriété, d’un sous-ensemble de propriétés, d’une combinaison de propriétés provenant de diverses sources de données ou d’un nouveau type de résultat basé sur un calcul.</span><span class="sxs-lookup"><span data-stu-id="afd81-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="afd81-139">Quand la clause `Select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.</span><span class="sxs-lookup"><span data-stu-id="afd81-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="afd81-140">Pour récupérer une collection `Customer` composée d’objets complets, sélectionnez la variable de plage elle-même :</span><span class="sxs-lookup"><span data-stu-id="afd81-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="afd81-141">Si `Customer` une instance est un grand objet qui a de nombreux champs, et `cust.Name`tout ce que vous voulez récupérer est le nom, vous pouvez sélectionner , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="afd81-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="afd81-142">L’inférence de type local reconnaît que `Customer` cela modifie le type de résultat d’une collection d’objets à une collection de cordes.</span><span class="sxs-lookup"><span data-stu-id="afd81-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="afd81-143">Pour sélectionner plusieurs champs à partir de la source de données, vous avez deux choix :</span><span class="sxs-lookup"><span data-stu-id="afd81-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="afd81-144">Dans `Select` la clause, spécifiez les champs que vous souhaitez inclure dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="afd81-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="afd81-145">Le compilateur définira un type anonyme qui a ces champs comme ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="afd81-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="afd81-146">Pour plus d’informations, voir [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="afd81-147">Étant donné que les éléments retournés dans l’exemple suivant sont des cas de type anonyme, vous ne pouvez pas vous référer au type par nom ailleurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="afd81-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="afd81-148">Le nom désigné compilateur pour le type contient des caractères qui ne sont pas valides dans le code de base visuel normal.</span><span class="sxs-lookup"><span data-stu-id="afd81-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="afd81-149">Dans l’exemple suivant, les éléments de la collection `londonCusts4` qui sont retournés par la requête sont des cas de type anonyme</span><span class="sxs-lookup"><span data-stu-id="afd81-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="afd81-150">-ou-</span><span class="sxs-lookup"><span data-stu-id="afd81-150">-or-</span></span>  
  
- <span data-ttu-id="afd81-151">Définissez un type nommé qui contient les champs particuliers que vous souhaitez inclure dans `Select` le résultat, et créez et initialisez des instances du type de la clause.</span><span class="sxs-lookup"><span data-stu-id="afd81-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="afd81-152">Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans laquelle ils sont retournés, ou si vous devez les passer comme paramètres dans les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="afd81-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="afd81-153">Le type `londonCusts5` de dans l’exemple suivant est IEnumerable (De NamePhone).</span><span class="sxs-lookup"><span data-stu-id="afd81-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="afd81-154">Pour plus d’informations `Select` sur la façon d’utiliser la clause dans Visual Basic, voir [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="afd81-155">Rejoindre data (Join and Group Join)</span><span class="sxs-lookup"><span data-stu-id="afd81-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="afd81-156">Vous pouvez combiner plus d’une source de données dans la `From` clause de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="afd81-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="afd81-157">Par exemple, le code suivant utilise deux sources de données et combine implicitement les propriétés des deux dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="afd81-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="afd81-158">La requête sélectionne les étudiants dont les noms de famille commencent par une voyelle.</span><span class="sxs-lookup"><span data-stu-id="afd81-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="afd81-159">Vous pouvez exécuter ce code avec la liste des étudiants créés dans [Comment : Créer une liste d’objets](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="afd81-160">Le `Join` mot clé `INNER JOIN` est équivalent à un SQL.</span><span class="sxs-lookup"><span data-stu-id="afd81-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="afd81-161">Il combine deux collections basées sur des valeurs clés assorties entre les éléments des deux collections.</span><span class="sxs-lookup"><span data-stu-id="afd81-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="afd81-162">La requête renvoie tout ou partie des éléments de collecte qui ont des valeurs clés correspondantes.</span><span class="sxs-lookup"><span data-stu-id="afd81-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="afd81-163">Par exemple, le code suivant reproduit l’action de la jointure implicite précédente.</span><span class="sxs-lookup"><span data-stu-id="afd81-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="afd81-164">`Group Join`combine des collections en une seule collection `LEFT JOIN` hiérarchique, tout comme un dans SQL.</span><span class="sxs-lookup"><span data-stu-id="afd81-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="afd81-165">Pour plus d’informations, voir [Clause De jointure](../../../../visual-basic/language-reference/queries/join-clause.md) et [clause de jointure de groupe](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="afd81-166">Groupement des données (Groupe par)</span><span class="sxs-lookup"><span data-stu-id="afd81-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="afd81-167">Vous pouvez `Group By` ajouter une clause pour regrouper les éléments dans un résultat de requête selon un ou plusieurs champs des éléments.</span><span class="sxs-lookup"><span data-stu-id="afd81-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="afd81-168">Par exemple, le code suivant regroupe les élèves par année de classe.</span><span class="sxs-lookup"><span data-stu-id="afd81-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="afd81-169">Si vous exécutez ce code en utilisant la liste des étudiants créés dans [Comment : Créer une liste d’éléments,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)la sortie de l’instruction `For Each` est :</span><span class="sxs-lookup"><span data-stu-id="afd81-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="afd81-170">Année: Junior</span><span class="sxs-lookup"><span data-stu-id="afd81-170">Year: Junior</span></span>  
  
 <span data-ttu-id="afd81-171">Michael Tucker</span><span class="sxs-lookup"><span data-stu-id="afd81-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="afd81-172">Hugo Garcia</span><span class="sxs-lookup"><span data-stu-id="afd81-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="afd81-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="afd81-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="afd81-174">Lance Tucker</span><span class="sxs-lookup"><span data-stu-id="afd81-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="afd81-175">Année: Senior</span><span class="sxs-lookup"><span data-stu-id="afd81-175">Year: Senior</span></span>  
  
 <span data-ttu-id="afd81-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="afd81-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="afd81-177">Michiko Osada</span><span class="sxs-lookup"><span data-stu-id="afd81-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="afd81-178">Fadi Fakhouri</span><span class="sxs-lookup"><span data-stu-id="afd81-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="afd81-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="afd81-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="afd81-180">Terry Adams</span><span class="sxs-lookup"><span data-stu-id="afd81-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="afd81-181">Année: Freshman</span><span class="sxs-lookup"><span data-stu-id="afd81-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="afd81-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="afd81-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="afd81-183">César Garcia</span><span class="sxs-lookup"><span data-stu-id="afd81-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="afd81-184">La variation indiquée dans le code suivant commande les années de classe, puis commande les étudiants dans chaque année par nom de famille.</span><span class="sxs-lookup"><span data-stu-id="afd81-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="afd81-185">Pour plus `Group By`d’informations sur , voir [Groupe par clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afd81-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd81-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afd81-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="afd81-187">Mise en route de LINQ dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afd81-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="afd81-188">Requêtes</span><span class="sxs-lookup"><span data-stu-id="afd81-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="afd81-189">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afd81-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="afd81-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="afd81-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
