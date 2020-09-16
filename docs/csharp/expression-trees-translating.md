---
title: Traduction d’arborescences d’expressions
description: Découvrez comment visiter chaque nœud dans une arborescence d’expressions lors de la génération d’une copie modifiée de cette arborescence d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: cb64e79d915a5c5567d5a3d25f1d747df9687c87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537461"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="3dd13-103">Traduire les arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dd13-103">Translate expression trees</span></span>

[<span data-ttu-id="3dd13-104">Précédent -- Génération d’expressions</span><span class="sxs-lookup"><span data-stu-id="3dd13-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="3dd13-105">Dans cette dernière section, vous allez découvrir comment visiter chaque nœud dans une arborescence d’expressions lors de la génération d’une copie modifiée de cette arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="3dd13-106">Voici les techniques que vous utiliserez dans deux scénarios importants.</span><span class="sxs-lookup"><span data-stu-id="3dd13-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="3dd13-107">La première consiste à comprendre les algorithmes exprimés par une arborescence d’expressions pour qu’elle puisse être traduite dans un autre environnement.</span><span class="sxs-lookup"><span data-stu-id="3dd13-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="3dd13-108">La deuxième s’applique quand vous souhaitez modifier l’algorithme qui a été créé,</span><span class="sxs-lookup"><span data-stu-id="3dd13-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="3dd13-109">par exemple pour ajouter la journalisation, intercepter des appels de méthode et les suivre, ou dans d’autres buts.</span><span class="sxs-lookup"><span data-stu-id="3dd13-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="3dd13-110">Traduire signifie visiter</span><span class="sxs-lookup"><span data-stu-id="3dd13-110">Translating is Visiting</span></span>

<span data-ttu-id="3dd13-111">Le code que vous générez pour traduire une arborescence d’expressions est une extension de ce que vous avez déjà vu pour visiter tous les nœuds dans une arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="3dd13-112">Quand vous traduisez une arborescence d’expressions, vous visitez tous les nœuds et, ce faisant, vous générez la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="3dd13-113">Celle-ci peut contenir des références aux nœuds d’origine ou de nouveaux nœuds que vous avez placés dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="3dd13-114">Nous allons voir cela en action en visitant une arborescence d’expressions et en créant une nouvelle arborescence avec certains nœuds de substitution.</span><span class="sxs-lookup"><span data-stu-id="3dd13-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="3dd13-115">Dans cet exemple, nous allons remplacer une constante par une autre dix fois plus grande.</span><span class="sxs-lookup"><span data-stu-id="3dd13-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="3dd13-116">Pour le reste, nous laisserons l’arborescence d’expressions intacte.</span><span class="sxs-lookup"><span data-stu-id="3dd13-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="3dd13-117">Au lieu de lire la valeur de la constante et de la remplacer par une nouvelle constante, nous allons remplacer le nœud de constante par un nouveau nœud qui effectue la multiplication.</span><span class="sxs-lookup"><span data-stu-id="3dd13-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="3dd13-118">Ici, une fois que vous avez trouvé un nœud de constante, vous créez un nœud de multiplication dont les enfants sont la constante d’origine, et la constante `10` :</span><span class="sxs-lookup"><span data-stu-id="3dd13-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="3dd13-119">Quand nous remplaçons le nœud d’origine par le substitut, une nouvelle arborescence contenant nos modifications est formée.</span><span class="sxs-lookup"><span data-stu-id="3dd13-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="3dd13-120">Nous pouvons vérifier cela en compilant et en exécutant l’arborescence remplacée.</span><span class="sxs-lookup"><span data-stu-id="3dd13-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="3dd13-121">Pour générer une nouvelle arborescence, il faut visiter les nœuds dans l’arborescence existante, créer de nouveaux nœuds et les insérer dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="3dd13-122">Cet exemple montre l’importance du caractère immuable des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="3dd13-123">Notez que la nouvelle arborescence créée ci-dessus contient une combinaison de nœuds nouvellement créés et de nœuds de l’arborescence existante.</span><span class="sxs-lookup"><span data-stu-id="3dd13-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="3dd13-124">Cela ne présente aucun risque, car les nœuds de l’arborescence existante ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="3dd13-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="3dd13-125">Ceci est susceptible d’accroître l’efficacité de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="3dd13-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="3dd13-126">Les mêmes nœuds sont utilisables dans toute une arborescence, ou dans plusieurs arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="3dd13-127">Étant donné que les nœuds ne peuvent pas être modifiés, le même nœud peut être réutilisé chaque fois qu’il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3dd13-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="3dd13-128">Parcours et exécution d’une addition</span><span class="sxs-lookup"><span data-stu-id="3dd13-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="3dd13-129">Nous allons vérifier cela en générant un deuxième visiteur qui parcourt l’arborescence de nœuds d’addition et calcule le résultat.</span><span class="sxs-lookup"><span data-stu-id="3dd13-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="3dd13-130">Pour cela, nous allons apporter quelques modifications au visiteur que nous avons vu jusqu’ici.</span><span class="sxs-lookup"><span data-stu-id="3dd13-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="3dd13-131">Dans cette nouvelle version, le visiteur va retourner la somme partielle de l’opération d’addition jusqu’à ce point.</span><span class="sxs-lookup"><span data-stu-id="3dd13-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="3dd13-132">Pour une expression constante, il s’agit simplement de la valeur de l’expression constante.</span><span class="sxs-lookup"><span data-stu-id="3dd13-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="3dd13-133">Pour une expression d’addition, le résultat est la somme des opérandes gauche et droit, une fois ces arborescences parcourues.</span><span class="sxs-lookup"><span data-stu-id="3dd13-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="3dd13-134">Il y a pas mal de code ici, mais les concepts sont très abordables.</span><span class="sxs-lookup"><span data-stu-id="3dd13-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="3dd13-135">Ce code visite les enfants avec une recherche en profondeur.</span><span class="sxs-lookup"><span data-stu-id="3dd13-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="3dd13-136">Quand il rencontre un nœud de constante, le visiteur retourne la valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="3dd13-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="3dd13-137">Une fois que le visiteur a visité les deux enfants, ces enfants auront calculé la somme calculée pour cette sous-arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="3dd13-138">Le nœud d’addition peut maintenant calculer sa somme.</span><span class="sxs-lookup"><span data-stu-id="3dd13-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="3dd13-139">Une fois que tous les nœuds dans l’arborescence d’expressions ont été visités, la somme a été calculée.</span><span class="sxs-lookup"><span data-stu-id="3dd13-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="3dd13-140">Vous pouvez suivre l’exécution en exécutant l’exemple dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="3dd13-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="3dd13-141">Nous allons simplifier le suivi de l’analyse des nœuds et du calcul de la somme en parcourant l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="3dd13-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="3dd13-142">Voici une version mise à jour de la méthode Aggregate qui comprend des informations de suivi :</span><span class="sxs-lookup"><span data-stu-id="3dd13-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="3dd13-143">Son exécution sur la même expression génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3dd13-143">Running it on the same expression yields the following output:</span></span>

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="3dd13-144">Suivez la sortie et suivez le code ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3dd13-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="3dd13-145">Vous devriez pouvoir déterminer comment le code visite chaque nœud et calcule la somme à mesure qu’il parcourt l’arborescence et trouve la somme.</span><span class="sxs-lookup"><span data-stu-id="3dd13-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="3dd13-146">À présent, jetons un œil à une autre exécution, avec l’expression donnée par `sum1` :</span><span class="sxs-lookup"><span data-stu-id="3dd13-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="3dd13-147">Voici la sortie de l’examen de cette expression :</span><span class="sxs-lookup"><span data-stu-id="3dd13-147">Here's the output from examining this expression:</span></span>

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="3dd13-148">Bien que la réponse finale soit la même, le parcours d’arborescence est complètement différent.</span><span class="sxs-lookup"><span data-stu-id="3dd13-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="3dd13-149">Les nœuds sont parcourus dans un ordre différent, car l’arborescence a été construite avec différentes opérations survenant en premier.</span><span class="sxs-lookup"><span data-stu-id="3dd13-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="3dd13-150">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="3dd13-150">Learning More</span></span>

<span data-ttu-id="3dd13-151">Cet exemple montre un petit sous-ensemble du code que vous créeriez pour parcourir et interpréter les algorithmes représentés par une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="3dd13-152">Pour obtenir une description complète de tout le travail nécessaire pour générer une bibliothèque à usage général qui traduit des arborescences d’expressions dans un autre langage, consultez [cette série](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) de Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="3dd13-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="3dd13-153">Elle décrit en détail comment traduire le code que vous pourriez rencontrer dans une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="3dd13-154">J’espère que cet article aura mis en évidence toute la puissance des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="3dd13-155">Vous pouvez examiner un ensemble de code, y apporter les modifications souhaitées et exécuter la version modifiée.</span><span class="sxs-lookup"><span data-stu-id="3dd13-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="3dd13-156">Les arborescences d’expressions étant immuables, vous pouvez créer des arborescences à l’aide de composants d’arborescences existantes.</span><span class="sxs-lookup"><span data-stu-id="3dd13-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="3dd13-157">Cela réduit la quantité de mémoire nécessaire pour créer des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="3dd13-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="3dd13-158">Suivant -- Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="3dd13-158">Next -- Summing up</span></span>](expression-trees-summary.md)
