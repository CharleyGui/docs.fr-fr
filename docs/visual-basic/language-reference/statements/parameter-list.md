---
title: Liste de paramètres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582182"
---
# <a name="parameter-list-visual-basic"></a>Liste de paramètres (Visual Basic)

Spécifie les paramètres qu’une procédure attend quand elle est appelée. Plusieurs paramètres sont séparés par des virgules. Voici la syntaxe d’un paramètre.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Composants

`attributelist`  
Optionnel. Liste des attributs qui s’appliquent à ce paramètre. Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus (« `<` » et « `>` »).

`Optional`  
Optionnel. Spécifie que ce paramètre n’est pas requis lorsque la procédure est appelée.

`ByVal`  
Optionnel. Spécifie que la procédure ne peut pas remplacer ou réassigner l’élément de variable sous-jacent à l’argument correspondant dans le code appelant.

`ByRef`  
Optionnel. Spécifie que la procédure peut modifier l’élément de variable sous-jacent dans le code appelant de la même façon que le code appelant lui-même.

`ParamArray`  
Optionnel. Spécifie que le dernier paramètre de la liste de paramètres est un tableau facultatif d’éléments du type de données spécifié. Cela permet au code appelant de passer un nombre arbitraire d’arguments à la procédure.

`parametername`  
Requis. Nom de la variable locale représentant le paramètre.

`parametertype`  
Obligatoire si `Option Strict` est `On`. Type de données de la variable locale représentant le paramètre.

`defaultvalue`  
Requis pour les paramètres de `Optional`. Toute expression constante ou constante qui prend la valeur du type de données du paramètre. Si le type est `Object`, ou une classe, une interface, un tableau ou une structure, la valeur par défaut ne peut être `Nothing`.

## <a name="remarks"></a>Notes

Les paramètres sont placés entre parenthèses et séparés par des virgules. Un paramètre peut être déclaré avec n’importe quel type de données. Si vous ne spécifiez pas `parametertype`, la valeur par défaut est `Object`.

Lorsque le code appelant appelle la procédure, il passe un *argument* à chaque paramètre requis. Pour plus d’informations, consultez [différences entre les paramètres et les arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

L’argument que le code appelant passe à chaque paramètre est un pointeur vers un élément sous-jacent dans le code appelant. Si cet élément n’est pas une *variable* (une constante, un littéral, une énumération ou une expression), il est impossible pour un code de le modifier. S’il s’agit d’un élément *variable* (une variable déclarée, un champ, une propriété, un élément de tableau ou un élément de structure), le code appelant peut le modifier. Pour plus d’informations, consultez [différences entre les arguments modifiables et non modifiables](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Si un élément variable est passé `ByRef`, la procédure peut également le modifier. Pour plus d’informations, consultez [différences entre le passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Règles

- **Parenthèses.** Si vous spécifiez une liste de paramètres, vous devez la placer entre parenthèses. S’il n’y a aucun paramètre, vous pouvez toujours utiliser des parenthèses englobant une liste vide. Cela améliore la lisibilité de votre code en clarifiant que l’élément est une procédure.

- **Paramètres facultatifs.** Si vous utilisez le modificateur `Optional` sur un paramètre, tous les paramètres suivants de la liste doivent également être facultatifs et être déclarés à l’aide du modificateur `Optional`.

     Chaque déclaration de paramètre facultative doit fournir la clause `defaultvalue`.

     Pour plus d’informations, consultez [paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Tableaux de paramètres.** Vous devez spécifier `ByVal` pour un paramètre `ParamArray`.

     Vous ne pouvez pas utiliser à la fois `Optional` et `ParamArray` dans la même liste de paramètres.

     Pour plus d’informations, consultez [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Mécanisme de passage.** Le mécanisme par défaut pour chaque argument est `ByVal`, ce qui signifie que la procédure ne peut pas modifier l’élément de variable sous-jacent. Toutefois, si l’élément est un type référence, la procédure peut modifier le contenu ou les membres de l’objet sous-jacent, même s’il ne peut pas remplacer ou réassigner l’objet lui-même.

- **Noms de paramètres.** Si le type de données du paramètre est un tableau, suivez `parametername` immédiatement par des parenthèses. Pour plus d’informations sur les noms de paramètres, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre une procédure `Function` qui définit deux paramètres.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
