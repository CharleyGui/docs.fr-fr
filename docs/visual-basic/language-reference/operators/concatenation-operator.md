---
title: '&amp;(Visual Basic), opérateur'
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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968357"
---
# <a name="amp-operator-visual-basic"></a>&amp;(Visual Basic), opérateur
Génère une concaténation de chaîne de deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. N' `String` importe `Object` quelle variable ou.  
  
 `expression1`  
 Requis. Toute expression avec un type de données qui s’étend `String`à.  
  
 `expression2`  
 Requis. Toute expression avec un type de données qui s’étend `String`à.  
  
## <a name="remarks"></a>Notes  
 Si le type de données `expression1` de `expression2` ou n' `String` est pas mais s' `String`élargit à, il `String`est converti en. Si l’un des types de données ne s’étend `String`pas à, le compilateur génère une erreur.  
  
 Le type de données `result` de `String`est. Si une ou les deux expressions ont la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou ont la <xref:System.DBNull.Value?displayProperty=nameWithType>valeur, elles sont traitées comme une chaîne avec la valeur «».  
  
> [!NOTE]
> L' `&` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Le caractère perluète (&) peut également être utilisé pour identifier des variables en `Long`tant que type. Pour plus d’informations, consultez [caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemples  
 Cet exemple utilise l' `&` opérateur pour forcer la concaténation de chaînes. Le résultat est une valeur de chaîne représentant la concaténation des deux opérandes de chaîne.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [&= (opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs de concaténation dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
