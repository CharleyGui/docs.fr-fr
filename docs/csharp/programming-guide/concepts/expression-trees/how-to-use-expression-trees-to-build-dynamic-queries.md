---
title: Comment utiliser des arborescences d’expression pour générer des requêtes dynamiques (C#)
description: Découvrez comment utiliser des arborescences d’expressions pour créer des requêtes LINQ dynamiques. Ces requêtes sont utiles lorsque les caractéristiques d’une requête sont inconnues au moment de la compilation.
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: edcef4068c19ba8e789683cf6ba4d5ef2477e0d8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105588"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="f68f7-104">Comment utiliser des arborescences d’expression pour générer des requêtes dynamiques (C#)</span><span class="sxs-lookup"><span data-stu-id="f68f7-104">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="f68f7-105">Dans LINQ, des arborescences d’expressions sont utilisées pour représenter des requêtes structurées qui ciblent des sources de données qui implémentent <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="f68f7-105">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="f68f7-106">Par exemple, le fournisseur LINQ implémente l’interface <xref:System.Linq.IQueryable%601> pour interroger des magasins de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="f68f7-106">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="f68f7-107">Le compilateur C# compile les requêtes qui ciblent de telles sources de données dans du code qui génère une arborescence d’expressions lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f68f7-107">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="f68f7-108">Le fournisseur de requêtes peut ensuite parcourir la structure de données de l’arborescence d’expressions et la traduire en un langage de requête qui convienne à la source de données.</span><span class="sxs-lookup"><span data-stu-id="f68f7-108">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="f68f7-109">Des arborescences d’expressions sont aussi utilisées dans LINQ pour représenter des expressions lambda assignées à des variables de type <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="f68f7-109">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="f68f7-110">Cette rubrique explique comment utiliser des arborescences d’expressions pour créer des requêtes LINQ dynamiques.</span><span class="sxs-lookup"><span data-stu-id="f68f7-110">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="f68f7-111">Les requêtes dynamiques sont utiles lorsque les caractéristiques d’une requête ne sont pas connues au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f68f7-111">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="f68f7-112">Par exemple, une application peut fournir une interface utilisateur qui permet aux utilisateurs de spécifier un ou plusieurs prédicats pour filtrer des données.</span><span class="sxs-lookup"><span data-stu-id="f68f7-112">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="f68f7-113">Si vous souhaitez utiliser LINQ pour interroger des données, ce type d’application doit utiliser des arborescences d’expressions pour créer la requête LINQ au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f68f7-113">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f68f7-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="f68f7-114">Example</span></span>  
 <span data-ttu-id="f68f7-115">L’exemple suivant montre comment utiliser des arborescences d’expressions pour construire une requête et l’exécuter sur une source de données `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="f68f7-115">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="f68f7-116">Le code génère une arborescence d’expressions pour représenter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="f68f7-116">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="f68f7-117">Les méthodes de fabrique de l’espace de noms <xref:System.Linq.Expressions> sont utilisées pour créer des arborescences d’expressions qui représentent les expressions qui composent l’ensemble de la requête.</span><span class="sxs-lookup"><span data-stu-id="f68f7-117">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="f68f7-118">Les expressions qui représentent des appels aux méthodes d’opérateur de requête standard font référence aux implémentations <xref:System.Linq.Queryable> de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="f68f7-118">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="f68f7-119">L’arborescence d’expression finale est passée à l’implémentation <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> du fournisseur de la source de données `IQueryable` pour créer une requête exécutable de type `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="f68f7-119">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="f68f7-120">Les résultats sont obtenus par l’énumération de cette variable de requête.</span><span class="sxs-lookup"><span data-stu-id="f68f7-120">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="f68f7-121">Ce code utilise un nombre fixe d’expressions dans le prédicat qui est passé à la méthode `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="f68f7-121">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="f68f7-122">Toutefois, vous pouvez écrire une application qui combine un nombre variable d’expressions de prédicat dépendant des entrées utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f68f7-122">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="f68f7-123">Vous pouvez également varier les opérateurs de requête standard qui sont appelés dans la requête, en fonction des entrées utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f68f7-123">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f68f7-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f68f7-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="f68f7-125">Incluez l’espace de noms System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="f68f7-125">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f68f7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f68f7-126">See also</span></span>

- [<span data-ttu-id="f68f7-127">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="f68f7-127">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="f68f7-128">Comment exécuter des arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="f68f7-128">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="f68f7-129">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="f68f7-129">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
