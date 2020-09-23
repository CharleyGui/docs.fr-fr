---
title: 'Guide pratique : combiner des données avec LINQ à l’aide de jointures'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: ebda8d3b7fa2e712c337ed2c1fadc580bed7fe61
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075068"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="07983-102">Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07983-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>

<span data-ttu-id="07983-103">Visual Basic fournit les `Join` `Group Join` clauses de requête et pour vous permettre de combiner le contenu de plusieurs collections en fonction de valeurs communes entre les collections.</span><span class="sxs-lookup"><span data-stu-id="07983-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="07983-104">Ces valeurs sont appelées valeurs de *clés* .</span><span class="sxs-lookup"><span data-stu-id="07983-104">These values are known as *key* values.</span></span> <span data-ttu-id="07983-105">Les développeurs familiarisés avec les concepts de base de données relationnelle reconnaissent la `Join` clause comme une jointure interne et la `Group Join` clause comme, en fait, une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="07983-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="07983-106">Les exemples de cette rubrique illustrent les différentes façons de combiner des données à l’aide des `Join` `Group Join` clauses de requête et.</span><span class="sxs-lookup"><span data-stu-id="07983-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="07983-107">Créer un projet et ajouter des exemples de données</span><span class="sxs-lookup"><span data-stu-id="07983-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="07983-108">Pour créer un projet qui contient des exemples de données et des types</span><span class="sxs-lookup"><span data-stu-id="07983-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="07983-109">Pour exécuter les exemples de cette rubrique, ouvrez Visual Studio et ajoutez un nouveau Visual Basic projet d’application console.</span><span class="sxs-lookup"><span data-stu-id="07983-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="07983-110">Double-cliquez sur le fichier Module1. vb créé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="07983-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="07983-111">Les exemples de cette rubrique utilisent les `Person` `Pet` types et et les données de l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="07983-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="07983-112">Copiez ce code dans le `Module1` module par défaut créé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="07983-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="07983-113">Effectuer une jointure interne à l’aide de la clause join</span><span class="sxs-lookup"><span data-stu-id="07983-113">Perform an Inner Join by Using the Join Clause</span></span>  

 <span data-ttu-id="07983-114">Une jointure interne combine les données de deux collections.</span><span class="sxs-lookup"><span data-stu-id="07983-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="07983-115">Les éléments pour lesquels les valeurs de clé spécifiées correspondent sont inclus.</span><span class="sxs-lookup"><span data-stu-id="07983-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="07983-116">Tous les éléments de l’une des collections qui n’ont pas d’élément correspondant dans l’autre collection sont exclus.</span><span class="sxs-lookup"><span data-stu-id="07983-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="07983-117">Dans Visual Basic, LINQ fournit deux options pour effectuer une jointure interne : une jointure implicite et une jointure explicite.</span><span class="sxs-lookup"><span data-stu-id="07983-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="07983-118">Une jointure implicite spécifie les collections à joindre dans une `From` clause et identifie les champs de clé correspondants dans une `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="07983-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="07983-119">Visual Basic joint implicitement les deux collections en fonction des champs de clé spécifiés.</span><span class="sxs-lookup"><span data-stu-id="07983-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="07983-120">Vous pouvez spécifier une jointure explicite à l’aide de la `Join` clause lorsque vous souhaitez être précis sur les champs clés à utiliser dans la jointure.</span><span class="sxs-lookup"><span data-stu-id="07983-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="07983-121">Dans ce cas, une `Where` clause peut encore être utilisée pour filtrer les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="07983-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="07983-122">Pour effectuer une jointure interne à l’aide de la clause join</span><span class="sxs-lookup"><span data-stu-id="07983-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="07983-123">Ajoutez le code suivant au `Module1` module dans votre projet pour voir des exemples de jointure interne implicite et explicite.</span><span class="sxs-lookup"><span data-stu-id="07983-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="07983-124">Effectuer une jointure externe gauche à l’aide de la clause Group Join</span><span class="sxs-lookup"><span data-stu-id="07983-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  

 <span data-ttu-id="07983-125">Une jointure externe gauche comprend tous les éléments de la collection du côté gauche de la jointure et uniquement les valeurs correspondantes de la collection de droite de la jointure.</span><span class="sxs-lookup"><span data-stu-id="07983-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="07983-126">Tous les éléments de la collection située à droite de la jointure qui n’ont pas d’élément correspondant dans la collection de gauche sont exclus du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="07983-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="07983-127">La `Group Join` clause effectue, en effet, une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="07983-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="07983-128">La différence entre ce qui est généralement appelé jointure externe gauche et ce que la `Group Join` clause retourne est que la `Group Join` clause regroupe les résultats de la collection de droite de la jointure pour chaque élément de la collection de gauche.</span><span class="sxs-lookup"><span data-stu-id="07983-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="07983-129">Dans une base de données relationnelle, une jointure externe gauche retourne un résultat non groupé dans lequel chaque élément du résultat de la requête contient des éléments correspondants des deux collections de la jointure.</span><span class="sxs-lookup"><span data-stu-id="07983-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="07983-130">Dans ce cas, les éléments de la collection du côté gauche de la jointure sont répétés pour chaque élément correspondant de la collection de droite.</span><span class="sxs-lookup"><span data-stu-id="07983-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="07983-131">Vous verrez à quoi cela ressemble quand vous effectuez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="07983-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="07983-132">Vous pouvez récupérer les résultats d’une `Group Join` requête en tant que résultat non groupé en étendant votre requête pour retourner un élément pour chaque résultat de requête groupé.</span><span class="sxs-lookup"><span data-stu-id="07983-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="07983-133">Pour ce faire, vous devez vous assurer que vous interrogez la `DefaultIfEmpty` méthode de la collection groupée.</span><span class="sxs-lookup"><span data-stu-id="07983-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="07983-134">Cela permet de s’assurer que les éléments de la collection de la jointure située à gauche sont toujours inclus dans le résultat de la requête, même s’ils n’ont aucun résultat correspondant de la collection de droite.</span><span class="sxs-lookup"><span data-stu-id="07983-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="07983-135">Vous pouvez ajouter du code à votre requête pour fournir une valeur de résultat par défaut lorsqu’il n’existe aucune valeur correspondante de la collection de droite de la jointure.</span><span class="sxs-lookup"><span data-stu-id="07983-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="07983-136">Pour effectuer une jointure externe gauche à l’aide de la clause Group Join</span><span class="sxs-lookup"><span data-stu-id="07983-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="07983-137">Ajoutez le code suivant au `Module1` module dans votre projet pour voir des exemples de jointure externe gauche groupée et d’une jointure externe gauche non groupée.</span><span class="sxs-lookup"><span data-stu-id="07983-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="07983-138">Effectuer une jointure à l’aide d’une clé composite</span><span class="sxs-lookup"><span data-stu-id="07983-138">Perform a Join by Using a Composite Key</span></span>  

 <span data-ttu-id="07983-139">Vous pouvez utiliser le `And` mot clé dans `Join` une `Group Join` clause ou pour identifier plusieurs champs clés à utiliser lors de la mise en correspondance des valeurs des collections jointes.</span><span class="sxs-lookup"><span data-stu-id="07983-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="07983-140">Le `And` mot clé spécifie que tous les champs clés spécifiés doivent correspondre pour les éléments à joindre.</span><span class="sxs-lookup"><span data-stu-id="07983-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="07983-141">Pour effectuer une jointure à l’aide d’une clé composite</span><span class="sxs-lookup"><span data-stu-id="07983-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="07983-142">Ajoutez le code suivant au `Module1` module dans votre projet pour voir des exemples de jointure qui utilise une clé composite.</span><span class="sxs-lookup"><span data-stu-id="07983-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="07983-143">Exécuter le code</span><span class="sxs-lookup"><span data-stu-id="07983-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="07983-144">Pour ajouter du code pour exécuter les exemples</span><span class="sxs-lookup"><span data-stu-id="07983-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="07983-145">Remplacez `Sub Main` dans le `Module1` module de votre projet par le code suivant pour exécuter les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="07983-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="07983-146">Appuyez sur F5 pour exécuter les exemples.</span><span class="sxs-lookup"><span data-stu-id="07983-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07983-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07983-147">See also</span></span>

- [<span data-ttu-id="07983-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="07983-148">LINQ</span></span>](index.md)
- [<span data-ttu-id="07983-149">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07983-149">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="07983-150">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="07983-150">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="07983-151">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="07983-151">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="07983-152">From, clause</span><span class="sxs-lookup"><span data-stu-id="07983-152">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="07983-153">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="07983-153">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="07983-154">Requêtes</span><span class="sxs-lookup"><span data-stu-id="07983-154">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="07983-155">Transformations de données avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="07983-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
