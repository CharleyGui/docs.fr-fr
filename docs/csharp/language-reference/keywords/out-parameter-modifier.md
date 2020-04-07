---
title: out, modificateur de paramètre - Référence C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 57308992268e1285cfeb82b28e2abf213e7a831b
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805858"
---
# <a name="out-parameter-modifier-c-reference"></a>out, modificateur de paramètre (référence C#)

Le mot clé `out` entraîne le passage des arguments par référence. Il fait du paramètre formel un alias de l’argument, qui doit être une variable. En d’autres termes, toute opération portant sur le paramètre est effectuée sur l’argument. Il est similaire au mot clé [ref](ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée. Il est également similaire au mot clé [in](in-parameter-modifier.md), à la différence que `in` n’autorise pas la méthode appelée à modifier la valeur d’argument. Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`. Par exemple :  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant. Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](out-generic-modifier.md).
  
Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode. Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.  
  
Les mots clés `in`, `ref` et `out` ne sont pas considérés comme faisant partie de la signature de méthode à des fins de résolution de surcharge. Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l’une d’elles accepte un argument `ref` ou `in` et que l’autre accepte un argument `out`. Le code suivant, par exemple, ne se compilera pas :  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Toutefois, la surcharge est autorisée si une méthode prend un argument `ref`, `in` ou `out`, et que l’autre méthode n’a aucun de ces modificateurs, comme suit :  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Le compilateur choisit la meilleure surcharge en mettant en correspondance les modificateurs de paramètre sur le site d’appel et les modificateurs de paramètre utilisés dans l’appel de méthode.

Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.
  
Vous ne pouvez pas utiliser les mots clés `in`, `ref` ou `out` pour les types de méthodes suivants :  
  
- Méthodes async, que vous définissez à l’aide du modificateur [async](./async.md).  
  
- Les méthodes Iterator, qui incluent une instruction [yield return](./yield.md) ou `yield break`.  

En outre, les [méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md) ont les restrictions suivantes :

- Le `out` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension.
- Le `ref` mot clé ne peut pas être utilisé sur le premier argument d’une méthode d’extension lorsque l’argument n’est pas une struction, ou un type générique non contraint d’être une struction.
- Le `in` mot clé ne peut pas être utilisé à moins que le premier argument soit une struction. Le `in` mot clé ne peut pas être utilisé sur n’importe quel type générique, même lorsqu’il est contraint d’être une struction.

## <a name="declaring-out-parameters"></a>Déclarer des paramètres `out`

Il arrive souvent que l’on déclare une méthode avec des arguments `out` pour qu’elle retourne plusieurs valeurs. À compter de C# 7.0, vous pouvez recourir aux [tuples](../../tuples.md) dans ce type de scénario. L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode. Le troisième argument est attribué à null. Cela permet aux méthodes de retourner des valeurs le cas échéant.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Appel d’une méthode avec un argument `out`

Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`. L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

À compter de C# 7.0, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte. Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode. L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

Dans l’exemple précédent, la variable `number` est fortement typée en `int`. Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>Spécification du langage C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](./index.md)
- [Paramètres de méthodes](./method-parameters.md)
