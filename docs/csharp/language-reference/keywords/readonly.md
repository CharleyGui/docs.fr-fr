---
title: readonly, mot clé - Référence C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368619"
---
# <a name="readonly-c-reference"></a>readonly (référence C#)

Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :

- Dans une [déclaration de champ](#readonly-field-example), `readonly` indique que l’assignation au champ peut uniquement se produire dans le cadre de la déclaration ou dans un constructeur de la même classe. Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.
  
  Un `readonly` champ ne peut pas être assigné après la sortie du constructeur. Cette règle a des implications différentes pour les types valeur et les types référence :
  
  - Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.
  - Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet. Cet objet n’est pas immuable. Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du champ en lecture seule.

  > [!WARNING]
  > Un type visible de l’extérieur qui contient un champ en lecture seule visible de l’extérieur qui est un type référence mutable peut être une faille de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « ne déclarez pas les types référence mutables en lecture seule ».

- Dans une `readonly struct` définition de type, `readonly` indique que le type de structure est immuable. Pour plus d’informations, consultez la section [ `readonly` struct](../builtin-types/struct.md#readonly-struct) de l’article [types de structures](../builtin-types/struct.md) .
- Dans une déclaration de membre d’instance au sein d’un type structure, `readonly` indique qu’un membre d’instance ne modifie pas l’état de la structure. Pour plus d’informations, consultez la section [ `readonly` membres d’instance](../builtin-types/struct.md#readonly-instance-members) de l’article [types de structures](../builtin-types/struct.md) .
- Dans une [ `ref readonly` méthode retournée](#ref-readonly-return-example), le `readonly` modificateur indique que la méthode retourne une référence et que les écritures ne sont pas autorisées à cette référence.

Les `readonly struct` `ref readonly` contextes et ont été ajoutés en C# 7,2. `readonly`des membres de struct ont été ajoutés en C# 8,0

## <a name="readonly-field-example"></a>Exemple de champ en lecture seule

Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear` , même si une valeur lui est assignée dans le constructeur de classe :

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :

- Lorsque la variable est initialisée dans la déclaration, par exemple :

  ```csharp
  public readonly int y = 5;
  ```

- Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.
- Dans le constructeur statique de la classe qui contient la déclaration de champ statique.

Ces contextes de constructeur sont également les seuls contextes dans lesquels il est possible de passer un `readonly` champ en tant que paramètre [out](out-parameter-modifier.md) ou [ref](ref.md) .

> [!NOTE]
> Le mot clé `readonly` est différent du mot clé [const](const.md). Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ. Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur. C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé. De même, si un `const` champ est une constante de compilation, le `readonly` champ peut être utilisé pour les constantes Runtime, comme dans l’exemple suivant :
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :

```csharp
p2.y = 66;        // Error
```

vous obtiendrez le message d’erreur du compilateur :

**Un champ ReadOnly ne peut pas être assigné (sauf s’il s’agit d’un constructeur ou d’un initialiseur de variable)**

## <a name="ref-readonly-return-example"></a>Exemple de retour ref readonly

Le `readonly` modificateur sur un `ref return` indique que la référence retournée ne peut pas être modifiée. L’exemple suivant retourne une référence à l’origine. Elle utilise le `readonly` modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Le type retourné ne doit pas nécessairement être un `readonly struct`. Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Vous pouvez également consulter les propositions de spécification de langage :

- [ReadOnly et struct ReadOnly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [membres de struct ReadOnly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [const](const.md)
- [Fields](../../programming-guide/classes-and-structs/fields.md)
