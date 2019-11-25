---
title: 'How to: Combine Data with LINQ by Using Joins'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345001"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="54f13-102">Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54f13-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="54f13-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span><span class="sxs-lookup"><span data-stu-id="54f13-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="54f13-104">These values are known as *key* values.</span><span class="sxs-lookup"><span data-stu-id="54f13-104">These values are known as *key* values.</span></span> <span data-ttu-id="54f13-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="54f13-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="54f13-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span><span class="sxs-lookup"><span data-stu-id="54f13-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="54f13-107">Create a Project and Add Sample Data</span><span class="sxs-lookup"><span data-stu-id="54f13-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="54f13-108">To create a project that contains sample data and types</span><span class="sxs-lookup"><span data-stu-id="54f13-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="54f13-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span><span class="sxs-lookup"><span data-stu-id="54f13-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="54f13-110">Double-click the Module1.vb file created by Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="54f13-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="54f13-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span><span class="sxs-lookup"><span data-stu-id="54f13-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="54f13-112">Copy this code into the default `Module1` module created by Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="54f13-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="54f13-113">Perform an Inner Join by Using the Join Clause</span><span class="sxs-lookup"><span data-stu-id="54f13-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="54f13-114">An INNER JOIN combines data from two collections.</span><span class="sxs-lookup"><span data-stu-id="54f13-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="54f13-115">Items for which the specified key values match are included.</span><span class="sxs-lookup"><span data-stu-id="54f13-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="54f13-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span><span class="sxs-lookup"><span data-stu-id="54f13-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="54f13-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span><span class="sxs-lookup"><span data-stu-id="54f13-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="54f13-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="54f13-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="54f13-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span><span class="sxs-lookup"><span data-stu-id="54f13-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="54f13-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span><span class="sxs-lookup"><span data-stu-id="54f13-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="54f13-121">In this case, a `Where` clause can still be used to filter the query results.</span><span class="sxs-lookup"><span data-stu-id="54f13-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="54f13-122">To perform an Inner Join by using the Join clause</span><span class="sxs-lookup"><span data-stu-id="54f13-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="54f13-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span><span class="sxs-lookup"><span data-stu-id="54f13-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="54f13-124">Perform a Left Outer Join by Using the Group Join Clause</span><span class="sxs-lookup"><span data-stu-id="54f13-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="54f13-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span><span class="sxs-lookup"><span data-stu-id="54f13-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="54f13-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span><span class="sxs-lookup"><span data-stu-id="54f13-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="54f13-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="54f13-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="54f13-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span><span class="sxs-lookup"><span data-stu-id="54f13-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="54f13-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span><span class="sxs-lookup"><span data-stu-id="54f13-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="54f13-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span><span class="sxs-lookup"><span data-stu-id="54f13-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="54f13-131">You will see what this looks like when you complete the next procedure.</span><span class="sxs-lookup"><span data-stu-id="54f13-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="54f13-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span><span class="sxs-lookup"><span data-stu-id="54f13-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="54f13-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span><span class="sxs-lookup"><span data-stu-id="54f13-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="54f13-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span><span class="sxs-lookup"><span data-stu-id="54f13-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="54f13-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span><span class="sxs-lookup"><span data-stu-id="54f13-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="54f13-136">To perform a Left Outer Join by using the Group Join clause</span><span class="sxs-lookup"><span data-stu-id="54f13-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="54f13-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span><span class="sxs-lookup"><span data-stu-id="54f13-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="54f13-138">Perform a Join by Using a Composite Key</span><span class="sxs-lookup"><span data-stu-id="54f13-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="54f13-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span><span class="sxs-lookup"><span data-stu-id="54f13-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="54f13-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span><span class="sxs-lookup"><span data-stu-id="54f13-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="54f13-141">To perform a Join by using a composite key</span><span class="sxs-lookup"><span data-stu-id="54f13-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="54f13-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span><span class="sxs-lookup"><span data-stu-id="54f13-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="54f13-143">Run the Code</span><span class="sxs-lookup"><span data-stu-id="54f13-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="54f13-144">To add code to run the examples</span><span class="sxs-lookup"><span data-stu-id="54f13-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="54f13-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span><span class="sxs-lookup"><span data-stu-id="54f13-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="54f13-146">Press F5 to run the examples.</span><span class="sxs-lookup"><span data-stu-id="54f13-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f13-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54f13-147">See also</span></span>

- [<span data-ttu-id="54f13-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="54f13-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="54f13-149">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54f13-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="54f13-150">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="54f13-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="54f13-151">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="54f13-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="54f13-152">From (clause)</span><span class="sxs-lookup"><span data-stu-id="54f13-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="54f13-153">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="54f13-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="54f13-154">Requêtes</span><span class="sxs-lookup"><span data-stu-id="54f13-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="54f13-155">Transformations de données avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="54f13-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
