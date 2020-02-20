---
title: readonly, mot clé - Référence C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: c3db8f7791e510768608e834339526fb82771979
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451939"
---
# <a name="readonly-c-reference"></a>readonly (référence C#)

Le mot clé `readonly` est un modificateur qui peut être utilisé dans quatre contextes :

- Dans une [déclaration de champ](#readonly-field-example), `readonly` indique qu’une affectation à destination d’un champ peut survenir uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe. Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur. 
  
  Un champ `readonly` ne peut pas être assigné après la sortie du constructeur. Cette règle a des implications différentes pour les types valeur et les types référence :
  
  - Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable. 
  - Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet. Cet objet n’est pas immuable. Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du champ en lecture seule.

  > [!WARNING]
  > Un type visible de l’extérieur qui contient un champ en lecture seule visible de l’extérieur qui est un type référence mutable peut être une faille de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « ne déclarez pas les types référence mutables en lecture seule ».

- Dans une définition [`readonly struct`](#readonly-struct-example), `readonly` indique que le `struct` est immuable.
- Dans une [définition de membre`readonly`](#readonly-member-examples), `readonly` indique qu’un membre d’un `struct` ne fait pas muter l’état interne de la structure.
- Dans une [`ref readonly` méthode retournée](#ref-readonly-return-example), le modificateur `readonly` indique que la méthode retourne une référence et que les écritures ne sont pas autorisées dans cette référence.

Les contextes `readonly struct` et `ref readonly` ont été ajoutés C# dans 7,2. `readonly` membres de struct ont été C# ajoutés dans 8,0

## <a name="readonly-field-example"></a>Exemple de champ en lecture seule

Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la `ChangeYear`de la méthode, même si une valeur lui est assignée dans le constructeur de classe :

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :

- Lorsque la variable est initialisée dans la déclaration, par exemple :

  ```csharp
  public readonly int y = 5;
  ```

- Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.
- Dans le constructeur statique de la classe qui contient la déclaration de champ statique.

Ces contextes de constructeur sont également les seuls contextes dans lesquels il est possible de passer un champ `readonly` en tant que paramètre [out](out-parameter-modifier.md) ou [ref](ref.md) .

> [!NOTE]
> Le mot clé `readonly` est différent du mot clé [const](const.md). Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ. Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur. C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé. De même, si un champ `const` est une constante de compilation, le champ `readonly` peut être utilisé pour les constantes Runtime, comme dans l’exemple suivant :
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :

```csharp
p2.y = 66;        // Error
```

vous obtiendrez le message d’erreur du compilateur :

**Un champ ReadOnly ne peut pas être assigné (sauf s’il s’agit d’un constructeur ou d’un initialiseur de variable)**

## <a name="readonly-struct-example"></a>Exemple de struct readonly

Le modificateur `readonly` dans une définition `struct` déclare que le struct est **immuable**. Chaque champ d’instance du `struct` doit être marqué `readonly`, comme dans l’exemple suivant :

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

L’exemple précédent utilise les [propriétés automatiques readonly](../../properties.md#read-only) pour déclarer son stockage. Il donne l’instruction au compilateur de créer des champs de stockage `readonly` pour ces propriétés. Vous pouvez aussi déclarer des champs `readonly` directement :

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

L’ajout d’un champ non marqué `readonly` génère l’erreur `CS8340` du compilateur : « Les champs d’instance de structs readonly doivent être en lecture seule ».

## <a name="readonly-member-examples"></a>Exemples de membres ReadOnly

Dans d’autres cas, vous pouvez créer un struct qui prend en charge la mutation. Dans ces cas, plusieurs membres d’instance ne modifieront probablement pas l’état interne de la structure. Vous pouvez déclarer ces membres d’instance avec le modificateur `readonly`. Le compilateur applique votre intention. Si ce membre modifie l’État directement ou accède à un membre qui n’est pas également déclaré avec le modificateur `readonly`, le résultat est une erreur au moment de la compilation. Le modificateur de `readonly` est valide sur `struct` membres, et non sur les déclarations de membres `class` ou `interface`.

Vous bénéficiez de deux avantages en appliquant le modificateur `readonly` aux méthodes `struct` applicables. Plus important encore, le compilateur applique votre intention. Le code qui modifie l’État n’est pas valide dans une méthode `readonly`. Le compilateur peut également utiliser le modificateur `readonly` pour activer les optimisations de performances. Quand des types de `struct` volumineux sont passés par `in` référence, le compilateur doit générer une copie défensive si l’état de la structure peut être modifié. Si vous accédez uniquement à `readonly` membres, le compilateur ne peut pas créer la copie défensive.

Le modificateur de `readonly` est valide sur la plupart des membres d’un `struct`, y compris les méthodes qui substituent les méthodes déclarées dans <xref:System.Object?displayProperty=nameWithType>. Certaines restrictions s’appliquent :

- Vous ne pouvez pas déclarer `readonly` des méthodes ou des propriétés statiques.
- Vous ne pouvez pas déclarer des constructeurs `readonly`.

Vous pouvez ajouter le modificateur `readonly` à une déclaration de propriété ou d’indexeur :

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Vous pouvez également ajouter le modificateur `readonly` aux accesseurs individuels `get` ou `set` d’une propriété ou d’un indexeur :

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Vous ne pouvez pas ajouter le modificateur `readonly` à la fois à une propriété et à un ou plusieurs des accesseurs de cette même propriété. Cette même restriction s’applique aux indexeurs.

Le compilateur applique implicitement le modificateur `readonly` aux propriétés implémentées automatiquement où le code implémenté par le compilateur ne modifie pas l’État. Elle est équivalente aux déclarations suivantes :

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

Vous pouvez ajouter le modificateur `readonly` dans ces emplacements, mais il n’aura aucun effet significatif. Vous ne pouvez pas ajouter le modificateur `readonly` à un accesseur Set de propriété implémentée automatiquement ou à une propriété implémentée automatiquement en lecture/écriture.

## <a name="ref-readonly-return-example"></a>Exemple de retour ref readonly

Le modificateur `readonly` sur une `ref return` indique que la référence retournée ne peut pas être modifiée. L’exemple suivant retourne une référence à l’origine. Elle utilise le modificateur `readonly` pour indiquer que les appelants ne peuvent pas modifier l’origine :

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Le type retourné ne doit pas nécessairement être un `readonly struct`. Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Vous pouvez également consulter les propositions de spécification de langage :

- [ReadOnly et struct ReadOnly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [membres de struct ReadOnly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [const](const.md)
- [Fields](../../programming-guide/classes-and-structs/fields.md)
