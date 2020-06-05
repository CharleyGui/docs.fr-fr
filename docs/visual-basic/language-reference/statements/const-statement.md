---
title: Const (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3b05d4067ef99e03df07d2c316c982051180d961
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382105"
---
# <a name="const-statement-visual-basic"></a>Const, instruction (Visual Basic)

Déclare et définit une ou plusieurs constantes.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a>Éléments

`attributelist`  
Facultatif. Liste des attributs qui s’appliquent à toutes les constantes déclarées dans cette instruction. Consultez la [liste des attributs](attribute-list.md) entre crochets pointus (« `<` » et «» `>` ).

`accessmodifier`  
Facultatif. Utilisez cette valeur pour spécifier le code qui peut accéder à ces constantes. Peut être [public](../modifiers/public.md), [protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md)ou [Private protected](../modifiers/private-protected.md).

`Shadows`  
Facultatif. À utiliser pour redéclarer et masquer un élément de programmation dans une classe de base. Consultez [Shadows](../modifiers/shadows.md).

`constantlist`  
Obligatoire. Liste des constantes déclarées dans cette instruction.

`constant` `[ ,` `constant` `... ]`

Chaque `constant` emploie la syntaxe et les éléments suivants :

`constantname` `[ As` `datatype` `] =` `initializer`

|Élément|Description|
|----------|-----------------|
|`constantname`|Obligatoire. Nom de la constante. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`datatype`|Obligatoire si `Option Strict` est `On` . Type de données de la constante.|
|`initializer`|Obligatoire. Expression évaluée au moment de la compilation et assignée à la constante.|

## <a name="remarks"></a>Notes

Si vous avez une valeur qui ne change jamais dans votre application, vous pouvez définir une constante nommée et l’utiliser à la place d’une valeur littérale. Un nom est plus facile à mémoriser qu’une valeur. Vous pouvez définir la constante une seule fois et l’utiliser à de nombreux emplacements de votre code. Si, dans une version ultérieure, vous devez redéfinir la valeur, l' `Const` instruction est le seul endroit où vous devez apporter une modification.

Vous pouvez utiliser `Const` uniquement au niveau du module ou de la procédure. Cela signifie que le *contexte de déclaration* pour une variable doit être une classe, une structure, un module, une procédure ou un bloc, et ne peut pas être un fichier source, un espace de noms ou une interface. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Les constantes locales (à l’intérieur d’une procédure) sont par défaut accessibles au public et vous ne pouvez pas utiliser de modificateurs d’accès. Les constantes de membre de classe et de module (en dehors de toute procédure) sont par défaut en accès privé, et les constantes de membre de structure ont par défaut un accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Une constante déclarée au niveau du module, en dehors de toute procédure, est une *constante membre*; Il est membre de la classe, de la structure ou du module qui le déclare.

  Une constante déclarée au niveau de la procédure est une *constante locale*; Il est local à la procédure ou au bloc qui le déclare.

- **Attributs.** Vous pouvez appliquer des attributs uniquement aux constantes membres, pas aux constantes locales. Un attribut fournit des informations aux métadonnées de l’assembly, ce qui n’est pas significatif pour le stockage temporaire comme les constantes locales.

- **Modificateurs.** Par défaut, toutes les constantes sont `Shared` , `Static` et `ReadOnly` . Vous ne pouvez pas utiliser l’un de ces mots clés lors de la déclaration d’une constante.

  Au niveau de la procédure, vous ne pouvez pas utiliser `Shadows` ou n’importe quel modificateur d’accès pour déclarer des constantes locales.

- **Constantes multiples.** Vous pouvez déclarer plusieurs constantes dans la même instruction de déclaration, en spécifiant la `constantname` partie de chacune d’elles. Les constantes multiples sont séparées par des virgules.

## <a name="data-type-rules"></a>Règles de type de données

- **Types de données.** L' `Const` instruction peut déclarer le type de données d’une variable. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération.

- **Type par défaut.** Si vous ne spécifiez pas `datatype` , la constante prend le type de données de `initializer` . Si vous spécifiez `datatype` `initializer` à la fois et, le type de données de `initializer` doit être convertible en `datatype` . Si ni `datatype` ni `initializer` n’est présent, le type de données prend par défaut la valeur `Object` .

- **Types différents.** Vous pouvez spécifier des types de données différents pour des constantes différentes à l’aide d’une `As` clause distincte pour chaque variable que vous déclarez. Toutefois, vous ne pouvez pas déclarer plusieurs constantes pour qu’elles soient du même type à l’aide d’une `As` clause commune.

- **D’initialisation.** Vous devez initialiser la valeur de chaque constante dans `constantlist` . Vous utilisez `initializer` pour fournir une expression à assigner à la constante. L’expression peut être n’importe quelle combinaison de littéraux, d’autres constantes déjà définies et de membres d’énumération qui sont déjà définis. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner de tels éléments.

  Vous ne pouvez pas utiliser de variables ou de fonctions dans `initializer` . Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort` . Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou un `Char` argument, car cela peut être évalué au moment de la compilation.

## <a name="behavior"></a>Comportement

- **Étendue.** Les constantes locales sont accessibles uniquement à partir de leur procédure ou de leur bloc. Les constantes membres sont accessibles depuis n’importe où dans leur classe, structure ou module.

- **Bénéfice.** Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une constante membre avec le nom de la classe, de la structure ou du module. Le code en dehors d’une procédure ou d’un bloc ne peut pas faire référence à des constantes locales au sein de cette procédure ou de ce bloc.

## <a name="example"></a>Exemple

L’exemple suivant utilise l' `Const` instruction pour déclarer des constantes à utiliser à la place de valeurs littérales.

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a>Exemple

Si vous définissez une constante avec le type `Object` de données, le compilateur Visual Basic lui donne le type de `initializer` , au lieu de `Object` . Dans l’exemple suivant, la constante `naturalLogBase` a le type au moment de l’exécution `Decimal` .

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

L’exemple précédent utilise la <xref:System.Type.ToString%2A> méthode sur l' <xref:System.Type> objet retourné par l' [opérateur GetType](../operators/gettype-operator.md), car <xref:System.Type> ne peut pas être converti en `String` à l’aide de `CStr` .

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum (instruction)](enum-statement.md)
- [#Const directive](../directives/const-directive.md)
- [Dim (instruction)](dim-statement.md)
- [ReDim (instruction)](redim-statement.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Constantes et énumérations](../../programming-guide/language-features/constants-enums/index.md)
- [Constantes et énumérations](../constants-and-enumerations.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
