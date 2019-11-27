---
title: '&amp;, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336057"
---
# <a name="amp-operator-visual-basic"></a>Opérateur de &amp; (Visual Basic)
Génère une concaténation de chaîne de deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute variable `String` ou `Object`.  
  
 `expression1`  
 Requis. Toute expression avec un type de données qui s’étend à `String`.  
  
 `expression2`  
 Requis. Toute expression avec un type de données qui s’étend à `String`.  
  
## <a name="remarks"></a>Notes  
 Si le type de données de `expression1` ou `expression2` n’est pas `String` mais s’élargit à `String`, il est converti en `String`. Si l’un des types de données ne s’étend pas à `String`, le compilateur génère une erreur.  
  
 Le type de données de `result` est `String`. Si l’une ou les deux expressions ont la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou si elles ont la valeur <xref:System.DBNull.Value?displayProperty=nameWithType>, elles sont traitées comme une chaîne avec la valeur «».  
  
> [!NOTE]
> L’opérateur `&` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Le caractère perluète (&) peut également être utilisé pour identifier des variables en tant que type `Long`. Pour plus d’informations, consultez [caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’opérateur `&` pour forcer la concaténation de chaînes. Le résultat est une valeur de chaîne représentant la concaténation des deux opérandes de chaîne.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [&=, opérateur](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Opérateurs de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs de concaténation dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
