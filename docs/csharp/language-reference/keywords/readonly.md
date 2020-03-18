---
title: readonly, mot clé - Référence C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399356"
---
# <a name="readonly-c-reference"></a>readonly (référence C#)

Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :

- Dans une déclaration `readonly` de [terrain](#readonly-field-example), indique que l’affectation sur le terrain ne peut se produire que dans le cadre de la déclaration ou dans un constructeur dans la même classe. Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.
  
  Un `readonly` champ ne peut pas être assigné après la sortie du constructeur. Cette règle a des implications différentes pour les types de valeur et les types de référence :
  
  - Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.
  - Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet. Cet objet n’est pas immuable. Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence. Toutefois, le modificateur n’empêche pas que les données d’instance du champ ne soient modifiées par le champ de lecture seulement.

  > [!WARNING]
  > Un type externement visible qui contient un champ de lecture-seulement visible à l’extérieur qui est un type de référence mutable peut être une vulnérabilité de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « Ne déclarez pas lu que les types de référence mutables. »

- Dans [ `readonly struct` ](#readonly-struct-example)une `readonly` définition , `struct` indique que le est immuable.
- Dans [ `readonly` ](#readonly-member-examples)une définition `readonly` de membre , `struct` indique qu’un membre d’un ne mute pas l’état interne de la struct.
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

## <a name="readonly-member-examples"></a>Exemples de membres Readonly

D’autres fois, vous pouvez créer une struct qui soutient la mutation. Dans ces cas, plusieurs des membres de l’instance ne modifieront probablement pas l’état interne de la struction. Vous pouvez déclarer ces `readonly` membres d’instance avec le modificateur. Le compilateur applique votre intention. Si ce membre modifie directement l’état ou accède à `readonly` un membre qui n’est pas également déclaré avec le modificateur, le résultat est une erreur de compilation. Le `readonly` modificateur `struct` est valable `class` `interface` sur les membres, non ou les déclarations des membres.

Vous gagnez deux avantages `readonly` en appliquant le modificateur aux méthodes applicables. `struct` Plus important encore, le compilateur applique votre intention. Le code qui modifie l’état `readonly` n’est pas valide dans une méthode. Le compilateur peut également `readonly` utiliser le modificateur pour permettre des optimisations de performance. Lorsque `struct` de grands `in` types sont adoptés par référence, le compilateur doit générer une copie défensive si l’état de la structe peut être modifié. Si `readonly` seulement les membres sont consultés, le compilateur ne peut pas créer la copie défensive.

Le `readonly` modificateur est valable `struct`sur la plupart des membres <xref:System.Object?displayProperty=nameWithType>d’un , y compris les méthodes qui remplacent les méthodes déclarées dans . Il y a quelques restrictions :

- Vous ne pouvez `readonly` pas déclarer des méthodes ou des propriétés statiques.
- Vous ne pouvez `readonly` pas déclarer les constructeurs.

Vous pouvez `readonly` ajouter le modificateur à une déclaration de propriété ou d’indexeur :

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Vous pouvez également `readonly` ajouter `get` le `set` modificateur à l’individu ou aux accesseurs d’une propriété ou d’un indexeur :

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Vous ne pouvez `readonly` pas ajouter le modificateur à la fois à une propriété et à un ou plusieurs des accesseurs de cette même propriété. Cette même restriction s’applique aux indexateurs.

Le compilateur applique `readonly` implicitement le modificateur aux propriétés auto-mises en œuvre où le code mis en œuvre par le compilateur ne modifie pas l’état. C’est l’équivalent des déclarations suivantes :

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

Vous pouvez `readonly` ajouter le modificateur dans ces endroits, mais il n’aura aucun effet significatif. Vous ne pouvez `readonly` pas ajouter le modificateur à un setter de propriété auto-mis en œuvre, ou à une propriété mise en œuvre automatique de lecture/écriture.

## <a name="ref-readonly-return-example"></a>Exemple de retour ref readonly

Le `readonly` modificateur `ref return` sur un indique que la référence retournée ne peut pas être modifiée. L’exemple suivant retourne une référence à l’origine. Il utilise `readonly` le modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Le type retourné ne doit pas nécessairement être un `readonly struct`. Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Vous pouvez également voir les propositions de spécification linguistique :

- [réajuster et structer readonly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [rétructurer les membres](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [const](const.md)
- [Champs](../../programming-guide/classes-and-structs/fields.md)
