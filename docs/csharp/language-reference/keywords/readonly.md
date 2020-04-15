---
title: readonly, mot clé - Référence C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389055"
---
# <a name="readonly-c-reference"></a>readonly (référence C#)

Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :

- Dans une déclaration `readonly` de [terrain](#readonly-field-example), indique que l’affectation sur le terrain ne peut se produire que dans le cadre de la déclaration ou dans un constructeur dans la même classe. Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.
  
  Un `readonly` champ ne peut pas être assigné après la sortie du constructeur. Cette règle a des implications différentes pour les types de valeur et les types de référence :
  
  - Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.
  - Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet. Cet objet n’est pas immuable. Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence. Toutefois, le modificateur n’empêche pas que les données d’instance du champ ne soient modifiées par le champ de lecture seulement.

  > [!WARNING]
  > Un type externement visible qui contient un champ de lecture-seulement visible à l’extérieur qui est un type de référence mutable peut être une vulnérabilité de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « Ne déclarez pas lu que les types de référence mutables. »

- Dans `readonly struct` une définition `readonly` de type, indique que le type de structure est immuable. Pour plus d’informations, consultez la [ `readonly` ](../builtin-types/struct.md#readonly-struct) section struct de l’article des types [structure.](../builtin-types/struct.md)
- Dans une déclaration de membre `readonly` dans un type de structure, indique qu’un membre de l’instance ne modifie pas l’état de la structure. Pour plus d’informations, consultez la [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) section des membres d’instance de l’article [de type Structure.](../builtin-types/struct.md)
- Dans [ `ref readonly` ](#ref-readonly-return-example)un retour `readonly` de méthode , le modificateur indique que la méthode renvoie une référence et écrit ne sont pas autorisés à cette référence.

Les `readonly struct` `ref readonly` contextes et les contextes ont été ajoutés dans C 7.2. `readonly`membres struct ont été ajoutés dans C 8.0

## <a name="readonly-field-example"></a>Exemple de champ en lecture seule

Dans cet exemple, la `year` valeur du champ ne `ChangeYear`peut pas être changée dans la méthode, même si elle est attribuée une valeur dans le constructeur de classe:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :

- Lorsque la variable est initialisée dans la déclaration, par exemple :

  ```csharp
  public readonly int y = 5;
  ```

- Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.
- Dans le constructeur statique de la classe qui contient la déclaration de champ statique.

Ces contextes constructeurs sont également les seuls contextes dans `readonly` lesquels il est valable de passer un champ comme un paramètre [out](out-parameter-modifier.md) ou [ref.](ref.md)

> [!NOTE]
> Le mot clé `readonly` est différent du mot clé [const](const.md). Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ. Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur. C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé. En outre, `const` alors qu’un champ est `readonly` une constante de compilateur- temps, le champ peut être employé pour des constantes de temps d’exécution comme dans l’exemple suivant :
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :

```csharp
p2.y = 66;        // Error
```

vous recevrez le message d’erreur du compilateur :

**Un champ de lecture ne peut pas être affecté à (sauf dans un constructeur ou un initialisateur variable)**

## <a name="ref-readonly-return-example"></a>Exemple de retour ref readonly

Le `readonly` modificateur `ref return` sur un indique que la référence retournée ne peut pas être modifiée. L’exemple suivant retourne une référence à l’origine. Il utilise `readonly` le modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Le type retourné ne doit pas nécessairement être un `readonly struct`. Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Vous pouvez également voir les propositions de spécification linguistique :

- [réajuster et structer readonly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [rétructurer les membres](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](index.md)
- [Modificateurs](index.md)
- [const](const.md)
- [Fields](../../programming-guide/classes-and-structs/fields.md)
