---
title: ref, mot clé - Référence C#
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 61ee0e320f85925e4d804a6032e01c0485a31451
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249329"
---
# <a name="ref-c-reference"></a>ref (référence C#)

Le mot clé `ref` indique une valeur qui est passée par référence. Il est utilisé dans quatre contextes différents :

- Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence. Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).
- Dans une signature de méthode, pour retourner une valeur à l’appelant par référence. Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).
- Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier, ou une variable locale accède généralement à une valeur par référence. Pour plus d’informations, consultez [Variables locales ref](#ref-locals).
- Dans une déclaration de `struct` pour déclarer un `ref struct` ou un `readonly ref struct`. Pour plus d’informations, consultez [Types de structures ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Passage d’un argument par référence

Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur. Le mot clé `ref` fait du paramètre formel un alias de l’argument, qui doit être une variable. En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument. Par exemple, si l’appelant passe une expression variable locale ou une expression d’accès à l’élément de tableau, et que la méthode appelée remplace l’objet auquel le paramètre de l’arbitre se réfère, alors la variable locale de l’appelant ou l’élément de tableau se réfère maintenant au nouvel objet lorsque le la méthode revient.

> [!NOTE]
> Ne confondez pas le concept de passage par référence avec celui de types de référence. Les deux concepts ne sont pas identiques. Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence. Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.  

Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Un argument passé à un paramètre `ref` ou `in` doit être initialisé avant d’être transmis. Cette obligation diffère des paramètres [out](out-parameter-modifier.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.

Les membres d’une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref`, `in` ou `out`. Une erreur de compilation se produit si la seule différence entre deux membres d’un type est que l’un d’eux a un paramètre `ref` et que l’autre un a un paramètre `out` ou `in`. Le code suivant, par exemple, ne se compile pas.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Toutefois, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref`, `in` ou `out` et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `in`, `ref` et `out` font partie de la signature et ne correspondent pas l’un à l’autre.  
  
 Les propriétés ne sont pas des variables. Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.  
  
 Vous ne pouvez pas utiliser les mots clés `ref`, `in` ou `out` pour les types de méthodes suivants :  
  
- Méthodes async, que vous définissez à l’aide du modificateur [async](async.md).  
- Les méthodes Iterator, qui incluent une instruction [yield return](yield.md) ou `yield break`.

En outre, les [méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md) ont les restrictions suivantes :

- Le `out` keywoard ne peut pas être utilisé sur le premier argument d’une méthode d’extension.
- Le `ref` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension lorsque l’argument n’est pas une struction, ou un type générique non contraint d’être une struction.
- Le `in` mot clé ne peut pas être utilisé à moins que le premier argument soit une struction. Le `in` mot clé ne peut pas être utilisé sur n’importe quel type générique, même lorsqu’il est contraint d’être une struction.

## <a name="passing-an-argument-by-reference-an-example"></a>Passage d’un argument par référence : exemple

Les exemples précédents passent les types valeur par référence. Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence. Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant. L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence. Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant. L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Valeurs de retour de référence

Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant. Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et ce changement est reflété dans l’état de l’objet qui contient la méthode.

Une valeur de retour de référence est définie à l’aide du mot clé `ref` :

- Dans la signature de la méthode. Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.

```csharp
public ref decimal GetCurrentPrice()
```

- Entre le jeton `return` et la variable retournée dans une instruction `return` dans la méthode. Par exemple :

```csharp
return ref DecimalArray[0];
```

Pour que l’appelant puisse modifier l’état de l’objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals).

La méthode appelée peut également déclarer la valeur renvoyée en tant que `ref readonly` pour renvoyer la valeur par référence et faire en sorte que le code d'appel ne puisse pas modifier la valeur renvoyée. La méthode d’appel peut éviter de copier la valeur renvoyée en stockant la valeur dans une variable [ref readonly](#ref-readonly-locals) locale.

Par exemple, voir [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Variables locales ref

Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `return ref`. Vous ne pouvez pas initialiser une variable locale ref en valeur de retour non ref. En d’autres termes, la partie droite de l’initialisation doit être une référence. Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.

Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.

Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Vous pouvez accéder à une valeur par référence de la même façon. Dans certains cas, l’accès à une valeur par référence augmente les performances en évitant une opération de copie potentiellement coûteuse. Par exemple, l’instruction suivante montre comment il est possible de définir une valeur locale ref qui est utilisée pour référencer une valeur.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Notez que dans les deux exemples, le mot clé `ref` doit être utilisé aux deux emplacements, sans quoi le compilateur génère l’erreur CS8172, « Impossible d’initialiser une variable par référence avec une valeur ».

À partir de C# 7.3, la variable d’itération de l’instruction `foreach` peut être une variable locale ref ou une variable locale ref readonly. Pour plus d’informations, voir l’article [Instruction foreach](foreach-in.md).

En commençant également par C 7.3, vous pouvez réaffecter une variable locale ou réactive avec [l’opérateur d’affectation d’arbitres.](../operators/assignment-operator.md#ref-assignment-operator)

## <a name="ref-readonly-locals"></a>Variable locale ref readonly

Une variable locale ref readonly est utilisée pour se référer à des valeurs renvoyées par la méthode ou par la propriété comprenant `ref readonly` dans sa signature et utilise `return ref`. Une variable `ref readonly` combine les propriétés d’une variable locale `ref` avec une variable `readonly` : c’est un alias du stockage auquel elle est assignée et qui ne peut pas être modifié.

## <a name="a-ref-returns-and-ref-locals-example"></a>Exemple de retours ref et de variables locales ref

L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`. Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`. Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Types de structures ref

L’ajout du modificateur `ref` à une déclaration `struct` définit que les instances de ce type doivent être allouées par la pile. En d’autres termes, les instances de ces types ne peuvent jamais être créées sur un segment de mémoire en tant que membre d’une autre classe. Cette fonctionnalité vise principalement <xref:System.Span%601> et ses structures associées.

La conservation d’un type `ref struct` comme variable allouée par la pile introduit plusieurs règles que le compilateur applique pour tous les types `ref struct`.

- Vous ne pouvez pas effectuer d’opération box sur un `ref struct`. Vous ne pouvez pas assigner un type `ref struct` à une variable de type `object`, `dynamic` ou tout type interface.
- Les types `ref struct` ne peuvent pas implémenter les interfaces.
- Vous ne pouvez pas déclarer `ref struct` comme membre de champ d’une classe ou d’un struct normal. Cela comprend la déclaration d’une propriété implémentée automatiquement, qui crée un champ de stockage généré par le compilateur.
- Vous ne pouvez pas déclarer des variables locales qui sont des types `ref struct` dans des méthodes async. Vous pouvez les déclarer dans des méthodes synchrones qui retournent des types semblables à <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `Task`.
- Vous ne pouvez pas déclarer de variables locales `ref struct` dans des itérateurs.
- Vous ne pouvez pas capturer de variables `ref struct` dans des expressions lambda ou des fonctions locales.

Ces restrictions garantissent que vous n’utilisiez pas accidentellement une `ref struct` d’une manière qui pourrait la promouvoir auprès du tas managé.

Vous pouvez combiner des modificateurs pour déclarer une structure en tant que `readonly ref`. Une `readonly ref struct` combine les avantages et les restrictions des déclarations `ref struct` et `readonly struct`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Écrire du code sécurisé et efficace](../../write-safe-efficient-code.md)
- [Retours ref et variables locales ref](../../programming-guide/classes-and-structs/ref-returns.md)
- [Expression ref conditionnelle](../operators/conditional-operator.md#conditional-ref-expression)
- [Paramètres de passage](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Paramètres de méthodes](method-parameters.md)
- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
