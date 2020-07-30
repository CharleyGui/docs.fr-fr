---
title: Cast et conversions de types - Guide de programmation C#
description: En savoir plus sur le cast et les conversions de types, telles que les conversions implicites, explicites et définies par l’utilisateur.
ms.date: 07/06/2020
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 040b5679b1e6666a7f0308e5990781a2ef86c530
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381955"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Cast et conversions de types (guide de programmation C#)

C# étant typé statiquement au moment de la compilation, une fois qu’une variable est déclarée elle ne peut plus être redéclarée et aucune valeur d’un autre type ne peut lui être assignée, sauf si ce type peut être converti de manière implicite au type de la variable. Par exemple, `string` ne peut pas être converti implicitement en `int`. Après avoir déclaré `i` comme `int`, vous ne pouvez donc pas lui assigner la chaîne « Hello », comme l’illustre le code suivant :

```csharp
int i;

// error CS0029: Cannot implicitly convert type 'string' to 'int'
i = "Hello";
```

Cependant, vous pouvez être amené à copier une valeur dans un paramètre de variable ou de méthode d’un autre type. C’est notamment le cas si vous avez une variable de type entier que vous devez passer à une méthode dont le paramètre est de type `double`. Il peut également arriver que vous deviez assigner une variable de classe à une variable de type interface. Les opérations de ce genre sont appelées « *conversions de types* ». En C#, vous pouvez effectuer les conversions suivantes :

- **Conversions implicites**: aucune syntaxe spéciale n’est requise, car la conversion échoue toujours et aucune donnée n’est perdue. Citons par exemple les conversions de types intégraux en d’autres plus importants, et les conversions de classes dérivées en classes de base.

- **Conversions explicites (CASTS)**: les conversions explicites requièrent une [expression de cast](../../language-reference/operators/type-testing-and-cast.md#cast-expression). Un cast est exigé quand les informations peuvent être perdues durant la conversion, ou quand la conversion peut échouer pour d’autres raisons. Exemples classiques : conversion numérique en type qui a moins de précision ou une plus petite plage, et conversion d’une instance de classe de base en classe dérivée.

- **Conversions définies par l’utilisateur** : les conversions définies par l’utilisateur sont effectuées par des méthodes spéciales que vous pouvez définir pour permettre des conversions explicites ou implicites entre des types personnalisés qui n’ont pas de relation classe de base/classe dérivée. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](../../language-reference/operators/user-defined-conversion-operators.md).

- **Conversions avec les classes d’assistance** : pour effectuer une conversion entre des types non compatibles, tels que des entiers et des objets <xref:System.DateTime?displayProperty=nameWithType> ou des chaînes hexadécimales et des tableaux d’octets, vous pouvez utiliser la classe <xref:System.BitConverter?displayProperty=nameWithType>, la classe <xref:System.Convert?displayProperty=nameWithType> et les méthodes `Parse` des types numériques intégrés, comme <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [Comment convertir un tableau d’octets en int](./how-to-convert-a-byte-array-to-an-int.md), [Comment convertir une chaîne en nombre](./how-to-convert-a-string-to-a-number.md)et [Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).

## <a name="implicit-conversions"></a>Conversions implicites

Pour les types numériques intégrés, une conversion implicite peut être effectuée quand la valeur à stocker peut tenir dans la variable sans être tronquée ni arrondie. Pour les types intégraux, cela signifie que la plage du type de source est un sous-ensemble approprié de la plage du type cible. Par exemple, une variable de type [long](../../language-reference/builtin-types/integral-numeric-types.md) (entier sur 64 bits) peut stocker n’importe quelle valeur pouvant être stockée par un [int](../../language-reference/builtin-types/integral-numeric-types.md) (entier sur 32 bits). Dans l’exemple suivant, le compilateur convertit implicitement la valeur de `num` à droite en type `long` avant de l’assigner à `bigNum`.

[!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]

Pour obtenir la liste complète de toutes les conversions numériques implicites, consultez la section [conversions numériques implicites](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) de l’article [conversions numériques intégrées](../../language-reference/builtin-types/numeric-conversions.md) .

Pour les types référence, il existe toujours une conversion implicite entre une classe et l’une de ses interfaces ou classes de base directes ou indirectes. Aucune syntaxe spéciale n’est nécessaire, car une classe dérivée contient toujours tous les membres d’une classe de base.

```csharp
Derived d = new Derived();

// Always OK.
Base b = d;
```

## <a name="explicit-conversions"></a>Conversions explicites

Toutefois, si une conversion ne peut pas être réalisée sans risque de perte d’informations, le compilateur exige une conversion explicite, aussi appelée *cast*. Un cast est un moyen d’informer explicitement le compilateur que vous avez l’intention d’effectuer la conversion et que vous savez que la perte de données peut se produire, ou le cast peut échouer au moment de l’exécution. Pour effectuer un cast, spécifiez le type voulu entre parenthèses devant la valeur ou la variable à convertir. Le programme suivant convertit un [double](../../language-reference/builtin-types/floating-point-numeric-types.md) en [int](../../language-reference/builtin-types/integral-numeric-types.md). Le programme ne se compilera pas sans le cast.

[!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]

Pour obtenir la liste complète des conversions numériques explicites prises en charge, consultez la section [conversions numériques explicites](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) de l’article [conversions numériques intégrées](../../language-reference/builtin-types/numeric-conversions.md) .

Pour les types référence, un cast explicite est exigé si vous devez effectuer une conversion d’un type de base en type dérivé :

```csharp
// Create a new derived type.
Giraffe g = new Giraffe();

// Implicit conversion to base type is safe.
Animal a = g;

// Explicit conversion is required to cast back
// to derived type. Note: This will compile but will
// throw an exception at run time if the right-side
// object is not in fact a Giraffe.
Giraffe g2 = (Giraffe)a;
```

Une opération cast entre types référence ne change pas le type au moment de l’exécution de l’objet sous-jacent. Elle change seulement le type de la valeur utilisée comme référence à cet objet. Pour plus d’informations, consultez [Polymorphisme](../classes-and-structs/polymorphism.md).

## <a name="type-conversion-exceptions-at-run-time"></a>Exceptions de conversion de type au moment de l’exécution

Dans certaines conversions de types référence, le compilateur ne peut pas déterminer si un cast sera valide. Il est possible qu’une opération cast dont la compilation fonctionne échoue au moment de l’exécution. Comme l’illustre l’exemple suivant, un cast de type qui échoue au moment de l’exécution provoque la levée d’une exception <xref:System.InvalidCastException>.

[!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]

La `Test` méthode a un `Animal` paramètre, par conséquent le cast explicite `a` de l’argument en un `Reptile` fait une supposition dangereuse. Il est plus sûr de ne pas faire d’hypothèses, mais de vérifier le type. C# fournit l’opérateur [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) pour vous permettre de tester la compatibilité avant d’effectuer réellement un cast. Pour plus d’informations, consultez [Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs As et is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Conversions](~/_csharplang/spec/conversions.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Types](./index.md)
- [Expression Cast](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [Opérateurs de conversion définie par l’utilisateur](../../language-reference/operators/user-defined-conversion-operators.md)
- [Conversion de type généralisée](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Comment convertir une chaîne en nombre](./how-to-convert-a-string-to-a-number.md)
