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
ms.openlocfilehash: b9216dba23f49e4d9fd99687e38f5c13addde8fb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636872"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="c19a2-102">Opérations de requête de base (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19a2-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="c19a2-103">Cette rubrique fournit une brève introduction aux expressions LINQ (Language-Integrated Query) dans Visual Basic, ainsi qu’à certains types d’opérations classiques que vous effectuez dans une requête.</span><span class="sxs-lookup"><span data-stu-id="c19a2-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="c19a2-104">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c19a2-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="c19a2-105">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19a2-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="c19a2-106">Requêtes</span><span class="sxs-lookup"><span data-stu-id="c19a2-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="c19a2-107">Procédure pas à pas : écriture de requêtes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19a2-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="c19a2-108">Spécification de la source de données (à partir de)</span><span class="sxs-lookup"><span data-stu-id="c19a2-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="c19a2-109">Dans une requête LINQ, la première étape consiste à spécifier la source de données que vous souhaitez interroger.</span><span class="sxs-lookup"><span data-stu-id="c19a2-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="c19a2-110">Par conséquent, la clause `From` dans une requête est toujours la première.</span><span class="sxs-lookup"><span data-stu-id="c19a2-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="c19a2-111">Les opérateurs de requête sélectionnent et déforment le résultat en fonction du type de la source.</span><span class="sxs-lookup"><span data-stu-id="c19a2-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c19a2-112">La clause `From` spécifie la source de données, `customers`et une *variable de portée*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="c19a2-113">La variable de portée est semblable à une variable d’itération de boucle, sauf que dans une expression de requête, aucune itération réelle n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="c19a2-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="c19a2-114">Lorsque la requête est exécutée, souvent à l’aide d’une `For Each` boucle, la variable de portée sert de référence à chaque élément successif dans `customers`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="c19a2-115">Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="c19a2-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="c19a2-116">Pour obtenir des exemples de requêtes écrites avec et sans typage explicite, consultez [relations de types dans les opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="c19a2-117">Pour plus d’informations sur l’utilisation de la clause `From` dans Visual Basic, consultez [from, clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="c19a2-118">Filtrage des données (où)</span><span class="sxs-lookup"><span data-stu-id="c19a2-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="c19a2-119">L’opération de requête la plus courante est probablement l’application d’un filtre sous la forme d’une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="c19a2-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="c19a2-120">La requête retourne alors uniquement les éléments pour lesquels l’expression a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="c19a2-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="c19a2-121">Une clause `Where` est utilisée pour effectuer le filtrage.</span><span class="sxs-lookup"><span data-stu-id="c19a2-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="c19a2-122">Le filtre spécifie les éléments de la source de données à inclure dans la séquence résultante.</span><span class="sxs-lookup"><span data-stu-id="c19a2-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="c19a2-123">Dans l’exemple suivant, seuls les clients qui ont une adresse à Londres sont inclus.</span><span class="sxs-lookup"><span data-stu-id="c19a2-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c19a2-124">Vous pouvez utiliser des opérateurs logiques tels que `And` et `Or` pour combiner des expressions de filtre dans une clause `Where`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="c19a2-125">Par exemple, pour retourner uniquement les clients de Londres et dont le nom est Devon, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c19a2-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="c19a2-126">Pour retourner les clients de Londres ou Paris, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c19a2-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="c19a2-127">Pour plus d’informations sur l’utilisation de la clause `Where` dans Visual Basic, consultez [clause WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="c19a2-128">Tri des données (Order By)</span><span class="sxs-lookup"><span data-stu-id="c19a2-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="c19a2-129">Il est souvent pratique de trier les données retournées dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="c19a2-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="c19a2-130">La clause `Order By` entraîne le tri des éléments de la séquence retournée sur un champ ou des champs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c19a2-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="c19a2-131">Par exemple, la requête suivante trie les résultats en fonction de la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="c19a2-132">Étant donné que `Name` est une chaîne, les données retournées sont triées par ordre alphabétique, de A à Z.</span><span class="sxs-lookup"><span data-stu-id="c19a2-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c19a2-133">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="c19a2-134">La valeur par défaut est `Ascending` lorsque ni `Ascending` ni `Descending` n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="c19a2-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="c19a2-135">Pour plus d’informations sur l’utilisation de la clause `Order By` dans Visual Basic, consultez [clause ORDER BY](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="c19a2-136">Sélection des données (Select)</span><span class="sxs-lookup"><span data-stu-id="c19a2-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="c19a2-137">La clause `Select` spécifie la forme et le contenu des éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="c19a2-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="c19a2-138">Par exemple, vous pouvez spécifier si vos résultats seront composés d’objets `Customer` complets, d’une seule `Customer` propriété, d’un sous-ensemble de propriétés, d’une combinaison de propriétés provenant de diverses sources de données ou d’un nouveau type de résultat basé sur un calcul.</span><span class="sxs-lookup"><span data-stu-id="c19a2-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="c19a2-139">Quand la clause `Select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.</span><span class="sxs-lookup"><span data-stu-id="c19a2-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="c19a2-140">Pour récupérer une collection qui se compose d’objets `Customer` complets, sélectionnez la variable de portée proprement dite :</span><span class="sxs-lookup"><span data-stu-id="c19a2-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c19a2-141">Si une instance de `Customer` est un objet volumineux qui contient de nombreux champs, et que vous souhaitez récupérer le nom, vous pouvez sélectionner `cust.Name`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c19a2-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="c19a2-142">L’inférence de type local reconnaît que ce modifie le type de résultat d’une collection d’objets `Customer` en une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c19a2-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c19a2-143">Pour sélectionner plusieurs champs de la source de données, vous avez deux possibilités :</span><span class="sxs-lookup"><span data-stu-id="c19a2-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="c19a2-144">Dans la clause `Select`, spécifiez les champs que vous souhaitez inclure dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="c19a2-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="c19a2-145">Le compilateur définit un type anonyme dont les propriétés sont les champs.</span><span class="sxs-lookup"><span data-stu-id="c19a2-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="c19a2-146">Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="c19a2-147">Étant donné que les éléments retournés dans l’exemple suivant sont des instances d’un type anonyme, vous ne pouvez pas faire référence au type par un autre nom dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c19a2-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="c19a2-148">Le nom désigné par le compilateur pour le type contient des caractères qui ne sont pas valides dans le code Visual Basic normal.</span><span class="sxs-lookup"><span data-stu-id="c19a2-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="c19a2-149">Dans l’exemple suivant, les éléments de la collection qui est retournée par la requête dans `londonCusts4` sont des instances d’un type anonyme</span><span class="sxs-lookup"><span data-stu-id="c19a2-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="c19a2-150">\- ou -</span><span class="sxs-lookup"><span data-stu-id="c19a2-150">-or-</span></span>  
  
- <span data-ttu-id="c19a2-151">Définissez un type nommé qui contient les champs particuliers que vous souhaitez inclure dans le résultat, et créez et initialisez des instances du type dans la clause `Select`.</span><span class="sxs-lookup"><span data-stu-id="c19a2-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="c19a2-152">Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans laquelle ils sont retournés, ou si vous devez les passer en tant que paramètres dans les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="c19a2-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="c19a2-153">Le type de `londonCusts5` dans l’exemple suivant est IEnumerable (of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="c19a2-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c19a2-154">Pour plus d’informations sur l’utilisation de la clause `Select` dans Visual Basic, consultez [Select, clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="c19a2-155">Jointure de données (jointure et jointure groupée)</span><span class="sxs-lookup"><span data-stu-id="c19a2-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="c19a2-156">Vous pouvez combiner plusieurs sources de données dans la clause `From` de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="c19a2-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="c19a2-157">Par exemple, le code suivant utilise deux sources de données et combine implicitement les propriétés des deux dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="c19a2-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="c19a2-158">La requête sélectionne les élèves dont les noms commencent par une voyelle.</span><span class="sxs-lookup"><span data-stu-id="c19a2-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="c19a2-159">Vous pouvez exécuter ce code avec la liste des élèves créée dans [How to : Create a list of items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="c19a2-160">Le mot clé `Join` est équivalent à un `INNER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="c19a2-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="c19a2-161">Il combine deux collections en fonction des valeurs de clé correspondantes entre les éléments des deux collections.</span><span class="sxs-lookup"><span data-stu-id="c19a2-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="c19a2-162">La requête retourne tout ou partie des éléments de la collection qui ont des valeurs de clé correspondantes.</span><span class="sxs-lookup"><span data-stu-id="c19a2-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="c19a2-163">Par exemple, le code suivant duplique l’action de la jointure implicite précédente.</span><span class="sxs-lookup"><span data-stu-id="c19a2-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="c19a2-164">`Group Join` combine des collections dans une collection hiérarchique unique, tout comme une `LEFT JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="c19a2-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="c19a2-165">Pour plus d’informations, consultez [clause join](../../../../visual-basic/language-reference/queries/join-clause.md) et [clause Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="c19a2-166">Regroupement de données (Group by)</span><span class="sxs-lookup"><span data-stu-id="c19a2-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="c19a2-167">Vous pouvez ajouter une clause `Group By` pour regrouper les éléments d’un résultat de requête en fonction d’un ou de plusieurs champs des éléments.</span><span class="sxs-lookup"><span data-stu-id="c19a2-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="c19a2-168">Par exemple, le code suivant regroupe les étudiants par année de classe.</span><span class="sxs-lookup"><span data-stu-id="c19a2-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c19a2-169">Si vous exécutez ce code à l’aide de la liste des élèves créée dans [How to : Create a list of items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), la sortie de l’instruction `For Each` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c19a2-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="c19a2-170">Année : Junior</span><span class="sxs-lookup"><span data-stu-id="c19a2-170">Year: Junior</span></span>  
  
 <span data-ttu-id="c19a2-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="c19a2-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="c19a2-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="c19a2-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="c19a2-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="c19a2-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="c19a2-174">Tucker, lance</span><span class="sxs-lookup"><span data-stu-id="c19a2-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="c19a2-175">Année : Senior</span><span class="sxs-lookup"><span data-stu-id="c19a2-175">Year: Senior</span></span>  
  
 <span data-ttu-id="c19a2-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="c19a2-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="c19a2-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="c19a2-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="c19a2-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="c19a2-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="c19a2-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="c19a2-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="c19a2-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="c19a2-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="c19a2-181">Année : actualité</span><span class="sxs-lookup"><span data-stu-id="c19a2-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="c19a2-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="c19a2-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="c19a2-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="c19a2-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="c19a2-184">La variation indiquée dans le code suivant trie les années de la classe, puis classe les étudiants au cours de chaque année par nom.</span><span class="sxs-lookup"><span data-stu-id="c19a2-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="c19a2-185">Pour plus d’informations sur `Group By`, consultez [clause Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c19a2-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19a2-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c19a2-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="c19a2-187">Bien démarrer avec LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19a2-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="c19a2-188">Requêtes</span><span class="sxs-lookup"><span data-stu-id="c19a2-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c19a2-189">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19a2-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c19a2-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="c19a2-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
