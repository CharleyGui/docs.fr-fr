---
title: New, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955876"
---
# <a name="new-operator-visual-basic"></a>New, opérateur (Visual Basic)
Introduit une `New` clause pour créer une nouvelle instance d’objet, spécifie une contrainte de constructeur sur un paramètre de type `Sub` ou identifie une procédure comme un constructeur de classe.  
  
## <a name="remarks"></a>Notes  
 Dans une déclaration ou une instruction d’assignation `New` , une clause doit spécifier une classe définie à partir de laquelle l’instance peut être créée. Cela signifie que la classe doit exposer un ou plusieurs constructeurs auxquels le code appelant peut accéder.  
  
 Vous pouvez utiliser une `New` clause dans une instruction de déclaration ou une instruction d’assignation. Lorsque l’instruction s’exécute, elle appelle le constructeur approprié de la classe spécifiée, en passant tous les arguments que vous avez fournis. L’exemple suivant illustre cela en créant des instances d' `Customer` une classe qui a deux constructeurs, un qui ne prend aucun paramètre et un qui accepte un paramètre de chaîne.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Étant donné que les tableaux sont `New` des classes, peut créer une nouvelle instance de tableau, comme indiqué dans les exemples suivants.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Le Common Language Runtime (CLR) lève une <xref:System.OutOfMemoryException> erreur si la mémoire est insuffisante pour créer la nouvelle instance.  
  
> [!NOTE]
> Le `New` mot clé est également utilisé dans les listes de paramètres de type pour spécifier que le type fourni doit exposer un constructeur sans paramètre accessible. Pour plus d’informations sur les paramètres de type et les contraintes, consultez [type list](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Pour créer une procédure constructeur pour une classe, définissez le nom d’une `Sub` procédure sur le `New` mot clé. Pour plus d’informations, [consultez durée de vie d’un objet: Comment les objets sont créés et](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)détruits.  
  
 Le mot clé `New` peut être utilisé dans les contextes suivants :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.OutOfMemoryException>
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Durée de vie d’un objet: Comment les objets sont créés et détruits](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
