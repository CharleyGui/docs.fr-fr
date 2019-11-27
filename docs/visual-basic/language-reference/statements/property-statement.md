---
title: Property Statement
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346755"
---
# <a name="property-statement"></a>Property Statement

Déclare le nom d’une propriété, ainsi que les procédures de propriété utilisées pour stocker et récupérer la valeur de la propriété.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a>Composants

- `attributelist`

  Ce paramètre est facultatif. Liste des attributs qui s’appliquent à cette propriété ou `Get` ou `Set` procédure. Consultez la [liste des attributs](attribute-list.md).

- `Default`

  Ce paramètre est facultatif. Spécifie que cette propriété est la propriété par défaut pour la classe ou la structure sur laquelle elle est définie. Les propriétés par défaut doivent accepter des paramètres et peuvent être définies et récupérées sans spécifier le nom de la propriété. Si vous déclarez la propriété comme `Default`, vous ne pouvez pas utiliser `Private` sur la propriété ou sur l’une de ses procédures de propriété.

- `accessmodifier`

  Facultatif sur l’instruction `Property` et sur au plus une des instructions `Get` et `Set`. Il peut s'agir de l'un des éléments suivants :

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  Consultez [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `propertymodifiers`

  Ce paramètre est facultatif. Il peut s'agir de l'un des éléments suivants :

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Ce paramètre est facultatif. Consultez [partagé](../modifiers/shared.md).

- `Shadows`

  Ce paramètre est facultatif. Consultez [Shadows](../modifiers/shadows.md).

- `ReadOnly`

  Ce paramètre est facultatif. Consultez [ReadOnly](../modifiers/readonly.md).

- `WriteOnly`

  Ce paramètre est facultatif. Consultez [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  Ce paramètre est facultatif. Consultez [iterator](../modifiers/iterator.md).

- `name`

  Requis. Nom de la propriété. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  Ce paramètre est facultatif. Liste des noms de variables locales qui représentent les paramètres de cette propriété, ainsi que des paramètres supplémentaires possibles de la procédure `Set`. Consultez la [liste des paramètres](parameter-list.md).

- `returntype`

  Obligatoire si `Option Strict` est `On`. Type de données de la valeur retournée par cette propriété.

- `Implements`

  Ce paramètre est facultatif. Indique que cette propriété implémente une ou plusieurs propriétés, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette propriété. Consultez [Implements, instruction](implements-statement.md).

- `implementslist`

  Obligatoire si `Implements` est utilisé. Liste des propriétés en cours d’implémentation.

  `implementedproperty [ , implementedproperty ... ]`

  Chaque `implementedproperty` emploie la syntaxe et les éléments suivants :

  `interface.definedname`

  |Élément|Description|
  |---|---|
  |`interface`|Requis. Nom d’une interface implémentée par la classe ou la structure conteneur de cette propriété.|
  |`definedname`|Requis. Nom par lequel la propriété est définie dans `interface`.|

- `Get`

  Ce paramètre est facultatif. Obligatoire si la propriété est marquée `ReadOnly`. Démarre une procédure de propriété `Get` qui est utilisée pour retourner la valeur de la propriété.  L’instruction `Get` n’est pas utilisée avec les [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `statements`

  Ce paramètre est facultatif. Bloc d’instructions à exécuter au sein de la procédure `Get` ou `Set`.

- `End Get`

  Met fin à la procédure de propriété `Get`.

- `Set`

  Ce paramètre est facultatif. Obligatoire si la propriété est marquée `WriteOnly`. Démarre une procédure de propriété `Set` qui est utilisée pour stocker la valeur de la propriété.  L’instruction `Set` n’est pas utilisée avec les [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `End Set`

  Met fin à la procédure de propriété `Set`.

- `End Property`

  Met fin à la définition de cette propriété.

## <a name="remarks"></a>Notes

L’instruction `Property` introduit la déclaration d’une propriété. Une propriété peut avoir une procédure `Get` (lecture seule), une procédure `Set` (écriture seule) ou les deux (lecture-écriture). Vous pouvez omettre les `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

Vous pouvez utiliser `Property` uniquement au niveau de la classe. Cela signifie que le *contexte de déclaration* pour une propriété doit être une classe, une structure, un module ou une interface, et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Par défaut, les propriétés utilisent un accès public. Vous pouvez ajuster le niveau d’accès d’une propriété à l’aide d’un modificateur d’accès sur l’instruction `Property`, et vous pouvez éventuellement ajuster l’une de ses procédures de propriété à un niveau d’accès plus restrictif.

Visual Basic passe un paramètre à la procédure `Set` au cours des assignations de propriété. Si vous ne fournissez pas de paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`. Ce paramètre contient la valeur à assigner à la propriété. En général, cette valeur est stockée dans une variable locale privée et elle est retournée à chaque appel de la procédure `Get`.

## <a name="rules"></a>Règles

- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` ou la procédure `Set`, mais pas les deux. Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Set` `Private`, mais pas `Public`.

  Si vous définissez une propriété `ReadOnly` ou `WriteOnly`, la procédure de propriété unique (`Get` ou `Set`, respectivement) représente la totalité de la propriété. Vous ne pouvez pas déclarer un niveau d’accès différent pour une telle procédure, car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.

- **Type de retour.** L’instruction `Property` peut déclarer le type de données de la valeur qu’elle retourne. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.

  Si vous ne spécifiez pas `returntype`, la propriété retourne `Object`.

- **Déploiement.** Si cette propriété utilise le mot clé `Implements`, la classe ou la structure conteneur doit avoir une instruction `Implements` immédiatement après son `Class` ou `Structure` instruction. L’instruction `Implements` doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit le `Property` (dans `definedname`) ne doit pas être le même que le nom de cette propriété (dans `name`).

## <a name="behavior"></a>Comportement

- **Retour d’une procédure de propriété.** Lorsque la procédure `Get` ou `Set` retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.

  Les instructions `Exit Property` et `Return` provoquent une sortie immédiate d’une procédure de propriété. Un nombre quelconque d’instructions `Exit Property` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Property` et `Return`.

- **Valeur de retour.** Pour retourner une valeur à partir d’une procédure `Get`, vous pouvez affecter la valeur au nom de la propriété ou l’inclure dans une instruction `Return`. L’exemple suivant affecte la valeur de retour au nom de la propriété `quoteForTheDay` puis utilise l’instruction `Exit Property` pour retourner.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  Si vous utilisez `Exit Property` sans assigner de valeur à `name`, la procédure `Get` retourne la valeur par défaut pour le type de données de la propriété.

  En même temps, l’instruction `Return` affecte la valeur de retour de la procédure `Get` et ferme la procédure. L’exemple suivant illustre cela.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Exemple

L’exemple suivant déclare une propriété dans une classe.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Voir aussi

- [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Get (instruction)](get-statement.md)
- [Set (instruction)](set-statement.md)
- [Liste de paramètres](parameter-list.md)
- [Default](../modifiers/default.md)
