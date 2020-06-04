---
title: Enum (instruction)
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
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404730"
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

## <a name="parts"></a>Éléments

- `attributelist`

  Facultatif. Liste des attributs qui s’appliquent à cette énumération. Vous devez placer la [liste des attributs](attribute-list.md) entre crochets pointus (« `<` » et «» `>` ).

  L' <xref:System.FlagsAttribute> attribut indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres de l’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.

- `accessmodifier`

  Facultatif. Spécifie le code qui peut accéder à cette énumération. Il peut s'agir d'une des méthodes suivantes :

  - [Public](../modifiers/public.md)

  - [Protect](../modifiers/protected.md)

  - [Contact](../modifiers/friend.md)

  - [Privé](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Protégé privé](../modifiers/private-protected.md)

- `Shadows`

  Facultatif. Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez spécifier des [ombres](../modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur l’un de ses membres.

- `enumerationname`

  Obligatoire. Nom de l’énumération. Pour plus d’informations sur les noms valides, consultez [noms d’éléments déclarés](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Facultatif. Type de données de l’énumération et de tous ses membres.

- `memberlist`

  Obligatoire. Liste des constantes membres déclarées dans cette instruction. Plusieurs membres apparaissent sur des lignes de code source individuelles.

  Chaque `member` possède la syntaxe et les éléments suivants :`[<attribute list>] member name [ = initializer ]`

  |Élément|Description|
  |---|---|
  |`membername`|Obligatoire. Nom de ce membre.|
  |`initializer`|Facultatif. Expression évaluée au moment de la compilation et assignée à ce membre.|

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

Les énumérations de membres sont accessibles à partir de n’importe quel emplacement dans leur classe, structure, module ou interface. Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une énumération de membre avec le nom de la classe, de la structure ou du module. Vous pouvez éviter d’avoir à utiliser des noms qualifiés complets en ajoutant une instruction [Imports](imports-statement-net-namespace-and-type.md) au fichier source.

Une énumération déclarée au niveau de l’espace de noms, en dehors d’une classe, d’une structure, d’un module ou d’une interface, est un membre de l’espace de noms dans lequel elle apparaît.

Le *contexte de déclaration* pour une énumération doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement. Un attribut fournit des informations aux métadonnées de l’assembly.

## <a name="data-type"></a>Type de données

L' `Enum` instruction peut déclarer le type de données d’une énumération. Chaque membre prend le type de données de l’énumération. Vous pouvez spécifier `Byte` , `Integer` , `Long` , `SByte` , `Short` , `UInteger` , `ULong` ou `UShort` .

Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de son `initializer` . Si vous spécifiez `datatype` `initializer` à la fois et, le type de données de `initializer` doit être convertible en `datatype` . Si ni `datatype` ni `initializer` n’est présent, le type de données prend par défaut la valeur `Integer` .

## <a name="initializing-members"></a>Initialisation des membres

L' `Enum` instruction peut initialiser le contenu des membres sélectionnés dans `memberlist` . Vous utilisez `initializer` pour fournir une expression à assigner au membre.

Si vous ne spécifiez pas `initializer` pour un membre, Visual Basic l’initialise sur zéro (s’il s’agit du premier `member` dans `memberlist` ) ou sur une valeur supérieure à celle du immédiatement précédent `member` .

L’expression fournie dans chaque `initializer` peut être toute combinaison de littéraux, d’autres constantes déjà définies et de membres d’énumération qui sont déjà définis, y compris un membre précédent de cette énumération. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner de tels éléments.

Vous ne pouvez pas utiliser de variables ou de fonctions dans `initializer` . Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort` . Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou un `Char` argument, car cela peut être évalué au moment de la compilation.

Les énumérations ne peuvent pas avoir de valeurs à virgule flottante. Si une valeur à virgule flottante est assignée à un membre et si a la valeur `Option Strict` on, une erreur de compilateur se produit. Si `Option Strict` est désactivé, la valeur est automatiquement convertie en `Enum` type.

Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacent, ou si vous initialisez un membre avec la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.

## <a name="modifiers"></a>Modificateurs

Les énumérations des classes, des structures, des modules et des membres d’interface sont par défaut accessibles au public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Les énumérations de membres d’espaces de noms ont par défaut accès Friend. Vous pouvez régler leurs niveaux d’accès sur public, mais pas sur privé ou protégé. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Tous les membres de l’énumération ont un accès public et vous ne pouvez pas utiliser de modificateurs d’accès sur ceux-ci. Toutefois, si l’énumération elle-même a un niveau d’accès plus restreint, le niveau d’accès de l’énumération spécifié est prioritaire.

Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes. Par conséquent `Shared` , les `Static` `ReadOnly` Mots clés, et ne peuvent pas être utilisés lors de la déclaration d’une énumération ou de ses membres.

## <a name="assigning-multiple-values"></a>Attribution de plusieurs valeurs

Les énumérations représentent généralement des valeurs mutuellement exclusives. En incluant l' <xref:System.FlagsAttribute> attribut dans la `Enum` déclaration, vous pouvez assigner à la place plusieurs valeurs à une instance de l’énumération. L' <xref:System.FlagsAttribute> attribut spécifie que l’énumération doit être traitée comme un champ de bits, c’est-à-dire un ensemble d’indicateurs. Il s’agit des énumérations de *bits* .

Quand vous déclarez une énumération à l’aide de l' <xref:System.FlagsAttribute> attribut, nous vous recommandons d’utiliser les puissances de 2, c’est-à-dire 1, 2, 4, 8, 16, et ainsi de suite, pour les valeurs. Nous recommandons également que « None » soit le nom d’un membre dont la valeur est 0. Pour obtenir des instructions supplémentaires, consultez <xref:System.FlagsAttribute> et <xref:System.Enum> .

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l’instruction `Enum`. Notez que le membre est appelé `EggSizeEnum.Medium` , et non As `Medium` .

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Exemple

La méthode de l’exemple suivant est en dehors de la `Egg` classe. Par conséquent, `EggSizeEnum` est qualifié complet comme `Egg.EggSizeEnum` .

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Exemple

L’exemple suivant utilise l' `Enum` instruction pour définir un ensemble connexe de valeurs de constantes nommées. Dans ce cas, les valeurs sont des couleurs que vous pouvez choisir pour concevoir des formulaires d’entrée de données pour une base de données.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Exemple

L’exemple suivant montre des valeurs qui incluent à la fois des nombres positifs et négatifs.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, une `As` clause est utilisée pour spécifier le `datatype` d’une énumération.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser une énumération au niveau du bit. Plusieurs valeurs peuvent être assignées à une instance d’une énumération au niveau du bit. La `Enum` déclaration comprend l' <xref:System.FlagsAttribute> attribut, qui indique que l’énumération peut être traitée comme un jeu d’indicateurs.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Exemple

L’exemple suivant itère au sein d’une énumération. Elle utilise la <xref:System.Enum.GetNames%2A> méthode pour récupérer un tableau de noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A> pour récupérer un tableau de valeurs de membre.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const (instruction)](const-statement.md)
- [Dim (instruction)](dim-statement.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Constantes et énumérations](../constants-and-enumerations.md)
