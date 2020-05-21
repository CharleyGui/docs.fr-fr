---
title: Interprétation des expressions
description: Découvrez comment écrire du code pour analyser la structure d’une arborescence d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 5734e1be6b59bfe3eae97f29d1bd91e7e3a3623f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761861"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="6b7ed-103">Interprétation des expressions</span><span class="sxs-lookup"><span data-stu-id="6b7ed-103">Interpreting Expressions</span></span>

[<span data-ttu-id="6b7ed-104">Précédent -- Exécution d’expressions</span><span class="sxs-lookup"><span data-stu-id="6b7ed-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="6b7ed-105">Nous allons maintenant écrire du code pour analyser la structure d’une *arborescence d’expressions*.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="6b7ed-106">Chaque nœud d’une arborescence d’expressions est un objet d’une classe dérivée de `Expression`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="6b7ed-107">Grâce à cette conception, visiter tous les nœuds d’une arborescence d’expressions est une opération récursive relativement simple.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="6b7ed-108">La stratégie générale consiste à débuter au niveau du nœud racine et à déterminer de quel genre de nœud il s’agit.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="6b7ed-109">Si le type de nœud a des enfants, visitez-les de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="6b7ed-110">Sur chaque nœud enfant, répétez le processus utilisé au niveau du nœud racine : déterminez le type et, s’il a des enfants, visitez chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="6b7ed-111">Examen d’une expression sans enfants</span><span class="sxs-lookup"><span data-stu-id="6b7ed-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="6b7ed-112">Commençons par visiter chaque nœud dans une arborescence d’expressions très simple.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="6b7ed-113">Voici le code qui crée une expression constante, puis examine ses propriétés :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="6b7ed-114">La sortie suivante est générée :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="6b7ed-115">Maintenant, nous allons écrire le code qui examinerait cette expression et écrirait certaines propriétés importantes à son sujet.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="6b7ed-116">Voici ce code :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="6b7ed-117">Examen d’une expression d’addition simple</span><span class="sxs-lookup"><span data-stu-id="6b7ed-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="6b7ed-118">Commençons par l’exemple d’addition issu de l’introduction à cette section.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="6b7ed-119">Je n’utilise pas `var` pour déclarer cette arborescence d’expressions. C’est impossible, car la partie droite de l’assignation est implicitement typée.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span>

<span data-ttu-id="6b7ed-120">Le nœud racine est `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-120">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="6b7ed-121">Pour obtenir le code intéressant du côté droit de l’opérateur `=>`, nous devons trouver l’un des enfants de `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-121">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="6b7ed-122">Nous allons le faire avec toutes les expressions dans cette section.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-122">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="6b7ed-123">Le nœud parent nous aide à trouver le type de retour de `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-123">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="6b7ed-124">Pour examiner chaque nœud de cette expression, nous devons visiter plusieurs nœuds de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-124">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="6b7ed-125">Voici une première implémentation simple :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-125">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="6b7ed-126">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-126">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="6b7ed-127">Vous remarquerez que l’exemple de code ci-dessus contient un grand nombre de répétitions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-127">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="6b7ed-128">Nous allons le nettoyer et générer un visiteur de nœud d’expression plus général.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-128">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="6b7ed-129">Pour cela, nous allons devoir écrire un algorithme récursif.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-129">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="6b7ed-130">Tout nœud peut être d’un type susceptible d’avoir des enfants.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-130">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="6b7ed-131">Tout nœud ayant des enfants nous oblige à visiter ces enfants et à déterminer ce qu’est ce nœud.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-131">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="6b7ed-132">Voici la version nettoyée qui utilise la récursivité pour visiter les opérations d’addition :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-132">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="6b7ed-133">Cet algorithme est la base d’un algorithme qui peut visiter toute `LambdaExpression` arbitraire.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-133">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="6b7ed-134">Ce code ne fait que rechercher un très petit échantillon des ensembles possibles de nœuds d’arborescences d’expressions qu’il peut rencontrer,</span><span class="sxs-lookup"><span data-stu-id="6b7ed-134">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="6b7ed-135">mais ce qu’il génère peut quand même nous en apprendre beaucoup.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-135">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="6b7ed-136">(Le cas par défaut dans la méthode `Visitor.CreateFromExpression` affiche un message dans la console d’erreurs quand un nouveau type de nœud est détecté.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-136">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="6b7ed-137">De cette façon, vous savez que vous devez ajouter un nouveau type d’expression.)</span><span class="sxs-lookup"><span data-stu-id="6b7ed-137">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="6b7ed-138">Quand nous exécutons ce visiteur sur l’expression d’addition ci-dessus, nous obtenons la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-138">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="6b7ed-139">Maintenant que nous avons créé une implémentation de visiteur plus générale, nous pouvons visiter et traiter de nombreux autres types d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-139">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="6b7ed-140">Examen d’une expression d’addition avec de nombreux niveaux</span><span class="sxs-lookup"><span data-stu-id="6b7ed-140">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="6b7ed-141">Essayons un exemple plus complexe, tout en continuant de limiter les types de nœuds à l’addition uniquement :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-141">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="6b7ed-142">Avant d’exécuter cet exemple sur l’algorithme visiteur, essayez de réfléchir à ce que pourrait être le résultat.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-142">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="6b7ed-143">N’oubliez pas que l’opérateur `+` est un *opérateur binaire* : il doit avoir deux enfants, représentant les opérandes gauche et droit.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-143">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="6b7ed-144">Il existe plusieurs manières correctes de construire une arborescence :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-144">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="6b7ed-145">Vous pouvez voir la séparation en deux réponses possibles, pour mettre en évidence la plus prometteuse.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-145">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="6b7ed-146">La première représente les expressions *associatives à droite*.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-146">The first represents *right associative* expressions.</span></span> <span data-ttu-id="6b7ed-147">La deuxième représente les expressions *associatives à gauche*.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-147">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="6b7ed-148">L’avantage de ces deux formats est qu’ils peuvent s’adapter à un nombre arbitraire d’expressions d’addition.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-148">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="6b7ed-149">Si nous exécutons cette expression dans le visiteur, nous obtenons ce résultat, qui vérifie que l’expression d’addition simple est *associative à gauche*.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-149">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="6b7ed-150">Pour exécuter cet exemple et voir l’arborescence d’expressions complète, j’ai dû apporter une modification à l’arborescence d’expressions source.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-150">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="6b7ed-151">Quand l’arborescence d’expressions contient uniquement des constantes, l’arborescence résultante contient simplement la valeur constante `10`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-151">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="6b7ed-152">Le compilateur effectue toute l’addition et réduit l’expression à sa forme la plus simple.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-152">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="6b7ed-153">Le simple ajout d’une variable dans l’expression suffit pour voir l’arborescence d’origine :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-153">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="6b7ed-154">Créez un visiteur pour cette somme et exécutez-le. Vous obtiendrez cette sortie :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-154">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="6b7ed-155">Vous pouvez également exécuter l’un des autres exemples dans le code de visiteur et voir quelle arborescence il représente.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-155">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="6b7ed-156">Voici un exemple de l’expression `sum3` ci-dessus (avec un paramètre supplémentaire pour empêcher le compilateur de calculer la constante) :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-156">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="6b7ed-157">Voici la sortie du visiteur :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-157">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="6b7ed-158">Notez que les parenthèses ne font pas partie de la sortie.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-158">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="6b7ed-159">Il n’y a aucun nœud dans l’arborescence d’expressions qui représente les parenthèses dans l’expression d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-159">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="6b7ed-160">La structure de l’arborescence d’expressions contient toutes les informations nécessaires pour communiquer le niveau de priorité.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-160">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="6b7ed-161">Extension de cet exemple</span><span class="sxs-lookup"><span data-stu-id="6b7ed-161">Extending from this sample</span></span>

<span data-ttu-id="6b7ed-162">L’exemple traite uniquement les arborescences d’expressions les plus rudimentaires.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-162">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="6b7ed-163">Le code que nous avons vu dans cette section gère seulement des entiers constants et l’opérateur binaire `+`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-163">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="6b7ed-164">En guise de dernier exemple, nous allons mettre à jour le visiteur pour gérer une expression plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-164">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="6b7ed-165">Prenons le code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-165">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="6b7ed-166">Il représente une implémentation possible de la fonction mathématique *factorial*.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-166">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="6b7ed-167">La façon dont ce code est écrit met en évidence deux limitations concernant la méthode de création d’arborescences d’expressions qui consiste à assigner des expressions lambda à Expression.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-167">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="6b7ed-168">Tout d’abord, les lambda-instructions ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-168">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="6b7ed-169">Cela signifie que je ne peux pas utiliser de boucles, de blocs, d’instructions if / else et d’autres structures de contrôle courantes en C#.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-169">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="6b7ed-170">Je suis limité à l’utilisation d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-170">I'm limited to using expressions.</span></span> <span data-ttu-id="6b7ed-171">Ensuite, je ne peux pas appeler la même expression de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-171">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="6b7ed-172">Je le pourrais s’il s’agissait déjà d’un délégué, mais je ne peux pas l’appeler sous sa forme d’arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-172">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="6b7ed-173">Dans la section sur la [génération d’arborescences d’expressions](expression-trees-building.md), vous découvrirez des techniques pour surmonter ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-173">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="6b7ed-174">Dans cette expression, vous rencontrerez des nœuds de tous ces types :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-174">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="6b7ed-175">Égal (expression binaire)</span><span class="sxs-lookup"><span data-stu-id="6b7ed-175">Equal (binary expression)</span></span>
2. <span data-ttu-id="6b7ed-176">Multiplier (expression binaire)</span><span class="sxs-lookup"><span data-stu-id="6b7ed-176">Multiply (binary expression)</span></span>
3. <span data-ttu-id="6b7ed-177">Conditionnel (l’expression</span><span class="sxs-lookup"><span data-stu-id="6b7ed-177">Conditional (the ?</span></span> <span data-ttu-id="6b7ed-178">? :)</span><span class="sxs-lookup"><span data-stu-id="6b7ed-178">: expression)</span></span>
4. <span data-ttu-id="6b7ed-179">Expression d’appel de méthode (appel de `Range()` et `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="6b7ed-179">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="6b7ed-180">L’une des manières de modifier l’algorithme visiteur consiste à continuer à l’exécuter, et à écrire le type de nœud chaque fois que vous atteignez votre clause `default`.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-180">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="6b7ed-181">Après quelques itérations, vous aurez vu chacun des nœuds potentiels.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-181">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="6b7ed-182">Vous aurez alors tout ce qu’il vous faut.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-182">Then, you have all you need.</span></span> <span data-ttu-id="6b7ed-183">Le résultat ressemblera à ceci :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-183">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="6b7ed-184">ConditionalVisitor et MethodCallVisitor traitent ces deux nœuds :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-184">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="6b7ed-185">Et la sortie de l’arborescence d’expressions sera :</span><span class="sxs-lookup"><span data-stu-id="6b7ed-185">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="6b7ed-186">Extension de la bibliothèque d’exemples</span><span class="sxs-lookup"><span data-stu-id="6b7ed-186">Extending the Sample Library</span></span>

<span data-ttu-id="6b7ed-187">Les exemples de cette section illustrent les techniques de base pour visiter et examiner des nœuds dans une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-187">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="6b7ed-188">Si j’ai ignoré de nombreuses actions dont vous pourriez avoir besoin, c’est pour mieux me concentrer sur les tâches fondamentales de visite et d’accès aux nœuds dans une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-188">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="6b7ed-189">Tout d’abord, les visiteurs gèrent uniquement les constantes qui sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-189">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="6b7ed-190">Les valeurs constantes peuvent être n’importe quel autre type numérique, et le langage C# prend en charge les conversions et les promotions entre ces types.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-190">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="6b7ed-191">Une version plus robuste de ce code mettrait en miroir toutes ces capacités.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-191">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="6b7ed-192">Même le dernier exemple reconnaît un sous-ensemble des types de nœuds possibles.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-192">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="6b7ed-193">Vous pouvez toujours lui fournir de nombreuses expressions qui entraîneront son échec.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-193">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="6b7ed-194">Une implémentation complète est fournie dans .NET Standard sous le nom <xref:System.Linq.Expressions.ExpressionVisitor>. Elle peut prendre en charge tous les types de nœud possibles.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-194">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="6b7ed-195">Pour finir, la bibliothèque que j’ai utilisée dans cet article a été créée à des fins de démonstration et de formation.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-195">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="6b7ed-196">Elle n’est pas optimisée.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-196">It's not optimized.</span></span> <span data-ttu-id="6b7ed-197">Je l’ai écrite pour rendre très claires les structures utilisées, et pour mettre en évidence les techniques employées pour visiter les nœuds et analyser ce qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-197">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="6b7ed-198">Une implémentation de production accorderait davantage d’attention aux performances.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-198">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="6b7ed-199">Même avec ces limitations, vous devriez être sur la bonne voie pour écrire des algorithmes qui lisent et comprennent les arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="6b7ed-199">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="6b7ed-200">Suivant -- Génération d’expressions</span><span class="sxs-lookup"><span data-stu-id="6b7ed-200">Next -- Building Expressions</span></span>](expression-trees-building.md)
