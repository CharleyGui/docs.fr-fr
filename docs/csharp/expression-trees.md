---
title: Arborescences de l’expression
description: En savoir plus sur les arborescences d’expressions dans .NET Core et comment les utiliser pour représenter le code en tant que structures que vous pouvez examiner, modifier et exécuter.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036324"
---
# <a name="expression-trees"></a><span data-ttu-id="70862-103">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="70862-103">Expression Trees</span></span>

<span data-ttu-id="70862-104">Si vous avez déjà utilisé LINQ, vous connaissez une bibliothèque enrichie où les types `Func` font partie de l’ensemble d’API.</span><span class="sxs-lookup"><span data-stu-id="70862-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="70862-105">(Si vous n’êtes pas familiarisé avec LINQ, vous souhaiterez probablement lire [le didacticiel LINQ](linq/index.md) et l’article sur les [expressions lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) avant celui-ci.) Les *arborescences d’expressions* fournissent une interaction plus riche avec les arguments qui sont des fonctions.</span><span class="sxs-lookup"><span data-stu-id="70862-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="70862-106">Vous écrivez des arguments de fonction, généralement à l’aide d’expressions lambda, quand vous créez des requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="70862-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="70862-107">Dans une requête LINQ classique, ces arguments de fonction sont transformés en un délégué créé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="70862-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="70862-108">Quand vous souhaitez avoir une interaction plus complète, vous devez utiliser des *arborescences d’expressions*.</span><span class="sxs-lookup"><span data-stu-id="70862-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="70862-109">Les arborescences d’expressions représentent le code sous forme de structure que vous pouvez examiner, modifier ou exécuter.</span><span class="sxs-lookup"><span data-stu-id="70862-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="70862-110">Ces outils vous permettent de manipuler le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="70862-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="70862-111">Vous pouvez écrire du code qui examine les algorithmes en cours d’exécution ou injecte de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="70862-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="70862-112">Dans des scénarios avancés, vous pouvez modifier les algorithmes en cours d’exécution, et même traduire les expressions C# dans une autre forme en vue d’une exécution dans un autre environnement.</span><span class="sxs-lookup"><span data-stu-id="70862-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="70862-113">Vous avez probablement déjà écrit du code qui utilise des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="70862-114">Les API LINQ d’Entity Framework acceptent des arborescences d’expressions comme arguments pour le modèle d’expression de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="70862-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="70862-115">Cela permet à [Entity Framework](/ef/) de traduire la requête que vous avez écrite en C# en code SQL qui s’exécute dans le moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="70862-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="70862-116">[Moq](https://github.com/Moq/moq), framework de simulation populaire pour .NET, constitue un autre exemple.</span><span class="sxs-lookup"><span data-stu-id="70862-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="70862-117">Les sections suivantes de ce didacticiel expliquent en détail ce que sont les arborescences d’expressions, examinent les classes de framework qui prennent en charge les arborescences d’expressions et montrent comment utiliser des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="70862-118">Vous découvrirez comment lire des arborescences d’expressions, créer des arborescences d’expressions, créer des arborescences d’expressions modifiées et exécuter le code représenté par des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="70862-119">Une fois ce didacticiel terminé, vous serez prêt à utiliser ces structures pour créer des algorithmes adaptatifs enrichis.</span><span class="sxs-lookup"><span data-stu-id="70862-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="70862-120">Explication des arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="70862-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="70862-121">Comprenez la structure et les concepts derrière les *arborescences d’expressions*.</span><span class="sxs-lookup"><span data-stu-id="70862-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="70862-122">Types de frameworks prenant en charge les arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="70862-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="70862-123">Découvrez les structures et les classes qui définissent et manipulent des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="70862-124">Exécution d’expressions</span><span class="sxs-lookup"><span data-stu-id="70862-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="70862-125">Découvrez comment convertir une arborescence d’expressions représentée sous forme d’expression lambda en un délégué, et comment exécuter le délégué résultant.</span><span class="sxs-lookup"><span data-stu-id="70862-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="70862-126">Interprétation d’expressions</span><span class="sxs-lookup"><span data-stu-id="70862-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="70862-127">Découvrez comment parcourir et examiner des *arborescences d’expressions* pour comprendre quel est le code représenté par l’arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="70862-128">Création d’expressions</span><span class="sxs-lookup"><span data-stu-id="70862-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="70862-129">Découvrez comment construire les nœuds d’une arborescence d’expressions et comment générer des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="70862-130">Traduction d’expressions</span><span class="sxs-lookup"><span data-stu-id="70862-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="70862-131">Découvrez comment générer une copie modifiée d’une arborescence d’expressions ou comment traduire une arborescence d’expressions dans un format différent.</span><span class="sxs-lookup"><span data-stu-id="70862-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="70862-132">Conclusion</span><span class="sxs-lookup"><span data-stu-id="70862-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="70862-133">Passez en revue les informations sur les arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="70862-133">Review the information on expression trees.</span></span>
