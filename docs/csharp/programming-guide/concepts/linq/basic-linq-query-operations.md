---
title: Opérations de requête LINQ de base (C#)
description: Présentez les expressions de requête LINQ et certaines opérations que vous pouvez effectuer dans une requête.
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 9f5d39e396e9be3e633326d4034a89d874373d75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159291"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="b2248-103">Opérations de requête LINQ de base (C#)</span><span class="sxs-lookup"><span data-stu-id="b2248-103">Basic LINQ Query Operations (C#)</span></span>

<span data-ttu-id="b2248-104">Cette rubrique fournit une brève introduction aux expressions de requête LINQ et à certains genres classiques d’opérations que vous effectuez dans une requête.</span><span class="sxs-lookup"><span data-stu-id="b2248-104">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="b2248-105">Vous trouverez des informations plus détaillées dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2248-105">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="b2248-106">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="b2248-106">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="b2248-107">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="b2248-107">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="b2248-108">Procédure pas à pas : écriture de requêtes en C#</span><span class="sxs-lookup"><span data-stu-id="b2248-108">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="b2248-109">Si vous êtes déjà familiarisé avec un langage de requête tel que SQL ou XQuery, vous pouvez ignorer la plupart des informations de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b2248-109">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="b2248-110">`from`Pour en savoir plus sur l’ordre des clauses dans les expressions de requête LINQ, consultez la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b2248-110">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="b2248-111">Obtention d’une source de données</span><span class="sxs-lookup"><span data-stu-id="b2248-111">Obtaining a Data Source</span></span>  

 <span data-ttu-id="b2248-112">Dans une requête LINQ, la première étape consiste à spécifier la source de données.</span><span class="sxs-lookup"><span data-stu-id="b2248-112">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="b2248-113">Dans C#, comme dans la plupart des langages de programmation, une variable doit être déclarée avant de pouvoir être utilisée.</span><span class="sxs-lookup"><span data-stu-id="b2248-113">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="b2248-114">Dans une requête LINQ, la `from` clause est d’abord introduite pour introduire la source de données ( `customers` ) et la *variable de portée* ( `cust` ).</span><span class="sxs-lookup"><span data-stu-id="b2248-114">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="b2248-115">La variable de portée est similaire à la variable d’itération dans une boucle `foreach`, à la différence qu’aucune itération réelle ne se produit dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="b2248-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="b2248-116">Quand la requête est exécutée, la variable de portée sert de référence à chaque élément consécutif dans `customers`.</span><span class="sxs-lookup"><span data-stu-id="b2248-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="b2248-117">Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="b2248-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="b2248-118">Des variables de portée supplémentaires peuvent être introduites par une clause `let`.</span><span class="sxs-lookup"><span data-stu-id="b2248-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="b2248-119">Pour plus d’informations, consultez [let, clause](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-119">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2248-120">Pour les sources de données non génériques telles que <xref:System.Collections.ArrayList>, la variable de portée doit être explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="b2248-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="b2248-121">Pour plus d’informations, consultez [Comment interroger un ArrayList avec LINQ (C#) et la](./how-to-query-an-arraylist-with-linq.md) [clause from](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-121">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="b2248-122">Filtrage</span><span class="sxs-lookup"><span data-stu-id="b2248-122">Filtering</span></span>  

 <span data-ttu-id="b2248-123">L'opération de requête la plus courante est probablement l'application d'un filtre sous forme d'expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="b2248-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="b2248-124">Du fait du filtre, la requête retourne uniquement les éléments pour lesquels l’expression a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="b2248-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="b2248-125">Le résultat est produit à l'aide de la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="b2248-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="b2248-126">En effet, le filtre spécifie les éléments à exclure de la séquence source.</span><span class="sxs-lookup"><span data-stu-id="b2248-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="b2248-127">Dans l’exemple suivant, seuls les clients (`customers`) qui ont une adresse à Londres sont retournés.</span><span class="sxs-lookup"><span data-stu-id="b2248-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="b2248-128">Vous pouvez utiliser les opérateurs logiques C# `AND` et `OR` habituels pour appliquer le nombre d’expressions de filtre nécessaire dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="b2248-128">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="b2248-129">Par exemple, pour retourner uniquement les clients situés à « Londres » ET (`AND`) dont le nom est « Devon », vous devez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b2248-129">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="b2248-130">Pour retourner les clients situés à Londres ou à Paris, vous devez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b2248-130">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="b2248-131">Pour plus d’informations, consultez [where, clause](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-131">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="b2248-132">Classement</span><span class="sxs-lookup"><span data-stu-id="b2248-132">Ordering</span></span>  

 <span data-ttu-id="b2248-133">Il est souvent utile de trier les données retournées.</span><span class="sxs-lookup"><span data-stu-id="b2248-133">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="b2248-134">La clause `orderby` permet de trier les éléments de la séquence retournée en fonction du comparateur par défaut pour le type qui est trié.</span><span class="sxs-lookup"><span data-stu-id="b2248-134">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="b2248-135">Par exemple, la requête suivante peut être étendue pour trier les résultats selon la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="b2248-135">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="b2248-136">Comme `Name` est une chaîne, le comparateur par défaut effectue un tri alphabétique de A à Z.</span><span class="sxs-lookup"><span data-stu-id="b2248-136">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="b2248-137">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `orderby…descending`.</span><span class="sxs-lookup"><span data-stu-id="b2248-137">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="b2248-138">Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-138">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="b2248-139">Regroupement</span><span class="sxs-lookup"><span data-stu-id="b2248-139">Grouping</span></span>  

 <span data-ttu-id="b2248-140">La clause `group` vous permet de grouper vos résultats selon une clé que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="b2248-140">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="b2248-141">Par exemple, vous pouvez spécifier un regroupement des résultats par ville (`City`) pour que tous les clients de Londres ou Paris soient dans des groupes individuels.</span><span class="sxs-lookup"><span data-stu-id="b2248-141">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="b2248-142">Dans ce cas, utilisez la clé `cust.City`.</span><span class="sxs-lookup"><span data-stu-id="b2248-142">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="b2248-143">Quand vous terminez une requête avec une clause `group`, les résultats sont présentés sous la forme d’une liste de listes.</span><span class="sxs-lookup"><span data-stu-id="b2248-143">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="b2248-144">Chaque élément de la liste est un objet qui a un membre `Key` et une liste d’éléments qui sont regroupés sous cette clé.</span><span class="sxs-lookup"><span data-stu-id="b2248-144">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="b2248-145">Quand vous itérez une requête qui produit une séquence de groupes, vous devez utiliser une boucle `foreach` imbriquée.</span><span class="sxs-lookup"><span data-stu-id="b2248-145">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="b2248-146">La boucle externe itère chaque groupe et la boucle interne itère les membres de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="b2248-146">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="b2248-147">Si vous devez faire référence aux résultats d’une opération de regroupement, utilisez le mot clé `into` pour créer un identificateur susceptible d’être interrogé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="b2248-147">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="b2248-148">La requête suivante retourne uniquement les groupes qui contiennent plus de deux clients :</span><span class="sxs-lookup"><span data-stu-id="b2248-148">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="b2248-149">Pour plus d’informations, consultez [Group, clause](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-149">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="b2248-150">Jonction</span><span class="sxs-lookup"><span data-stu-id="b2248-150">Joining</span></span>  

 <span data-ttu-id="b2248-151">Les opérations de jointure créent des associations entre les séquences qui ne sont pas explicitement modélisées dans les sources de données.</span><span class="sxs-lookup"><span data-stu-id="b2248-151">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="b2248-152">Par exemple, effectuez une jointure pour rechercher tous les clients et distributeurs qui se trouvent au même endroit.</span><span class="sxs-lookup"><span data-stu-id="b2248-152">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="b2248-153">Dans LINQ, la `join` clause fonctionne toujours sur les collections d’objets plutôt que sur les tables de base de données directement.</span><span class="sxs-lookup"><span data-stu-id="b2248-153">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="b2248-154">Dans LINQ, il n’est pas nécessaire d’utiliser `join` aussi souvent que dans SQL, car les clés étrangères dans LINQ sont représentées dans le modèle objet sous la forme de propriétés qui contiennent une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="b2248-154">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="b2248-155">Par exemple, un objet `Customer` contient une collection d’objets `Order`.</span><span class="sxs-lookup"><span data-stu-id="b2248-155">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="b2248-156">Au lieu d’effectuer une jointure, accédez aux commandes en utilisant la notation par points :</span><span class="sxs-lookup"><span data-stu-id="b2248-156">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="b2248-157">Pour plus d’informations, consultez [join, clause](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-157">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="b2248-158">Sélection (projections)</span><span class="sxs-lookup"><span data-stu-id="b2248-158">Selecting (Projections)</span></span>  

 <span data-ttu-id="b2248-159">La clause `select` produit les résultats de la requête et spécifie la « forme » ou le type de chaque élément retourné.</span><span class="sxs-lookup"><span data-stu-id="b2248-159">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="b2248-160">Par exemple, spécifiez si les résultats doivent contenir des objets `Customer` complets, un seul membre, un sous-ensemble de membres ou un type de résultat complètement différent basé sur un calcul ou une création d’objet.</span><span class="sxs-lookup"><span data-stu-id="b2248-160">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="b2248-161">Quand la clause `select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.</span><span class="sxs-lookup"><span data-stu-id="b2248-161">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="b2248-162">L’utilisation de projections pour transformer des données est une fonctionnalité puissante des expressions de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="b2248-162">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="b2248-163">Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](./data-transformations-with-linq.md) et [select, clause](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2248-163">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2248-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2248-164">See also</span></span>

- [<span data-ttu-id="b2248-165">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="b2248-165">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="b2248-166">Procédure pas à pas : écriture de requêtes en C#</span><span class="sxs-lookup"><span data-stu-id="b2248-166">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="b2248-167">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b2248-167">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="b2248-168">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="b2248-168">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
