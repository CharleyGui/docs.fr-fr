---
title: TypeOf, opérateur
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350889"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf, opérateur (Visual Basic)
Vérifie si le type d’exécution du résultat d’une expression est compatible avec le type spécifié.
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Retourné. Valeur `Boolean`.  
  
 `objectexpression`  
 Requis. Toute expression ayant pour résultat un type référence.  
  
 `typename`  
 Requis. Tout nom de type de données.  
  
## <a name="remarks"></a>Notes  
 L'opérateur `TypeOf` détermine si le type d'exécution de `objectexpression` est compatible avec `typename`. La compatibilité dépend de la catégorie du type de `typename`. Le tableau suivant illustre la manière dont la compatibilité est déterminée.  
  
|Catégorie de type de `typename`|Critère de compatibilité|  
|---------------------------------|-----------------------------|  
|Class|`objectexpression` est de type `typename` ou hérite de `typename`|  
|Structure|`objectexpression` est de type `typename`|  
|Interface|`objectexpression` implémente `typename` ou hérite d’une classe qui implémente `typename`|  
  
 Si le type de l'exécution de `objectexpression` satisfait le critère de compatibilité, `result` est `True`. Sinon, `result` est `False`.  Si `objectexpression` est null, alors `TypeOf`...`Is` retourne `False`, et ...`IsNot` retourne `True`.  
  
 `TypeOf` est toujours utilisé avec le mot clé `Is` pour construire une expression `TypeOf`...`Is` ou avec le mot clé `IsNot` pour construire une expression `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des expressions `TypeOf`...`Is` pour tester la compatibilité du type de deux variables de référence d'objet avec différents types de données.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 La variable `refInteger` a un type au moment de l'exécution de `Integer`. Il est compatible avec `Integer` mais pas avec `Double`. La variable `refForm` a un type au moment de l'exécution de <xref:System.Windows.Forms.Form>. Il est compatible avec <xref:System.Windows.Forms.Form> car il s'agit de son type, avec <xref:System.Windows.Forms.Control> car <xref:System.Windows.Forms.Form> hérite de <xref:System.Windows.Forms.Control>, et avec <xref:System.ComponentModel.IComponent> car <xref:System.Windows.Forms.Form> hérite de <xref:System.ComponentModel.Component>, qui implémente <xref:System.ComponentModel.IComponent>. Toutefois, `refForm` n'est pas compatible avec <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Voir aussi

- [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Opérateurs de comparaison dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
