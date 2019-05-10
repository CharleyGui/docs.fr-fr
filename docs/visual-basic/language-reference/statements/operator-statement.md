---
title: Operator, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 4162f7cb5d8b89a1e5e8e7db429cf4e8dd9b700a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583594"
---
# <a name="operator-statement"></a>Operator Statement
Déclare le symbole d’opérateur, opérandes et le code qui définissent une procédure d’opérateur sur une classe ou structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>Composants  
 `attrlist`  
 Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Obligatoire. Indique que cette procédure d’opérateur a [Public](../../../visual-basic/language-reference/modifiers/public.md) accès.  
  
 `Overloads`  
 Facultatif. Consultez [surcharges](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Obligatoire. Indique que cette procédure d’opérateur est un [partagé](../../../visual-basic/language-reference/modifiers/shared.md) procédure.  
  
 `Shadows`  
 Facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Narrowing`. Indique que cette procédure d’opérateur définit un [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion. Consultez « Conversions étendues et restrictives » sur cette page d’aide.  
  
 `Narrowing`  
 Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Widening`. Indique que cette procédure d’opérateur définit un [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion. Consultez « Conversions étendues et restrictives » sur cette page d’aide.  
  
 `operatorsymbol`  
 Obligatoire. Le symbole ou l’identificateur de l’opérateur qui définit cette procédure d’opérateur.  
  
 `operand1`  
 Obligatoire. Le nom et le type de l’opérande unique d’un opérateur unaire (y compris un opérateur de conversion) ou de l’opérande gauche d’un opérateur binaire.  
  
 `operand2`  
 Requis pour les opérateurs binaires. Le nom et le type de l’opérande de droite d’un opérateur binaire.  
  
 `operand1` et `operand2` ont la syntaxe et les éléments suivants :  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Élément|Description|  
|----------|-----------------|  
|`ByVal`|Facultatif, mais le mécanisme de passage doit être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Obligatoire. Nom de la variable représentant cet opérande. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Facultatif, sauf si `Option Strict` est `On`. Type de données de cet opérande.|  
  
 `type`  
 Facultatif, sauf si `Option Strict` est `On`. Type de données de la valeur de la procédure d’opérateur retourne.  
  
 `statements`  
 Facultatif. Bloc d’instructions qui s’exécute la procédure d’opérateur.  
  
 `returnvalue`  
 Obligatoire. La valeur que la procédure d’opérateur retourne au code appelant.  
  
 `End` `Operator`  
 Obligatoire. Met fin à la définition de cette procédure d’opérateur.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser `Operator` uniquement dans une classe ou structure. Cela signifie que le *contexte de déclaration* pour un opérateur ne peut pas être un fichier source, espace de noms, module, interface, procédure ou bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Tous les opérateurs doivent être `Public Shared`. Vous ne pouvez pas spécifier `ByRef`, `Optional`, ou `ParamArray` pour des opérandes.  
  
 Vous ne pouvez pas utiliser le symbole d’opérateur ou l’identificateur pour contenir une valeur de retour. Vous devez utiliser le `Return` instruction et elle doit spécifier une valeur. Un nombre quelconque de `Return` instructions peuvent apparaître n’importe où dans la procédure.  
  
 Définition d’un opérateur de cette façon est appelée *surcharge d’opérateur*, que vous utilisiez ou non le `Overloads` mot clé. Le tableau suivant présente les opérateurs que vous pouvez définir.  
  
|Type|Opérateurs|  
|----------|---------------|  
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversion (unaire)|`CType`|  
  
 Notez que le `=` opérateur dans la liste binaire est l’opérateur de comparaison, pas l’opérateur d’assignation.  
  
 Lorsque vous définissez `CType`, vous devez spécifier soit `Widening` ou `Narrowing`.  
  
## <a name="matched-pairs"></a>Paires correspondantes  
 Vous devez définir certains opérateurs comme des paires correspondantes. Si vous définissez des opérateurs de cette paire, vous devez définir l’autre. Les paires correspondantes sont les suivantes :  
  
- `=` et `<>`  
  
- `>` et `<`  
  
- `>=` et `<=`  
  
- `IsTrue` et `IsFalse`  
  
## <a name="data-type-restrictions"></a>Restrictions de Type de données  
 Chaque opérateur que vous définissez doit impliquer la classe ou la structure sur laquelle vous le définissez. Cela signifie que la classe ou structure doit apparaître en tant que le type de données des éléments suivants :  
  
- L’opérande d’un opérateur unaire.  
  
- Au moins un des opérandes d’un opérateur binaire.  
  
- L’opérande ou le type de retour d’un opérateur de conversion.  
  
 Certains opérateurs ont des données supplémentaires de type des restrictions, comme suit :  
  
- Si vous définissez la `IsTrue` et `IsFalse` opérateurs, ils doivent retourner le `Boolean` type.  
  
- Si vous définissez la `<<` et `>>` opérateurs, ils doivent tous deux spécifient le `Integer` type pour le `operandtype` de `operand2`.  
  
 Le type de retour ne doit pas forcément correspondre au type de des opérandes. Par exemple, un opérateur de comparaison tel que `=` ou `<>` peut retourner `Boolean` même si aucun des opérandes sont `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Opérateurs de bits et opérateurs logiques  
 Le `And`, `Or`, `Not`, et `Xor` opérateurs peuvent effectuer des opérations logiques ou au niveau du bit en Visual Basic. Toutefois, si vous définissez un de ces opérateurs sur une classe ou structure, vous pouvez définir uniquement son opération au niveau du bit.  
  
 Vous ne pouvez pas définir le `AndAlso` opérateur directement avec un `Operator` instruction. Toutefois, vous pouvez utiliser `AndAlso` si vous avez rempli les conditions suivantes :  
  
- Vous avez défini `And` sur les mêmes types d’opérande à utiliser pour `AndAlso`.  
  
- Votre définition de `And` retourne le même type que la classe ou la structure sur lequel vous l’avez défini.  
  
- Vous avez défini le `IsFalse` opérateur sur la classe ou la structure sur laquelle vous avez défini `And`.  
  
 De même, vous pouvez utiliser `OrElse` si vous avez défini `Or` sur les mêmes opérandes, avec le type de retour de la classe ou structure et que vous avez défini `IsTrue` sur la classe ou structure.  
  
## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions  
 Un *conversion étendue* réussit toujours au moment de l’exécution, pendant un *conversion restrictive* peut échouer au moment de l’exécution. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Si vous déclarez une procédure de conversion pour être `Widening`, votre code de procédure ne doit pas générer d’échecs. Par conséquent :  
  
- Elle doit toujours retourner une valeur valide de type `type`.  
  
- Il doit gérer toutes les exceptions possibles et autres conditions d’erreur.  
  
- Il doit gérer les erreurs retournées par toutes les procédures qu’elle appelle.  
  
 S’il est possible qu’une procédure de conversion peut échouer, ou qu’elle peut entraîner une exception non gérée, vous devez déclarer qu’elle soit `Narrowing`.  
  
## <a name="example"></a>Exemple  
 Le code suivant exemple utilise le `Operator` instruction pour définir le contour d’une structure qui inclut des procédures d’opérateur pour le `And`, `Or`, `IsFalse`, et `IsTrue` opérateurs. `And` et `Or` chacun prennent deux opérandes de type `abc` et type de retour `abc`. `IsFalse` et `IsTrue` chacune accepter un opérande unique de type `abc` et retourner `Boolean`. Ces définitions permettent au code appelant d’utiliser `And`, `AndAlso`, `Or`, et `OrElse` avec opérandes de type `abc`.  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a>Voir aussi

- [IsFalse (opérateur)](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [IsTrue (opérateur)](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Guide pratique pour Définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Guide pratique pour Définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Guide pratique pour Appeler une procédure d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Guide pratique pour Utiliser une classe qui définit des opérateurs](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
