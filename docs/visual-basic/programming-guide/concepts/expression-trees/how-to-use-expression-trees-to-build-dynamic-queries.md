---
title: "Comment : utiliser des arborescences d'expression pour générer des requêtes dynamiques"
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bf15880c1988ac5639dd80ba56d330372dc3803b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344713"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="bdd8a-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd8a-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="bdd8a-103">Dans LINQ, des arborescences d’expressions sont utilisées pour représenter des requêtes structurées qui ciblent des sources de données qui implémentent <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="bdd8a-104">Par exemple, le fournisseur LINQ implémente l’interface <xref:System.Linq.IQueryable%601> pour interroger des magasins de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="bdd8a-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="bdd8a-106">Le fournisseur de requêtes peut ensuite parcourir la structure de données de l’arborescence d’expressions et la traduire en un langage de requête qui convienne à la source de données.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="bdd8a-107">Des arborescences d’expressions sont aussi utilisées dans LINQ pour représenter des expressions lambda assignées à des variables de type <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="bdd8a-108">Cette rubrique explique comment utiliser des arborescences d’expressions pour créer des requêtes LINQ dynamiques.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="bdd8a-109">Les requêtes dynamiques sont utiles lorsque les caractéristiques d’une requête ne sont pas connues au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="bdd8a-110">Par exemple, une application peut fournir une interface utilisateur qui permet aux utilisateurs de spécifier un ou plusieurs prédicats pour filtrer des données.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="bdd8a-111">Si vous souhaitez utiliser LINQ pour interroger des données, ce type d’application doit utiliser des arborescences d’expressions pour créer la requête LINQ au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="bdd8a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bdd8a-112">Example</span></span>

<span data-ttu-id="bdd8a-113">L’exemple suivant montre comment utiliser des arborescences d’expressions pour construire une requête et l’exécuter sur une source de données `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="bdd8a-114">Le code génère une arborescence d’expressions pour représenter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="bdd8a-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="bdd8a-115">Les méthodes de fabrique de l’espace de noms <xref:System.Linq.Expressions> sont utilisées pour créer des arborescences d’expressions qui représentent les expressions qui composent l’ensemble de la requête.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="bdd8a-116">Les expressions qui représentent des appels aux méthodes d’opérateur de requête standard font référence aux implémentations <xref:System.Linq.Queryable> de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="bdd8a-117">L’arborescence d’expression finale est passée à l’implémentation <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> du fournisseur de la source de données `IQueryable` pour créer une requête exécutable de type `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="bdd8a-118">Les résultats sont obtenus par l’énumération de cette variable de requête.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-118">The results are obtained by enumerating that query variable.</span></span>

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

<span data-ttu-id="bdd8a-119">Ce code utilise un nombre fixe d’expressions dans le prédicat qui est passé à la méthode `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="bdd8a-120">Toutefois, vous pouvez écrire une application qui combine un nombre variable d’expressions de prédicat dépendant des entrées utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="bdd8a-121">Vous pouvez également varier les opérateurs de requête standard qui sont appelés dans la requête, en fonction des entrées utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="bdd8a-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bdd8a-122">Compiling the Code</span></span>

- <span data-ttu-id="bdd8a-123">Créez un projet d’**Application console**.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="bdd8a-124">Incluez l’espace de noms System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="bdd8a-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="bdd8a-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd8a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd8a-126">See also</span></span>

- [<span data-ttu-id="bdd8a-127">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd8a-127">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="bdd8a-128">How to: Execute Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd8a-128">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
