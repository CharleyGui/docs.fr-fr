---
title: IsFalse, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 7c5ad5fa0b72370eeb19fbaced88807570467552
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370672"
---
# <a name="isfalse-operator-visual-basic"></a>Opérateur IsFalse (Visual Basic)
Détermine si une expression est `False` .  
  
 Vous ne pouvez pas appeler `IsFalse` explicitement dans votre code, mais le compilateur Visual Basic peut l’utiliser pour générer du code à partir de `AndAlso` clauses. Si vous définissez une classe ou une structure, puis que vous utilisez une variable de ce type dans une `AndAlso` clause, vous devez définir `IsFalse` sur cette classe ou structure.  
  
 Le compilateur considère les `IsFalse` `IsTrue` opérateurs et comme une *paire correspondante*. Cela signifie que si vous définissez l’une d’entre elles, vous devez également définir l’autre.  
  
> [!NOTE]
> L' `IsFalse` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit le plan d’une structure qui comprend des définitions pour les `IsFalse` `IsTrue` opérateurs et.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [IsTrue, opérateur](istrue-operator.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso, opérateur](andalso-operator.md)
