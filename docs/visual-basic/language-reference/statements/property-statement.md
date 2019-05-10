---
title: Property, instruction (Visual Basic)
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
ms.openlocfilehash: 55da13eec9dc555c320ecd48d22d984dfcfea84c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751054"
---
# <a name="property-statement"></a>Property Statement

Déclare le nom d’une propriété et les procédures de propriété utilisées pour stocker et récupérer la valeur de la propriété.

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

  Facultatif. Liste des attributs qui s’appliquent à cette propriété ou `Get` ou `Set` procédure. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).

- `Default`

  Facultatif. Spécifie que cette propriété est la propriété par défaut pour la classe ou structure sur lesquels il est défini. Propriétés par défaut doivent accepter des paramètres et peuvent être définies et récupérées sans spécifier le nom de propriété. Si vous déclarez la propriété comme `Default`, vous ne pouvez pas utiliser `Private` sur la propriété ou sur un de ses procédures de propriété.

- `accessmodifier`

  Facultatif sur le `Property` instruction et sur un de la `Get` et `Set` instructions. Il peut s'agir d'une des valeurs suivantes :

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `propertymodifiers`

  Facultatif. Il peut s'agir d'une des valeurs suivantes :

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Facultatif. Consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `ReadOnly`

  Facultatif. Consultez [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WriteOnly`

  Facultatif. Consultez [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).

- `Iterator`

  Facultatif. Consultez [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Obligatoire. Nom de la propriété. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  Facultatif. Liste des noms de variables locales représentant les paramètres de cette propriété et les éventuels paramètres supplémentaires de la `Set` procédure. Consultez [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).

- `returntype`

  Obligatoire si `Option Strict` est `On`. Type de données de la valeur retournée par cette propriété.

- `Implements`

  Facultatif. Indique que cette propriété implémente une ou plusieurs propriétés, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette propriété. Consultez [implémente instruction](../../../visual-basic/language-reference/statements/implements-statement.md).

- `implementslist`

  Obligatoire si `Implements` est utilisé. Liste de propriétés en cours d’implémentation.

  `implementedproperty [ , implementedproperty ... ]`

  Chaque `implementedproperty` emploie la syntaxe et les éléments suivants :

  `interface.definedname`

  |Élément|Description|
  |---|---|
  |`interface`|Obligatoire. Nom d’une interface implémentée par cette propriété de classe ou la structure conteneur.|
  |`definedname`|Obligatoire. Nom par lequel la propriété est définie dans `interface`.|

- `Get`

  Facultatif. Obligatoire si la propriété est marquée `WriteOnly`. Démarre un `Get` procédure de propriété qui est utilisée pour retourner la valeur de la propriété.

- `statements`

  Facultatif. Bloc d’instructions à exécuter dans le `Get` ou `Set` procédure.

- `End Get`

  Met fin à la `Get` procédure de propriété.

- `Set`

  Facultatif. Obligatoire si la propriété est marquée `ReadOnly`. Démarre un `Set` procédure de propriété qui est utilisé pour stocker la valeur de la propriété.

- `End Set`

  Met fin à la `Set` procédure de propriété.

- `End Property`

  Termine la définition de cette propriété.

## <a name="remarks"></a>Notes

La `Property` instruction introduit la déclaration d’une propriété. Une propriété peut avoir un `Get` procédure (en lecture seule), un `Set` procédure (écriture seule), ou les deux (lecture-écriture). Vous pouvez omettre le `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

Vous pouvez utiliser `Property` uniquement au niveau de classe. Cela signifie que le *contexte de déclaration* pour une propriété doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Par défaut, les propriétés utilisent un accès public. Vous pouvez ajuster le niveau d’accès d’une propriété avec un modificateur d’accès sur le `Property` instruction et vous pouvez éventuellement ajuster une de ses procédures de propriété à un niveau d’accès plus restrictif.

Visual Basic passe un paramètre à la `Set` procédure pendant les assignations de propriété. Si vous ne fournissez pas un paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicit nommé `value`. Ce paramètre conserve la valeur à assigner à la propriété. Vous en général de stocker cette valeur dans une variable locale privée et renvoyez-le à chaque fois que le `Get` procédure est appelée.

## <a name="rules"></a>Règles

- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux. Si vous procédez ainsi, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Set` procédure `Private`, mais pas `Public`.

  Si vous définissez un `ReadOnly` ou `WriteOnly` propriété, la procédure de propriété unique (`Get` ou `Set`, respectivement) représente la propriété. Vous ne pouvez pas déclarer un niveau d’accès différent pour cette procédure, parce que qui risque de deux niveaux d’accès pour la propriété.

- **Type de retour.** La `Property` instruction peut déclarer le type de données de la valeur de retour. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface.

  Si vous ne spécifiez pas `returntype`, la propriété retourne `Object`.

- **Mise en œuvre.** Si cette propriété utilise la `Implements` mot clé, la classe de conteneur ou la structure doit avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction. Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit les `Property` (dans `definedname`) ne doit pas être le même que le nom de cette propriété (dans `name`).

## <a name="behavior"></a>Comportement

- **Retour d’une procédure de propriété.** Lorsque le `Get` ou `Set` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.

  Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété. Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez combiner `Exit Property` et `Return` instructions.

- **Valeur de retour.** Pour retourner une valeur à partir d’un `Get` procédure, vous pouvez affecter la valeur au nom de propriété ou l’inclure dans un `Return` instruction. L’exemple suivant affecte la valeur de retour au nom de propriété `quoteForTheDay` et utilise ensuite la `Exit Property` instruction à retourner.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  Si vous utilisez `Exit Property` sans assigner une valeur à `name`, le `Get` procédure retourne la valeur par défaut type de la propriété de données.

  Le `Return` instruction en même temps affecte le `Get` procédure retourner de valeur et termine la procédure. L’exemple suivant illustre cela.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Exemple

L’exemple suivant déclare une propriété dans une classe.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Voir aussi

- [Propriétés implémentées automatiquement](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
- [Liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Default](../../../visual-basic/language-reference/modifiers/default.md)
