---
title: Enum, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 48220fd1e88cf38e67db5dd3a2ad90638eb6b6df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343711"
---
# <a name="enum-statement-visual-basic"></a>Enum, instruction (Visual Basic)

Déclare une énumération et définit les valeurs de ses membres.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Composants

- `attributelist`

  Ce paramètre est facultatif. Liste des attributs qui s’appliquent à cette énumération. Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus («`<`» et «`>`»).

  L’attribut <xref:System.FlagsAttribute> indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres de l’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.

- `accessmodifier`

  Ce paramètre est facultatif. Spécifie le code qui peut accéder à cette énumération. Il peut s'agir de l'un des éléments suivants :

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  Ce paramètre est facultatif. Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez spécifier des [ombres](../../../visual-basic/language-reference/modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur l’un de ses membres.

- `enumerationname`

  Requis. Nom de l’énumération. Pour plus d’informations sur les noms valides, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Ce paramètre est facultatif. Type de données de l’énumération et de tous ses membres.

- `memberlist`

  Requis. Liste des constantes membres déclarées dans cette instruction. Plusieurs membres apparaissent sur des lignes de code source individuelles.

  Chaque `member` possède la syntaxe et les parties suivantes : `[<attribute list>] member name [ = initializer ]`

  |Élément|Description|
  |---|---|
  |`membername`|Requis. Nom de ce membre.|
  |`initializer`|Ce paramètre est facultatif. Expression évaluée au moment de la compilation et assignée à ce membre.|

- `End` `Enum`

  Met fin au bloc `Enum`.

## <a name="remarks"></a>Notes

Si vous avez un ensemble de valeurs immuables qui sont logiquement liées entre elles, vous pouvez les définir ensemble dans une énumération. Cela fournit des noms explicites pour l’énumération et ses membres, qui sont plus faciles à mémoriser que leurs valeurs. Vous pouvez ensuite utiliser les membres de l’énumération à de nombreux emplacements de votre code.

Les avantages de l’utilisation des énumérations sont les suivants :

- Réduit les erreurs dues à la transposition ou à la frappe de nombres.

- Facilite la modification des valeurs à l’avenir.

- Rend le code plus facile à lire, ce qui signifie qu’il est moins probable que des erreurs soient introduites.

- Garantit la compatibilité ascendante. Si vous utilisez des énumérations, votre code risque d’échouer si, à l’avenir, un utilisateur modifie les valeurs correspondant aux noms des membres.

Une énumération a un nom, un type de données sous-jacent et un ensemble de membres. Chaque membre représente une constante.

Une énumération déclarée au niveau de la classe, de la structure, du module ou de l’interface, en dehors de toute procédure, est une *énumération de membre*. Il est membre de la classe, de la structure, du module ou de l’interface qui le déclare.

Les énumérations de membres sont accessibles à partir de n’importe quel emplacement dans leur classe, structure, module ou interface. Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une énumération de membre avec le nom de la classe, de la structure ou du module. Vous pouvez éviter d’avoir à utiliser des noms qualifiés complets en ajoutant une instruction [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) au fichier source.

Une énumération déclarée au niveau de l’espace de noms, en dehors d’une classe, d’une structure, d’un module ou d’une interface, est un membre de l’espace de noms dans lequel elle apparaît.

Le *contexte de déclaration* pour une énumération doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement. Un attribut fournit des informations aux métadonnées de l’assembly.

## <a name="data-type"></a>Type de données

L’instruction `Enum` peut déclarer le type de données d’une énumération. Chaque membre prend le type de données de l’énumération. Vous pouvez spécifier `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`ou `UShort`.

Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de son `initializer`. Si vous spécifiez à la fois `datatype` et `initializer`, le type de données de `initializer` doit être convertible en `datatype`. Si ni `datatype` ni `initializer` n’est présent, le type de données prend par défaut la valeur `Integer`.

## <a name="initializing-members"></a>Initialisation des membres

L’instruction `Enum` peut initialiser le contenu des membres sélectionnés dans `memberlist`. Vous utilisez `initializer` pour fournir une expression à assigner au membre.

Si vous ne spécifiez pas `initializer` pour un membre, Visual Basic l’initialise soit sur zéro (s’il s’agit du premier `member` dans `memberlist`), soit sur une valeur supérieure à celle de la `member`précédente.

L’expression fournie dans chaque `initializer` peut être n’importe quelle combinaison de littéraux, d’autres constantes déjà définies et de membres d’énumération qui sont déjà définis, y compris un membre précédent de cette énumération. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner de tels éléments.

Vous ne pouvez pas utiliser de variables ou de fonctions dans `initializer`. Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`. Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, car cela peut être évalué au moment de la compilation.

Les énumérations ne peuvent pas avoir de valeurs à virgule flottante. Si une valeur à virgule flottante est assignée à un membre et que `Option Strict` a la valeur on, une erreur de compilateur se produit. Si `Option Strict` a la valeur OFF, la valeur est automatiquement convertie en type `Enum`.

Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacent, ou si vous initialisez un membre avec la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.

## <a name="modifiers"></a>Modificateurs

Les énumérations des classes, des structures, des modules et des membres d’interface sont par défaut accessibles au public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Les énumérations de membres d’espaces de noms ont par défaut accès Friend. Vous pouvez régler leurs niveaux d’accès sur public, mais pas sur privé ou protégé. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Tous les membres de l’énumération ont un accès public et vous ne pouvez pas utiliser de modificateurs d’accès sur ceux-ci. Toutefois, si l’énumération elle-même a un niveau d’accès plus restreint, le niveau d’accès de l’énumération spécifié est prioritaire.

Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes. Par conséquent, les mots clés `Shared`, `Static`et `ReadOnly` ne peuvent pas être utilisés lors de la déclaration d’une énumération ou de ses membres.

## <a name="assigning-multiple-values"></a>Attribution de plusieurs valeurs

Les énumérations représentent généralement des valeurs mutuellement exclusives. En incluant l’attribut <xref:System.FlagsAttribute> dans la déclaration `Enum`, vous pouvez à la place assigner plusieurs valeurs à une instance de l’énumération. L’attribut <xref:System.FlagsAttribute> spécifie que l’énumération doit être traitée comme un champ de bits, c’est-à-dire un ensemble d’indicateurs. Il s’agit des énumérations de *bits* .

Quand vous déclarez une énumération à l’aide de l’attribut <xref:System.FlagsAttribute>, nous vous recommandons d’utiliser les puissances de 2, c’est-à-dire 1, 2, 4, 8, 16, et ainsi de suite, pour les valeurs. Nous recommandons également que « None » soit le nom d’un membre dont la valeur est 0. Pour obtenir des instructions supplémentaires, consultez <xref:System.FlagsAttribute> et <xref:System.Enum>.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l’instruction `Enum`. Notez que le membre est appelé `EggSizeEnum.Medium`et non pas comme `Medium`.

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Exemple

La méthode de l’exemple suivant est en dehors de la classe `Egg`. Par conséquent, `EggSizeEnum` est entièrement qualifié en tant que `Egg.EggSizeEnum`.

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Exemple

L’exemple suivant utilise l’instruction `Enum` pour définir un ensemble de valeurs constantes nommées. Dans ce cas, les valeurs sont des couleurs que vous pouvez choisir pour concevoir des formulaires d’entrée de données pour une base de données.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Exemple

L’exemple suivant montre des valeurs qui incluent à la fois des nombres positifs et négatifs.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, une clause `As` est utilisée pour spécifier le `datatype` d’une énumération.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser une énumération au niveau du bit. Plusieurs valeurs peuvent être assignées à une instance d’une énumération au niveau du bit. La déclaration `Enum` comprend l’attribut <xref:System.FlagsAttribute>, qui indique que l’énumération peut être traitée comme un jeu d’indicateurs.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Exemple

L’exemple suivant itère au sein d’une énumération. Elle utilise la méthode <xref:System.Enum.GetNames%2A> pour récupérer un tableau de noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A> pour récupérer un tableau de valeurs de membre.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Constantes et énumérations](../../../visual-basic/language-reference/constants-and-enumerations.md)
