---
title: Dim (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744727"
---
# <a name="dim-statement-visual-basic"></a>Dim, instruction (Visual Basic)

Déclare et alloue de l’espace de stockage pour une ou plusieurs variables.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Parties

- `attributelist`

  Option facultative. Consultez la [liste des attributs](attribute-list.md).

- `accessmodifier`

  Option facultative. Il peut s'agir de l'un des éléments suivants :

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  Consultez [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `Shared`

  Option facultative. Consultez [partagé](../modifiers/shared.md).

- `Shadows`

  Option facultative. Consultez [Shadows](../modifiers/shadows.md).

- `Static`

  Option facultative. Consultez [static](../modifiers/static.md).

- `ReadOnly`

  Option facultative. Consultez [ReadOnly](../modifiers/readonly.md).

- `WithEvents`

  Option facultative. Spécifie qu’il s’agit de variables objets qui font référence à des instances d’une classe qui peuvent déclencher des événements. Consultez [WithEvents](../modifiers/withevents.md).

- `variablelist`

  Requis. Liste des variables déclarées dans cette instruction.

  `variable [ , variable ... ]`

  Chaque `variable` emploie la syntaxe et les éléments suivants :

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Partie|Description|
  |---|---|
  |`variablename`|Requis. Nom de la variable. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|Option facultative. Liste des limites de chaque dimension d’une variable de tableau.|
  |`New`|Option facultative. Crée une nouvelle instance de la classe lors de l’exécution de l’instruction `Dim`.|
  |`datatype`|Option facultative. Type de données de la variable.|
  |`With`|Option facultative. Introduit la liste d’initialiseurs d’objets.|
  |`propertyname`|Option facultative. Nom d’une propriété dans la classe à partir de laquelle vous effectuez une instance.|
  |`propinitializer`|Obligatoire après `propertyname` =. Expression évaluée et assignée au nom de la propriété.|
  |`initializer`|Facultatif si `New` n’est pas spécifié. Expression qui est évaluée et assignée à la variable lors de sa création.|

## <a name="remarks"></a>Notes

Le compilateur Visual Basic utilise l’instruction `Dim` pour déterminer le type de données de la variable et d’autres informations, telles que le code qui peut accéder à la variable. L’exemple suivant déclare une variable qui doit contenir une valeur `Integer`.

```vb
Dim numberOfStudents As Integer
```

Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Pour un type référence, vous utilisez le mot clé `New` pour créer une nouvelle instance de la classe ou de la structure spécifiée par le type de données. Si vous utilisez `New`, vous n’utilisez pas d’expression d’initialiseur. Au lieu de cela, vous fournissez des arguments, s’ils sont requis, au constructeur de la classe à partir de laquelle vous créez la variable.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Vous pouvez déclarer une variable dans une procédure, un bloc, une classe, une structure ou un module. Vous ne pouvez pas déclarer une variable dans un fichier source, un espace de noms ou une interface. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Une variable déclarée au niveau du module, en dehors de toute procédure, est une *variable membre* ou un *champ*. Les variables membres sont dans la portée de la classe, de la structure ou du module. Une variable déclarée au niveau de la procédure est une *variable locale*. Les variables locales se trouvent dans la portée uniquement dans leur procédure ou bloc.

Les modificateurs d’accès suivants sont utilisés pour déclarer des variables en dehors d’une procédure : `Public`, `Protected`, `Friend`, `Protected Friend`et `Private`. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Le mot clé `Dim` est facultatif et est généralement omis si vous spécifiez l’un des modificateurs suivants : `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`ou `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

Si `Option Explicit` est activé (valeur par défaut), le compilateur requiert une déclaration pour chaque variable que vous utilisez. Pour plus d’informations, consultez [Option Explicit, instruction](option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Spécification d’une valeur initiale

Vous pouvez assigner une valeur à une variable lors de sa création. Pour un type valeur, vous utilisez un *initialiseur* pour fournir une expression à assigner à la variable. L’expression doit correspondre à une constante qui peut être calculée au moment de la compilation.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Si un initialiseur est spécifié et qu’aucun type de données n’est spécifié dans une clause `As`, l' *inférence de type* est utilisée pour déduire le type de données de l’initialiseur. Dans l’exemple suivant, les `num1` et `num2` sont fortement typés en tant qu’entiers. Dans la deuxième déclaration, l’inférence de type déduit le type de la valeur 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

L’inférence de type s’applique au niveau de la procédure. Elle ne s’applique pas en dehors d’une procédure dans une classe, une structure, un module ou une interface. Pour plus d’informations sur l’inférence de type, consultez [instruction Option Infer](option-infer-statement.md) et [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).

Pour plus d’informations sur ce qui se passe quand un type de données ou un initialiseur n’est pas spécifié, consultez [types de données et valeurs par défaut](dim-statement.md#default) plus loin dans cette rubrique.

Vous pouvez utiliser un *initialiseur d’objet* pour déclarer des instances de types nommés et anonymes. Le code suivant crée une instance d’une classe `Student` et utilise un initialiseur d’objet pour initialiser les propriétés.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [initialiseurs d’objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), et [types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Déclaration de plusieurs variables

Vous pouvez déclarer plusieurs variables dans une instruction de déclaration, en spécifiant le nom de chaque variable et en suivant les parenthèses de chaque nom de tableau. Les variables multiples sont séparées par des virgules.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Si vous déclarez plusieurs variables avec une seule clause `As`, vous ne pouvez pas fournir un initialiseur pour ce groupe de variables.

Vous pouvez spécifier des types de données différents pour différentes variables à l’aide d’une clause `As` distincte pour chaque variable que vous déclarez. Chaque variable prend le type de données spécifié dans la première clause `As` rencontrée après sa partie `variablename`.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Tableaux

Vous pouvez déclarer une variable qui contiendra un *tableau*, qui peut contenir plusieurs valeurs. Pour spécifier qu’une variable contient un tableau, suivez son `variablename` immédiatement avec des parenthèses. Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/language-features/arrays/index.md).

Vous pouvez spécifier les limites inférieure et supérieure de chaque dimension d’un tableau. Pour ce faire, incluez un `boundslist` à l’intérieur des parenthèses. Pour chaque dimension, le `boundslist` spécifie la limite supérieure et éventuellement la limite inférieure. La limite inférieure est toujours égale à zéro, que vous la spécifiiez ou non. Chaque index peut varier de zéro à sa valeur limite supérieure.

Les deux instructions suivantes sont équivalentes. Chaque instruction déclare un tableau de 21 `Integer` éléments. Lorsque vous accédez au tableau, l’index peut varier de 0 à 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

L’instruction suivante déclare un tableau à deux dimensions de type `Double`. Le tableau comporte 4 lignes (3 + 1) de 6 colonnes (5 + 1) chacune. Notez qu’une limite supérieure représente la valeur la plus élevée possible pour l’index, et non la longueur de la dimension. La longueur de la dimension est la limite supérieure plus un.

```vb
Dim matrix2(3, 5) As Double
```

Un tableau peut avoir entre 1 et 32 dimensions.

Vous pouvez laisser toutes les limites vides dans une déclaration de tableau. Dans ce cas, le tableau a le nombre de dimensions que vous spécifiez, mais il n’est pas initialisé. Elle a la valeur `Nothing` jusqu’à ce que vous initialisez au moins certains de ses éléments. L’instruction `Dim` doit spécifier des limites pour toutes les dimensions ou pour aucune dimension.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Si le tableau a plusieurs dimensions, vous devez inclure des virgules entre les parenthèses pour indiquer le nombre de dimensions.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

Vous pouvez déclarer un *tableau de longueur zéro* en déclarant l’une des dimensions du tableau avec la valeur-1. Une variable qui contient un tableau de longueur zéro n’a pas la valeur `Nothing`. Des tableaux de longueur zéro sont requis par certaines fonctions common language runtime. Si vous essayez d’accéder à ce type de tableau, une exception d’exécution se produit. Pour plus d’informations, consultez [Tableaux](../../programming-guide/language-features/arrays/index.md).

Vous pouvez initialiser les valeurs d’un tableau à l’aide d’un littéral de tableau. Pour ce faire, placez les valeurs d’initialisation entre accolades (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Pour les tableaux multidimensionnels, l’initialisation de chaque dimension séparée est placée entre accolades dans la dimension externe. Les éléments sont spécifiés dans l’ordre ligne-principal.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Pour plus d’informations sur les littéraux de tableau, consultez [tableaux](../../programming-guide/language-features/arrays/index.md).

## <a name="default"></a>Valeurs et types de données par défaut

Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.

|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|
|---|---|---|---|
|Non|Non|`Dim qty`|Si [option strict](option-strict-statement.md) a la valeur OFF (valeur par défaut), la variable est définie sur `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Non|Oui|`Dim qty = 5`|Si [Option Infer](option-infer-statement.md) est activé (valeur par défaut), la variable prend le type de données de l’initialiseur. Consultez [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Consultez le tableau plus loin dans cette section.|
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|

Si vous spécifiez un type de données, mais que vous ne spécifiez pas d’initialiseur, Visual Basic initialise la variable à la valeur par défaut pour son type de données. Le tableau suivant indique les valeurs d’initialisation par défaut.

|Type de données|Valeur par défaut|
|---|---|
|Tous les types numériques (y compris `Byte` et `SByte`)|0|
|`Char`|Binaire 0|
|Tous les types référence (y compris `Object`, `String`et tous les tableaux)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00 du 1er janvier de l’année 1 (01/01/0001 12:00:00 AM)|

Chaque élément d’une structure est initialisé comme s’il s’agissait d’une variable distincte. Si vous déclarez la longueur d’un tableau mais que vous n’initialisez pas ses éléments, chaque élément est initialisé comme s’il s’agissait d’une variable distincte.

## <a name="static-local-variable-lifetime"></a>Durée de vie d’une variable locale statique

Une variable locale `Static` a une durée de vie plus longue que celle de la procédure dans laquelle elle est déclarée. Les limites de la durée de vie de la variable dépendent de l’endroit où la procédure est déclarée et si elle est `Shared`.

|Déclaration de procédure|Variable initialisée|La variable cesse d’être existante|
|---|---|---|
|Dans un module|La première fois que la procédure est appelée|Quand votre programme cesse de s’exécuter|
|Dans une classe ou une structure, la procédure est `Shared`|La première fois que la procédure est appelée sur une instance spécifique ou sur la classe ou la structure elle-même|Quand votre programme cesse de s’exécuter|
|Dans une classe ou une structure, la procédure n’est pas `Shared`|La première fois que la procédure est appelée sur une instance spécifique|Lorsque l’instance est libérée pour garbage collection (GC)|

## <a name="attributes-and-modifiers"></a>Attributs et modificateurs

Vous pouvez appliquer des attributs uniquement aux variables membres, et non aux variables locales. Un attribut fournit des informations aux métadonnées de l’assembly, ce qui n’est pas significatif pour le stockage temporaire, tel que les variables locales.

Au niveau du module, vous ne pouvez pas utiliser le modificateur `Static` pour déclarer des variables membres. Au niveau de la procédure, vous ne pouvez pas utiliser `Shared`, `Shadows`, `ReadOnly`, `WithEvents`ou n’importe quel modificateur d’accès pour déclarer des variables locales.

Vous pouvez spécifier le code qui peut accéder à une variable en fournissant une `accessmodifier`. Les variables de membre de classe et de module (en dehors de toute procédure) sont par défaut en accès privé, et les variables de membre de structure ont un accès public par défaut. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Vous ne pouvez pas utiliser de modificateurs d’accès sur des variables locales (à l’intérieur d’une procédure).

Vous pouvez spécifier des `WithEvents` uniquement sur des variables membres, et non sur des variables locales à l’intérieur d’une procédure. Si vous spécifiez `WithEvents`, le type de données de la variable doit être un type de classe spécifique, et non `Object`. Vous ne pouvez pas déclarer un tableau avec `WithEvents`. Pour plus d’informations sur les événements, consultez [événements](../../programming-guide/language-features/events/index.md).

> [!NOTE]
> Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une variable membre avec le nom de la classe, de la structure ou du module. Le code en dehors d’une procédure ou d’un bloc ne peut pas faire référence à des variables locales dans cette procédure ou ce bloc.

## <a name="releasing-managed-resources"></a>Libération des ressources managées

Le .NET Framework garbage collector supprime les ressources managées sans codage supplémentaire de votre part. Toutefois, vous pouvez forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.

Si une classe contient une ressource particulièrement précieuse et rare (telle qu’une connexion de base de données ou un descripteur de fichier), vous pouvez ne pas vouloir attendre la garbage collection suivante pour nettoyer une instance de classe qui n’est plus utilisée. Une classe peut implémenter l’interface <xref:System.IDisposable> pour fournir un moyen de libérer des ressources avant une garbage collection. Une classe qui implémente cette interface expose une méthode `Dispose` qui peut être appelée pour forcer la libération immédiate de ressources précieuses.

L’instruction `Using` automatise le processus d’acquisition d’une ressource, d’exécution d’un ensemble d’instructions, puis de suppression de la ressource. Toutefois, la ressource doit implémenter l’interface <xref:System.IDisposable>. Pour plus d’informations, consultez [using, instruction](using-statement.md).

## <a name="example"></a>Exemple

L’exemple suivant déclare des variables à l’aide de l’instruction `Dim` avec diverses options.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Exemple

L’exemple suivant répertorie les nombres premiers compris entre 1 et 30. La portée des variables locales est décrite dans commentaires de code.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, la variable `speedValue` est déclarée au niveau de la classe. Le mot clé `Private` est utilisé pour déclarer la variable. La variable est accessible par n’importe quelle procédure de la classe `Car`.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Voir aussi

- [Const (instruction)](const-statement.md)
- [ReDim (instruction)](redim-statement.md)
- [Option Explicit (instruction)](option-explicit-statement.md)
- [Option Infer (instruction)](option-infer-statement.md)
- [Option Strict (instruction)](option-strict-statement.md)
- [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Déclaration de variable](../../programming-guide/language-features/variables/variable-declaration.md)
- [Tableaux](../../programming-guide/language-features/arrays/index.md)
- [Initialiseurs d’objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Initialiseurs d’objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Guide pratique : déclarer un objet à l’aide d’un initialiseur d’objet](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
