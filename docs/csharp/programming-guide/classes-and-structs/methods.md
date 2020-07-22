---
title: Méthodes - Guide de programmation C#
description: Une méthode en C# est un bloc de code qui contient une série d’instructions. Un programme exécute les instructions en appelant la méthode et en spécifiant des arguments.
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: db35b48d4d7e70a54b38342e79fa2881b3857bd7
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864148"
---
# <a name="methods-c-programming-guide"></a>Méthodes (Guide de programmation C#)

Une méthode est un bloc de code qui contient une série d'instructions. Un programme provoque l'exécution des instructions en appelant la méthode et en spécifiant les éventuels arguments de méthode requis. En C#, chaque instruction exécutée est effectuée dans le contexte d'une méthode. La `Main` méthode est le point d’entrée de chaque application C# et elle est appelée par le Common Language Runtime (CLR) au démarrage du programme.

> [!NOTE]
> Cet article décrit les méthodes nommées. Pour plus d’informations sur les fonctions anonymes, consultez [Fonctions anonymes](../statements-expressions-operators/anonymous-functions.md).

## <a name="method-signatures"></a>Signatures de méthode

Les méthodes sont déclarées dans une [classe](../../language-reference/keywords/class.md), un [struct](../../language-reference/builtin-types/struct.md)ou une [interface](../interfaces/index.md) en spécifiant le niveau d’accès comme `public` ou `private` , les modificateurs facultatifs tels que `abstract` ou `sealed` , la valeur de retour, le nom de la méthode et tous les paramètres de méthode. Ces parties forment ensemble la signature de la méthode.

> [!NOTE]
> Un type de retour d'une méthode ne fait pas partie de la signature de la méthode à des fins de surcharge de méthode. Toutefois, il fait partie de la signature de la méthode lors de la détermination de la compatibilité entre un délégué et la méthode vers laquelle il pointe.

Les paramètres de méthode sont placés entre parenthèses et séparés par des virgules. Des parenthèses vides indiquent que la méthode ne requiert aucun paramètre. Cette classe contient quatre méthodes :

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a>Accès aux méthodes

L'appel d'une méthode sur un objet revient à accéder à un champ. Après le nom de l'objet, ajoutez un point, le nom de la méthode et les parenthèses. Les arguments sont répertoriés entre les parenthèses et séparés par des virgules. Les méthodes de la classe `Motorcycle` peuvent donc être appelées comme dans l'exemple suivant :

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a>Paramètres de méthode et arguments

La définition de la méthode spécifie les noms et types des paramètres requis. Quand le code appelant appelle la méthode, il fournit des valeurs concrètes appelées arguments pour chaque paramètre. Les arguments doivent être compatibles avec le type de paramètre, mais le nom d’argument (le cas échéant) utilisé dans le code appelant ne doit pas nécessairement être le même que le paramètre nommé défini dans la méthode. Par exemple :

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Passage par référence et passage par valeur

Par défaut, lorsqu’une instance d’un [type valeur](../../language-reference/builtin-types/value-types.md) est passée à une méthode, sa copie est passée au lieu de l’instance elle-même. Par conséquent, les modifications apportées à l’argument n’ont aucun effet sur l’instance d’origine dans la méthode d’appel. Pour passer une instance de type valeur par référence, utilisez le `ref` mot clé. Pour plus d’informations, consultez [Passage de paramètres de type valeur ](./passing-value-type-parameters.md).

Quand un objet d'un type référence est passé à une méthode, une référence à l'objet est passée. Autrement dit, la méthode ne reçoit pas l'objet lui-même mais un argument qui indique l'emplacement de l'objet. Si vous modifiez un membre de l'objet à l'aide de cette référence, la modification est répercutée dans l'argument de la méthode d'appel, même si vous passez l'objet par valeur.

Vous créez un type référence à l’aide du `class` mot clé, comme le montre l’exemple suivant :

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

Maintenant, si vous passez un objet basé sur ce type à une méthode, une référence à l'objet est passée. L’exemple suivant passe un objet de type `SampleRefType` à la méthode `ModifyObject` :

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

L'exemple produit essentiellement la même chose que l'exemple précédent, dans la mesure où il passe un argument par valeur à une méthode. Mais, puisqu'un type référence est utilisé, le résultat est différent. La modification apportée dans `ModifyObject` au champ `value` du paramètre, `obj`, modifie également le champ `value` de l'argument, `rt`, dans la méthode `TestRefType` . La méthode `TestRefType` affiche 33 en tant que sortie.

Pour plus d’informations sur le passage de types référence par référence et par valeur, consultez [Passage de paramètres de type référence ](./passing-reference-type-parameters.md) et [Types référence](../../language-reference/keywords/reference-types.md).

## <a name="return-values"></a>Valeurs retournées

Les méthodes peuvent retourner une valeur à l'appelant. Si le type de retour, le type répertorié avant le nom de la méthode, n'est pas `void`, la méthode peut retourner la valeur à l'aide du mot clé `return` . Une instruction avec le mot clé `return` suivi d'une valeur qui correspond au type de retour retourne cette valeur à l'appelant de la méthode.

La valeur peut être retournée à l’appelant par valeur ou, à compter de C# 7.0, [par référence](ref-returns.md). Les valeurs sont retournées à l’appelant par référence si le mot clé `ref` est utilisé dans la signature de méthode et s’il suit chaque mot clé `return`. Par exemple, la signature de méthode suivante et l’instruction de retour indiquent que la méthode retourne un nom de variable `estDistance` par référence à l’appelant.

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

Le mot clé `return` arrête également l'exécution de la méthode. Si le type de retour est `void`, une instruction `return` sans valeur est quand même utile pour arrêter l'exécution de la méthode. Sans le mot clé `return` , la méthode arrête de s'exécuter quand elle atteint la fin du bloc de code. Les méthodes dotées d'un type de retour non void doivent utiliser le mot clé `return` pour retourner une valeur. Par exemple, ces deux méthodes utilisent le mot clé `return` pour retourner des entiers :

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

Pour utiliser une valeur retournée à partir d'une méthode, la méthode d'appel peut utiliser l'appel de méthode proprement dit partout où une valeur du même type peut suffire. Vous pouvez également affecter la valeur de retour à une variable. Par exemple, les deux exemples de code suivants remplissent le même objectif :

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

L'utilisation d'une variable locale, dans cet exemple, `result`, pour stocker une valeur est facultative. Elle peut favoriser la lisibilité du code ou s'avérer nécessaire si vous avez besoin de stocker la valeur d'origine de l'argument pour la portée entière de la méthode.

Pour utiliser une valeur retournée par référence à partir d’une méthode, vous devez déclarer une variable [ref local](ref-returns.md#ref-locals) si vous avez l’intention de modifier sa valeur. Par exemple, si la méthode `Planet.GetEstimatedDistance` retourne une valeur <xref:System.Double> par référence, vous pouvez la définir en tant que variable ref local avec du code semblable à celui-ci :

```csharp
ref int distance = plant
```

Le retour d’un tableau multidimensionnel à partir d’une méthode, `M`, qui modifie le contenu du tableau n’est pas nécessaire si la fonction appelante a passé le tableau à `M`.  Vous pouvez retourner le tableau obtenu à partir de `M` pour bénéficier d’un style approprié ou d’un flux fonctionnel de valeurs, mais cela n’est pas nécessaire, car C# passe tous les types de référence par valeur, et la valeur d’une référence de tableau est le pointeur qui désigne le tableau. Dans la méthode `M` , toute modification apportée au contenu du tableau est observable par tout code qui possède une référence au tableau, comme indiqué dans l’exemple suivant :

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

Pour plus d'informations, consultez [return](../../language-reference/keywords/return.md).

## <a name="async-methods"></a>Méthodes Async

La fonctionnalité async vous permet d'appeler des méthodes asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs méthodes ou expressions lambda.

Si vous marquez une méthode avec le modificateur [async](../../language-reference/keywords/async.md), vous pouvez utiliser l’opérateur [await](../../language-reference/operators/await.md) dans la méthode. Quand le contrôle atteint une expression await dans la méthode async, il retourne à l'appelant, et la progression dans la méthode est interrompue jusqu'à ce que la tâche attendue se termine. Quand la tâche est terminée, l'exécution peut reprendre dans la méthode.

> [!NOTE]
> Une méthode async retourne à l'appelant quand elle rencontre le premier objet await qui n'est pas encore terminé ou quand elle atteint la fin de la méthode async, selon la première éventualité.

Une méthode async peut avoir un type de retour <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>ou void. Le type de retour void est principalement utilisé pour définir les gestionnaires d'événements, où un type de retour void est requis. Une méthode async qui retourne void ne peut pas être attendue, et l'appelant d'une méthode retournant void ne peut intercepter aucune exception levée par la méthode.

Dans l'exemple suivant, `DelayAsync` est une méthode async dont le type de retour est <xref:System.Threading.Tasks.Task%601>. `DelayAsync` a une instruction `return` qui retourne un entier. Ainsi, la déclaration de méthode de `DelayAsync` doit avoir un type de retour de `Task<int>`. Étant donné que le type de retour est `Task<int>`, l'évaluation de l'expression `await` dans `DoSomethingAsync` produit un entier, comme le montre l'instruction suivante : `int result = await delayTask`.

La méthode `startButton_Click` est un exemple de méthode async dont le type de retour est void. Étant donné que `DoSomethingAsync` est une méthode async, la tâche pour l'appel à `DoSomethingAsync` doit être attendue, comme le montre l'instruction suivante : `await DoSomethingAsync();`. La méthode `startButton_Click` doit être définie avec le modificateur `async` car la méthode a une expression `await` .

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

Une méthode async ne peut pas déclarer de paramètres [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md) , mais elle peut appeler des méthodes qui comportent ces paramètres.

Pour plus d’informations sur les méthodes Async, consultez [programmation asynchrone avec Async et await](../concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../concepts/async/async-return-types.md).

## <a name="expression-body-definitions"></a>Définitions de corps d’expression

Il est courant d'avoir des définitions de méthode qui retournent tout simplement le résultat d'une expression immédiatement, ou qui ont une seule instruction en tant que corps de la méthode. Il existe un raccourci de syntaxe pour définir de telles méthodes en utilisant `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Si la méthode retourne `void` ou est une méthode async, alors le corps de la méthode doit être une expression d'instruction (même chose avec les expressions lambda). En ce qui concerne les propriétés et indexeurs, ils doivent être en lecture seule et vous n'utilisez pas le mot clé d'accesseur `get`.

## <a name="iterators"></a>Iterators

Un itérateur exécute une itération personnalisée sur une collection, comme une liste ou un tableau. Un itérateur utilise l'instruction [yield return](../../language-reference/keywords/yield.md) pour retourner chaque élément un par un. Quand une instruction [yield return](../../language-reference/keywords/yield.md) est atteinte, l'emplacement actuel dans le code est mémorisé. L'exécution redémarre à partir de cet emplacement au prochain appel de l'itérateur.

Vous appelez un itérateur depuis le code client en utilisant une instruction [foreach](../../language-reference/keywords/foreach-in.md).

Le type de retour d'un itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

Pour plus d’informations, consultez [itérateurs](../concepts/iterators.md).

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Classes statiques et membres de classe statique](static-classes-and-static-class-members.md)
- [Héritage](inheritance.md)
- [Classes abstract et sealed et membres de classe](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [renvoi](../../language-reference/keywords/return.md)
- [à](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Passer des paramètres](passing-parameters.md)
