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
# <a name="translate-expression-trees"></a>Traduire les arborescences d’expressions

[Précédent -- Génération d’expressions](expression-trees-building.md)

Dans cette dernière section, vous allez découvrir comment visiter chaque nœud dans une arborescence d’expressions lors de la génération d’une copie modifiée de cette arborescence d’expressions. Voici les techniques que vous utiliserez dans deux scénarios importants. La première consiste à comprendre les algorithmes exprimés par une arborescence d’expressions pour qu’elle puisse être traduite dans un autre environnement. La deuxième s’applique quand vous souhaitez modifier l’algorithme qui a été créé, par exemple pour ajouter la journalisation, intercepter des appels de méthode et les suivre, ou dans d’autres buts.

## <a name="translating-is-visiting"></a>Traduire signifie visiter

Le code que vous générez pour traduire une arborescence d’expressions est une extension de ce que vous avez déjà vu pour visiter tous les nœuds dans une arborescence. Quand vous traduisez une arborescence d’expressions, vous visitez tous les nœuds et, ce faisant, vous générez la nouvelle arborescence. Celle-ci peut contenir des références aux nœuds d’origine ou de nouveaux nœuds que vous avez placés dans l’arborescence.

Nous allons voir cela en action en visitant une arborescence d’expressions et en créant une nouvelle arborescence avec certains nœuds de substitution. Dans cet exemple, nous allons remplacer une constante par une autre dix fois plus grande.
Pour le reste, nous laisserons l’arborescence d’expressions intacte. Au lieu de lire la valeur de la constante et de la remplacer par une nouvelle constante, nous allons remplacer le nœud de constante par un nouveau nœud qui effectue la multiplication.

Ici, une fois que vous avez trouvé un nœud de constante, vous créez un nœud de multiplication dont les enfants sont la constante d’origine, et la constante `10` :

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

Quand nous remplaçons le nœud d’origine par le substitut, une nouvelle arborescence contenant nos modifications est formée. Nous pouvons vérifier cela en compilant et en exécutant l’arborescence remplacée.

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

Pour générer une nouvelle arborescence, il faut visiter les nœuds dans l’arborescence existante, créer de nouveaux nœuds et les insérer dans l’arborescence.

Cet exemple montre l’importance du caractère immuable des arborescences d’expressions. Notez que la nouvelle arborescence créée ci-dessus contient une combinaison de nœuds nouvellement créés et de nœuds de l’arborescence existante. Cela ne présente aucun risque, car les nœuds de l’arborescence existante ne peuvent pas être modifiés. Ceci est susceptible d’accroître l’efficacité de la mémoire.
Les mêmes nœuds sont utilisables dans toute une arborescence, ou dans plusieurs arborescences d’expressions. Étant donné que les nœuds ne peuvent pas être modifiés, le même nœud peut être réutilisé chaque fois qu’il est nécessaire.

## <a name="traversing-and-executing-an-addition"></a>Parcours et exécution d’une addition

Nous allons vérifier cela en générant un deuxième visiteur qui parcourt l’arborescence de nœuds d’addition et calcule le résultat. Pour cela, nous allons apporter quelques modifications au visiteur que nous avons vu jusqu’ici. Dans cette nouvelle version, le visiteur va retourner la somme partielle de l’opération d’addition jusqu’à ce point. Pour une expression constante, il s’agit simplement de la valeur de l’expression constante. Pour une expression d’addition, le résultat est la somme des opérandes gauche et droit, une fois ces arborescences parcourues.

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

Il y a pas mal de code ici, mais les concepts sont très abordables.
Ce code visite les enfants avec une recherche en profondeur. Quand il rencontre un nœud de constante, le visiteur retourne la valeur de la constante. Une fois que le visiteur a visité les deux enfants, ces enfants auront calculé la somme calculée pour cette sous-arborescence. Le nœud d’addition peut maintenant calculer sa somme.
Une fois que tous les nœuds dans l’arborescence d’expressions ont été visités, la somme a été calculée. Vous pouvez suivre l’exécution en exécutant l’exemple dans le débogueur.

Nous allons simplifier le suivi de l’analyse des nœuds et du calcul de la somme en parcourant l’arborescence. Voici une version mise à jour de la méthode Aggregate qui comprend des informations de suivi :

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

Son exécution sur la même expression génère la sortie suivante :

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

Suivez la sortie et suivez le code ci-dessus. Vous devriez pouvoir déterminer comment le code visite chaque nœud et calcule la somme à mesure qu’il parcourt l’arborescence et trouve la somme.

À présent, jetons un œil à une autre exécution, avec l’expression donnée par `sum1` :

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Voici la sortie de l’examen de cette expression :

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

Bien que la réponse finale soit la même, le parcours d’arborescence est complètement différent. Les nœuds sont parcourus dans un ordre différent, car l’arborescence a été construite avec différentes opérations survenant en premier.

## <a name="learning-more"></a>En savoir plus

Cet exemple montre un petit sous-ensemble du code que vous créeriez pour parcourir et interpréter les algorithmes représentés par une arborescence d’expressions. Pour obtenir une description complète de tout le travail nécessaire pour générer une bibliothèque à usage général qui traduit des arborescences d’expressions dans un autre langage, consultez [cette série](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) de Matt Warren. Elle décrit en détail comment traduire le code que vous pourriez rencontrer dans une arborescence d’expressions.

J’espère que cet article aura mis en évidence toute la puissance des arborescences d’expressions.
Vous pouvez examiner un ensemble de code, y apporter les modifications souhaitées et exécuter la version modifiée. Les arborescences d’expressions étant immuables, vous pouvez créer des arborescences à l’aide de composants d’arborescences existantes. Cela réduit la quantité de mémoire nécessaire pour créer des arborescences d’expressions.

[Suivant -- Récapitulatif](expression-trees-summary.md)
