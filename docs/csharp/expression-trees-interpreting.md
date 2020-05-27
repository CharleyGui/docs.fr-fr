---
title: Interprétation des expressions
description: Découvrez comment écrire du code pour analyser la structure d’une arborescence d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: ea205d42b02ea7b38c04cb70d322329cf7c1d495
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004645"
---
# <a name="interpreting-expressions"></a>Interprétation des expressions

[Précédent -- Exécution d’expressions](expression-trees-execution.md)

Nous allons maintenant écrire du code pour analyser la structure d’une *arborescence d’expressions*. Chaque nœud d’une arborescence d’expressions est un objet d’une classe dérivée de `Expression`.

Grâce à cette conception, visiter tous les nœuds d’une arborescence d’expressions est une opération récursive relativement simple. La stratégie générale consiste à débuter au niveau du nœud racine et à déterminer de quel genre de nœud il s’agit.

Si le type de nœud a des enfants, visitez-les de manière récursive. Sur chaque nœud enfant, répétez le processus utilisé au niveau du nœud racine : déterminez le type et, s’il a des enfants, visitez chacun d’eux.

## <a name="examining-an-expression-with-no-children"></a>Examen d’une expression sans enfants
Commençons par visiter chaque nœud dans une arborescence d’expressions simple.
Voici le code qui crée une expression constante, puis examine ses propriétés :

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

La sortie suivante est générée :

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Maintenant, nous allons écrire le code qui examinerait cette expression et écrirait certaines propriétés importantes à son sujet. Voici ce code :

## <a name="examining-a-simple-addition-expression"></a>Examen d’une expression d’addition simple

Commençons par l’exemple d’addition issu de l’introduction à cette section.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Je n’utilise pas `var` pour déclarer cette arborescence d’expressions. C’est impossible, car la partie droite de l’assignation est implicitement typée.

Le nœud racine est `LambdaExpression`. Pour obtenir le code intéressant sur le côté droit de l' `=>` opérateur, vous devez Rechercher l’un des enfants de `LambdaExpression` . Nous allons le faire avec toutes les expressions dans cette section. Le nœud parent nous aide à trouver le type de retour de `LambdaExpression`.

Pour examiner chaque nœud de cette expression, nous devons visiter plusieurs nœuds de manière récursive. Voici une première implémentation simple :

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

Cet exemple génère la sortie suivante :

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

Vous remarquerez que l’exemple de code ci-dessus contient un grand nombre de répétitions.
Nous allons le nettoyer et générer un visiteur de nœud d’expression plus général. Pour cela, nous allons devoir écrire un algorithme récursif. Tout nœud peut être d’un type susceptible d’avoir des enfants.
Tout nœud ayant des enfants nous oblige à visiter ces enfants et à déterminer ce qu’est ce nœud. Voici la version nettoyée qui utilise la récursivité pour visiter les opérations d’addition :

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

Cet algorithme est la base d’un algorithme qui peut visiter toute `LambdaExpression` arbitraire. Il existe de nombreux trous, à savoir que le code que j’ai créé recherche uniquement un très petit échantillon des jeux possibles de nœuds d’arborescence d’expressions qu’il peut rencontrer. mais ce qu’il génère peut quand même nous en apprendre beaucoup. (Le cas par défaut dans la méthode `Visitor.CreateFromExpression` affiche un message dans la console d’erreurs quand un nouveau type de nœud est détecté. De cette façon, vous savez que vous devez ajouter un nouveau type d’expression.)

Quand nous exécutons ce visiteur sur l’expression d’addition ci-dessus, nous obtenons la sortie suivante :

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

Maintenant que nous avons créé une implémentation de visiteur plus générale, nous pouvons visiter et traiter de nombreux autres types d’expressions.

## <a name="examining-an-addition-expression-with-many-levels"></a>Examen d’une expression d’addition avec de nombreux niveaux

Essayons un exemple plus complexe, tout en continuant de limiter les types de nœuds à l’addition uniquement :

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Avant d’exécuter cet exemple sur l’algorithme visiteur, essayez de réfléchir à ce que pourrait être le résultat. N’oubliez pas que l’opérateur `+` est un *opérateur binaire* : il doit avoir deux enfants, représentant les opérandes gauche et droit. Il existe plusieurs manières correctes de construire une arborescence :

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Vous pouvez voir la séparation en deux réponses possibles, pour mettre en évidence la plus prometteuse. La première représente les expressions *associatives à droite*. La deuxième représente les expressions *associatives à gauche*.
L’avantage de ces deux formats est qu’ils peuvent s’adapter à un nombre arbitraire d’expressions d’addition.

Si vous exécutez cette expression par l’intermédiaire du visiteur, vous verrez cette sortie, en vérifiant que l’expression d’addition simple est *associative à gauche*.

Pour exécuter cet exemple et voir l’arborescence d’expressions complète, j’ai dû apporter une modification à l’arborescence d’expressions source. Quand l’arborescence d’expressions contient uniquement des constantes, l’arborescence résultante contient simplement la valeur constante `10`. Le compilateur effectue toute l’addition et réduit l’expression à sa forme la plus simple. Le simple ajout d’une variable dans l’expression suffit pour voir l’arborescence d’origine :

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Créez un visiteur pour cette somme et exécutez-le. Vous obtiendrez cette sortie :

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

Vous pouvez également exécuter l’un des autres exemples dans le code de visiteur et voir quelle arborescence il représente. Voici un exemple de l’expression `sum3` ci-dessus (avec un paramètre supplémentaire pour empêcher le compilateur de calculer la constante) :

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Voici la sortie du visiteur :

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

Notez que les parenthèses ne font pas partie de la sortie. Il n’y a aucun nœud dans l’arborescence d’expressions qui représente les parenthèses dans l’expression d’entrée. La structure de l’arborescence d’expressions contient toutes les informations nécessaires pour communiquer le niveau de priorité.

## <a name="extending-from-this-sample"></a>Extension de cet exemple

L’exemple traite uniquement les arborescences d’expressions les plus rudimentaires. Le code que nous avons vu dans cette section gère seulement des entiers constants et l’opérateur binaire `+`. En guise de dernier exemple, nous allons mettre à jour le visiteur pour gérer une expression plus complexe. Prenons le code ci-dessous :

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Il représente une implémentation possible de la fonction mathématique *factorial*. La façon dont ce code est écrit met en évidence deux limitations concernant la méthode de création d’arborescences d’expressions qui consiste à assigner des expressions lambda à Expression. Tout d’abord, les lambda-instructions ne sont pas autorisées. Cela signifie que je ne peux pas utiliser de boucles, de blocs, d’instructions if / else et d’autres structures de contrôle courantes en C#. Je suis limité à l’utilisation d’expressions. Ensuite, je ne peux pas appeler la même expression de manière récursive.
Je le pourrais s’il s’agissait déjà d’un délégué, mais je ne peux pas l’appeler sous sa forme d’arborescence d’expressions. Dans la section relative à la [création d’arborescences d’expressions](expression-trees-building.md), vous apprendrez les techniques permettant de surmonter ces limitations.

Dans cette expression, vous rencontrerez des nœuds de tous ces types :

1. Égal (expression binaire)
2. Multiplier (expression binaire)
3. Conditionnel (l’expression ? :)
4. Expression d’appel de méthode (appel de `Range()` et `Aggregate()`)

L’une des manières de modifier l’algorithme visiteur consiste à continuer à l’exécuter, et à écrire le type de nœud chaque fois que vous atteignez votre clause `default`. Après quelques itérations, vous aurez vu chacun des nœuds potentiels. Vous aurez alors tout ce qu’il vous faut. Le résultat ressemblera à ceci :

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

ConditionalVisitor et MethodCallVisitor traitent ces deux nœuds :

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

Et la sortie de l’arborescence d’expressions sera :

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

## <a name="extending-the-sample-library"></a>Extension de la bibliothèque d’exemples

Les exemples de cette section illustrent les techniques de base pour visiter et examiner des nœuds dans une arborescence d’expressions. Si j’ai ignoré de nombreuses actions dont vous pourriez avoir besoin, c’est pour mieux me concentrer sur les tâches fondamentales de visite et d’accès aux nœuds dans une arborescence d’expressions.

Tout d’abord, les visiteurs gèrent uniquement les constantes qui sont des entiers. Les valeurs constantes peuvent être n’importe quel autre type numérique, et le langage C# prend en charge les conversions et les promotions entre ces types. Une version plus robuste de ce code mettrait en miroir toutes ces capacités.

Même le dernier exemple reconnaît un sous-ensemble des types de nœuds possibles.
Vous pouvez toujours lui fournir de nombreuses expressions qui entraîneront son échec.
Une implémentation complète est fournie dans .NET Standard sous le nom <xref:System.Linq.Expressions.ExpressionVisitor>. Elle peut prendre en charge tous les types de nœud possibles.

Pour finir, la bibliothèque que j’ai utilisée dans cet article a été créée à des fins de démonstration et de formation. Elle n’est pas optimisée. Je l’ai écrit pour rendre les structures utilisées de façon claire, et pour mettre en évidence les techniques utilisées pour visiter les nœuds et analyser ce qu’il y a. Une implémentation de production accorderait davantage d’attention aux performances.

Même avec ces limitations, vous devriez être sur la bonne voie pour écrire des algorithmes qui lisent et comprennent les arborescences d’expressions.

[Suivant -- Génération d’expressions](expression-trees-building.md)
