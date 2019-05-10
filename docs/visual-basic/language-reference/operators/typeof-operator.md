---
title: TypeOf, opérateur (Visual Basic)
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
ms.openlocfilehash: e5cb1ddc130a8b1913f30b0d20d27941005dd9d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063254"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf, opérateur (Visual Basic)
Vérifie si le type de résultat d’une expression exécution est de type compatible avec le type spécifié.
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Retourné. Valeur `Boolean`.  
  
 `objectexpression`  
 Obligatoire. Toute expression ayant pour résultat un type référence.  
  
 `typename`  
 Obligatoire. Tout nom de type de données.  
  
## <a name="remarks"></a>Notes  
 L'opérateur `TypeOf` détermine si le type d'exécution de `objectexpression` est compatible avec `typename`. La compatibilité dépend de la catégorie du type de `typename`. Le tableau suivant illustre la manière dont la compatibilité est déterminée.  
  
|Catégorie de type de `typename`|Critère de compatibilité|  
|---------------------------------|-----------------------------|  
|Classe|`objectexpression` est de type `typename` ou hérite de `typename`|  
|Structure|`objectexpression` est de type `typename`|  
|Interface|`objectexpression` implémente `typename` ou hérite d'une classe qui implémente `typename`|  
  
 Si le type de l'exécution de `objectexpression` satisfait le critère de compatibilité, `result` est `True`. Sinon, `result` est `False`.  Si `objectexpression` est null, alors `TypeOf`...`Is` retourne `False`, et ...`IsNot` retourne `True`.  
  
 `TypeOf` est toujours utilisé avec le mot clé `Is` pour construire une expression `TypeOf`...`Is`, ou avec le mot clé `IsNot` pour construire une expression `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des expressions `TypeOf`...`Is` pour tester la compatibilité du type de deux variables de référence d'objet avec différents types de données.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 La variable `refInteger` a un type au moment de l'exécution de `Integer`. Il est compatible avec `Integer` mais pas avec `Double`. La variable `refForm` a un type au moment de l'exécution de <xref:System.Windows.Forms.Form>. Il est compatible avec <xref:System.Windows.Forms.Form> car il s'agit de son type, avec <xref:System.Windows.Forms.Control> car <xref:System.Windows.Forms.Form> hérite de <xref:System.Windows.Forms.Control>, et avec <xref:System.ComponentModel.IComponent> car <xref:System.Windows.Forms.Form> hérite de <xref:System.ComponentModel.Component>, qui implémente <xref:System.ComponentModel.IComponent>. Toutefois, `refForm` n'est pas compatible avec <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Voir aussi

- [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
