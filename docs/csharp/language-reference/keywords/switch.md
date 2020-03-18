---
title: switch, instruction (C#)
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345390"
---
# <a name="switch-c-reference"></a>switch (informations de référence sur C#)

`switch` est une instruction de sélection qui choisit une *section de commutation* unique à exécuter à partir d’une liste de candidats en fonction d’une mise en correspondance de modèle avec l’*expression de correspondance*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

L’instruction `switch` est souvent utilisée comme alternative à une construction [if-else](if-else.md) si une expression unique est testée en fonction de trois conditions ou plus. Par exemple, l’instruction `switch` suivante détermine laquelle des trois valeurs possibles a été affectée à une variable de type `Color` :

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Elle est équivalente à l’exemple suivant, qui utilise une construction `if`-`else`.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Expression de correspondance

L’expression de correspondance fournit la valeur à mettre en correspondance avec les modèles dans les étiquettes `case`. Sa syntaxe est la suivante :

```csharp
   switch (expr)
```

Avec C# 6 (et les versions antérieures), l’expression de correspondance doit retourner une valeur d’un des types suivants :

- [char](../builtin-types/char.md),
- une [chaîne](../builtin-types/reference-types.md).
- [bool](../builtin-types/bool.md),
- une valeur [intégrale,](../builtin-types/integral-numeric-types.md) telle qu’un `int` ou un `long`.
- une valeur [enum.](../builtin-types/enum.md)

À compter de C# 7.0, l’expression de correspondance peut être toute expression non Null.

## <a name="the-switch-section"></a>Section de commutation

Une instruction `switch` inclut une ou plusieurs sections de commutation. Chaque section de commutation contient une ou plusieurs *étiquettes case* (une case ou une étiquette par défaut) suivies d’une ou de plusieurs instructions. L’instruction `switch` peut inclure au maximum une étiquette par défaut, placée dans n’importe quelle section de commutation. L’exemple suivant montre une instruction `switch` simple qui a trois sections de commutation, chacune contenant à son tour deux instructions. La deuxième section de commutation contient les étiquettes `case 2:` et `case 3:`.

Une instruction `switch` peut inclure un nombre quelconque de sections de commutation, et chaque section peut contenir une ou plusieurs étiquettes case, comme dans l’exemple ci-dessous. Toutefois, deux étiquettes case ne doivent pas contenir la même expression.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Une seule section de commutation s’exécute dans une instruction switch. C# ne permet pas à l’exécution de passer d’une section switch à la suivante. Pour cette raison, le code suivant génère une erreur de compilateur, CS0163: "Le contrôle ne peut pas passer d’une étiquette de cas (étiquette\<de cas>) à l’autre."

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

Si cela est nécessaire, il est possible de procéder en quittant explicitement la section de commutation à l’aide d’une instruction [break](break.md), [goto](goto.md) ou [return](return.md). Toutefois, le code suivant est également valide, car il garantit que le contrôle du programme ne peut pas passer à la section switch `default`.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

L’exécution de la liste d’instructions dans la section de commutation avec une étiquette case qui correspond à l’expression de correspondance commence avec la première instruction et continue en suivant la liste d’instructions, en général jusqu’à ce qu’une instruction de saut, telle que `break`, `goto case`, `goto label`, `return` ou `throw`, soit atteinte. À ce stade, le contrôle est transféré hors de l'instruction `switch` ou vers un autre nom de cas. Si une instruction `goto` est utilisée, elle doit transférer le contrôle à une étiquette constante. Cette restriction est nécessaire, car tenter de transférer le contrôle à une étiquette non constante peut avoir des effets indésirables, tels que le transfert du contrôle à un emplacement inattendu dans le code ou la création d’une boucle sans fin.

## <a name="case-labels"></a>Étiquettes case

Chaque étiquette case spécifie un modèle à comparer à l’expression de correspondance (la variable `caseSwitch` dans les exemples précédents). S’ils correspondent, le contrôle est transféré à la section de commutation qui contient la **première** étiquette case correspondante. Si aucun modèle d’étiquette case ne correspond à l’expression de correspondance, le contrôle est transféré à la section comportant l’étiquette case `default`, s’il y en a une. En l’absence de cas `default`, aucune instruction d’aucune section switch n’est exécutée et le contrôle est transféré hors de l’instruction `switch`.

Pour plus d’informations sur l’instruction `switch` et les critères spéciaux, consultez la section [Critères spéciaux avec l’instruction `switch`](#pattern).

Étant donné que C# 6 ne prend en charge que le modèle de constante et n’autorise pas la répétition de valeurs constantes, les étiquettes case définissent des valeurs qui s’excluent mutuellement, et un seul modèle peut correspondre à l’expression utilisée. Par conséquent, l’ordre dans lequel les instructions `case` apparaissent n’a pas d’importance.

Dans C# 7.0, toutefois, comme d’autres modèles sont pris en charge, les étiquettes case ne sont pas tenues de définir des valeurs s’excluant mutuellement et plusieurs modèles peuvent correspondre à l’expression de correspondance. Comme seules les instructions de la première section de commutation contenant le modèle correspondant sont exécutées, l’ordre dans lequel les instructions `case` apparaissent est désormais important. Si C# détecte une section de commutation dont la ou les instructions case sont équivalentes aux instructions précédentes, ou en sont des sous-ensembles, C# génère une erreur du compilateur, CS8120, « Le switch case a déjà été pris en charge par un case antérieur ».

L’exemple suivant illustre une instruction `switch` qui utilise divers modèles ne s’excluant pas mutuellement. Si l’on déplace la section switch `case 0:` de sorte qu’elle n’est plus la première section de l’instruction `switch`, C# génère une erreur du compilateur, car un entier dont la valeur est égale à zéro est un sous-ensemble de tous les entiers, ce qui correspond au modèle défini par l’instruction `case int val`.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Vous pouvez corriger ce problème et éliminer l’avertissement du compilateur de deux façons :

- en modifiant l’ordre des sections de commutation ;

- en utilisant une [clause when](#when) dans l’étiquette `case`.

## <a name="the-default-case"></a>Étiquette case `default`

L’étiquette case `default` spécifie la section switch à exécuter si l’expression utilisée ne correspond à aucune autre étiquette `case`. En l’absence de cas `default`, si l’expression ne correspond à aucune autre étiquette `case`, le flux de programme passe à travers l’instruction `switch`.

L’étiquette case `default` peut apparaître à n’importe quelle position dans l’instruction `switch`. Quelle que soit sa position dans le code source, il est toujours évalué en dernier, une fois que toutes les étiquettes `case` ont été évaluées.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Critères spéciaux avec l’instruction `switch`

Chaque instruction `case` définit un modèle qui, s’il correspond à l’expression de correspondance, entraîne l’exécution de la section de commutation qui le contient. Toutes les versions de C# prennent en charge le modèle de constante. Les autres modèles sont pris en charge à compter de C# 7.0.

### <a name="constant-pattern"></a>Modèle de constante

Le modèle de constante teste si l’expression de correspondance est égale à une constante spécifiée. Sa syntaxe est la suivante :

```csharp
   case constant:
```

où *constant* est la valeur à tester. *constant* peut correspondre à l’une des expressions constantes suivantes :

- Un [bool](../builtin-types/bool.md) littéral: soit `true` ou `false`.
- Toute constante [intégrale,](../builtin-types/integral-numeric-types.md) comme un `int`, un `long`, ou un `byte`.
- Le nom d’une variable `const` déclarée
- Une constante d’énumération
- Un littéral de type [char](../builtin-types/char.md)
- Un littéral de type [string](../builtin-types/reference-types.md)

L’expression constante est évaluée de la manière suivante :

- Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).

- Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).

L’exemple suivant utilise le modèle de constante pour déterminer si une date particulière correspond à un jour de week-end, au premier jour de la semaine, au dernier jour de la semaine de travail ou au milieu de la semaine de travail. Il évalue la propriété <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> du jour actuel par rapport aux membres de l’énumération <xref:System.DayOfWeek>.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

L’exemple suivant utilise le modèle de constante pour gérer l’entrée d’utilisateur dans une application console qui simule une machine à café automatique.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Modèle de type

Le modèle de type permet une évaluation et une conversion rapides de type. Lorsqu’il est utilisé avec l’instruction `switch` pour effectuer une mise en correspondance de modèle, il permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, il effectue un cast de l’expression en une variable de ce type. Sa syntaxe est la suivante :

```csharp
   case type varname
```

où *type* est le nom du type vers lequel le résultat de *expr* doit être converti, et *varname* est l’objet vers lequel le résultat de *expr* est converti si la correspondance est établie. À compter de C# 7.1, le type *expr* au moment de la compilation peut être un paramètre de type générique.

L’expression `case` est `true` si l’une quelconque des affirmations suivantes est vraie :

- *expr* est une instance du même type que *type*.

- *expr* est une instance d’un type qui dérive de *type*. En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.

- *expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*. Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration de type. Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.

- *expr* est une instance d’un type qui implémente l’interface *type*.

Si l’expression case est true, *varname* est définitivement assigné et a une portée locale au sein de la section de commutation uniquement.

Notez que `null` ne correspond pas à un type. Pour mettre en correspondance `null`, vous utilisez l’étiquette `case` suivante :

```csharp
case null:
```

L’exemple suivant utilise le modèle de type pour fournir des informations sur différentes sortes de types de collection.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Au lieu de `object`, on pourrait créer une méthode générique en utilisant le type de la collection comme paramètre de type, comme le montre le code suivant :

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

La version générique présente deux différences avec le premier exemple. Tout d’abord, on ne peut pas utiliser le cas `null`. Aucun cas constant n’est possible, car le compilateur ne peut pas convertir un type arbitraire `T` en un type autre que `object`. Ce qui était auparavant le cas `default` teste maintenant la présence d’un `object` non Null, ce qui signifie que le cas `default` ne concerne que les valeurs `null`.

Sans critères spéciaux, ce code peut être écrit comme suit. L’utilisation de critères spéciaux de type génère un code plus compact et lisible en éliminant la nécessité de tester si le résultat d’une conversion est un `null` et d’effectuer des casts répétés.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> L’instruction `case` et la clause `when`

À compter de C# 7.0, comme les instructions case ne s’excluent pas nécessairement mutuellement, vous pouvez ajouter une clause `when` pour spécifier une condition supplémentaire qui doit être satisfaite pour que l’instruction case soit évaluée à true. La clause `when` peut être toute expression qui retourne une valeur booléenne.

L’exemple suivant définit une classe `Shape` de base, une classe `Rectangle` qui dérive de `Shape` et une classe `Square` qui dérive de `Rectangle`. Il utilise la clause `when` pour que `ShowShapeInfo` traite un objet `Rectangle` dont la longueur et la largeur sont égales à celles d’un `Square`, même s’il n’a pas été instancié comme objet `Square`. La méthode ne tente pas d’afficher des informations sur un objet `null` ou sur une forme dont l’aire est nulle.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Notez que la clause `when` de l’exemple qui tente de tester si un objet `Shape` est `null` ne s’exécute pas. Le modèle de type correct à utiliser pour tester un `null` est `case null:`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Instruction switch](~/_csharplang/spec/statements.md#the-switch-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [si-bien](if-else.md)
- [Filtrage](../../pattern-matching.md)
