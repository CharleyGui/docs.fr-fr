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
ms.openlocfilehash: e9a646d60bb22507f4c6bcbcdf9222fd0ed18f02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345751"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="4f26a-102">Opérations de requête de base (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f26a-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="4f26a-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span><span class="sxs-lookup"><span data-stu-id="4f26a-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="4f26a-104">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f26a-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="4f26a-105">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f26a-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="4f26a-106">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4f26a-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="4f26a-107">Walkthrough: Writing Queries in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f26a-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="4f26a-108">Specifying the Data Source (From)</span><span class="sxs-lookup"><span data-stu-id="4f26a-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="4f26a-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span><span class="sxs-lookup"><span data-stu-id="4f26a-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="4f26a-110">Therefore, the `From` clause in a query always comes first.</span><span class="sxs-lookup"><span data-stu-id="4f26a-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="4f26a-111">Query operators select and shape the result based on the type of the source.</span><span class="sxs-lookup"><span data-stu-id="4f26a-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="4f26a-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="4f26a-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="4f26a-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span><span class="sxs-lookup"><span data-stu-id="4f26a-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="4f26a-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span><span class="sxs-lookup"><span data-stu-id="4f26a-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="4f26a-115">Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="4f26a-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="4f26a-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="4f26a-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="4f26a-118">Filtering Data (Where)</span><span class="sxs-lookup"><span data-stu-id="4f26a-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="4f26a-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span><span class="sxs-lookup"><span data-stu-id="4f26a-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="4f26a-120">The query then returns only those elements for which the expression is true.</span><span class="sxs-lookup"><span data-stu-id="4f26a-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="4f26a-121">A `Where` clause is used to perform the filtering.</span><span class="sxs-lookup"><span data-stu-id="4f26a-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="4f26a-122">The filter specifies which elements in the data source to include in the resulting sequence.</span><span class="sxs-lookup"><span data-stu-id="4f26a-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="4f26a-123">In the following example, only those customers who have an address in London are included.</span><span class="sxs-lookup"><span data-stu-id="4f26a-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="4f26a-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="4f26a-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="4f26a-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span><span class="sxs-lookup"><span data-stu-id="4f26a-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="4f26a-126">To return customers from London or Paris, use the following code:</span><span class="sxs-lookup"><span data-stu-id="4f26a-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="4f26a-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="4f26a-128">Ordering Data (Order By)</span><span class="sxs-lookup"><span data-stu-id="4f26a-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="4f26a-129">It often is convenient to sort returned data into a particular order.</span><span class="sxs-lookup"><span data-stu-id="4f26a-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="4f26a-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span><span class="sxs-lookup"><span data-stu-id="4f26a-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="4f26a-131">For example, the following query sorts the results based on the `Name` property.</span><span class="sxs-lookup"><span data-stu-id="4f26a-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="4f26a-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span><span class="sxs-lookup"><span data-stu-id="4f26a-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4f26a-133">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="4f26a-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="4f26a-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span><span class="sxs-lookup"><span data-stu-id="4f26a-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="4f26a-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="4f26a-136">Selecting Data (Select)</span><span class="sxs-lookup"><span data-stu-id="4f26a-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="4f26a-137">The `Select` clause specifies the form and content of returned elements.</span><span class="sxs-lookup"><span data-stu-id="4f26a-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="4f26a-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span><span class="sxs-lookup"><span data-stu-id="4f26a-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="4f26a-139">Quand la clause `Select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.</span><span class="sxs-lookup"><span data-stu-id="4f26a-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="4f26a-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span><span class="sxs-lookup"><span data-stu-id="4f26a-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="4f26a-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="4f26a-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="4f26a-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span><span class="sxs-lookup"><span data-stu-id="4f26a-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="4f26a-143">To select multiple fields from the data source, you have two choices:</span><span class="sxs-lookup"><span data-stu-id="4f26a-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="4f26a-144">In the `Select` clause, specify the fields you want to include in the result.</span><span class="sxs-lookup"><span data-stu-id="4f26a-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="4f26a-145">The compiler will define an anonymous type that has those fields as its properties.</span><span class="sxs-lookup"><span data-stu-id="4f26a-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="4f26a-146">Pour plus d’informations, consultez la page [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="4f26a-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span><span class="sxs-lookup"><span data-stu-id="4f26a-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="4f26a-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="4f26a-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="4f26a-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span><span class="sxs-lookup"><span data-stu-id="4f26a-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="4f26a-150">ou</span><span class="sxs-lookup"><span data-stu-id="4f26a-150">-or-</span></span>  
  
- <span data-ttu-id="4f26a-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="4f26a-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="4f26a-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span><span class="sxs-lookup"><span data-stu-id="4f26a-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="4f26a-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="4f26a-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="4f26a-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="4f26a-155">Joining Data (Join and Group Join)</span><span class="sxs-lookup"><span data-stu-id="4f26a-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="4f26a-156">You can combine more than one data source in the `From` clause in several ways.</span><span class="sxs-lookup"><span data-stu-id="4f26a-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="4f26a-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span><span class="sxs-lookup"><span data-stu-id="4f26a-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="4f26a-158">The query selects students whose last names start with a vowel.</span><span class="sxs-lookup"><span data-stu-id="4f26a-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="4f26a-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="4f26a-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span><span class="sxs-lookup"><span data-stu-id="4f26a-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="4f26a-161">It combines two collections based on matching key values between elements in the two collections.</span><span class="sxs-lookup"><span data-stu-id="4f26a-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="4f26a-162">The query returns all or part of the collection elements that have matching key values.</span><span class="sxs-lookup"><span data-stu-id="4f26a-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="4f26a-163">For example, the following code duplicates the action of the previous implicit join.</span><span class="sxs-lookup"><span data-stu-id="4f26a-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="4f26a-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span><span class="sxs-lookup"><span data-stu-id="4f26a-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="4f26a-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="4f26a-166">Grouping Data (Group By)</span><span class="sxs-lookup"><span data-stu-id="4f26a-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="4f26a-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span><span class="sxs-lookup"><span data-stu-id="4f26a-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="4f26a-168">For example, the following code groups students by class year.</span><span class="sxs-lookup"><span data-stu-id="4f26a-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="4f26a-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span><span class="sxs-lookup"><span data-stu-id="4f26a-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="4f26a-170">Year: Junior</span><span class="sxs-lookup"><span data-stu-id="4f26a-170">Year: Junior</span></span>  
  
 <span data-ttu-id="4f26a-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="4f26a-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="4f26a-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="4f26a-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="4f26a-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="4f26a-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="4f26a-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="4f26a-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="4f26a-175">Year: Senior</span><span class="sxs-lookup"><span data-stu-id="4f26a-175">Year: Senior</span></span>  
  
 <span data-ttu-id="4f26a-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="4f26a-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="4f26a-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="4f26a-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="4f26a-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="4f26a-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="4f26a-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="4f26a-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="4f26a-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="4f26a-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="4f26a-181">Year: Freshman</span><span class="sxs-lookup"><span data-stu-id="4f26a-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="4f26a-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="4f26a-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="4f26a-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="4f26a-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="4f26a-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span><span class="sxs-lookup"><span data-stu-id="4f26a-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="4f26a-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4f26a-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f26a-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f26a-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4f26a-187">Bien démarrer avec LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f26a-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="4f26a-188">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4f26a-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4f26a-189">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f26a-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4f26a-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="4f26a-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
