---
title: Opérateur IsFalse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917157"
---
# <a name="isfalse-operator-visual-basic"></a>Opérateur IsFalse (Visual Basic)
Détermine si une expression est `False`.  
  
 Vous ne pouvez `IsFalse` pas appeler explicitement dans votre code, mais le compilateur Visual Basic peut l’utiliser pour générer `AndAlso` du code à partir de clauses. Si vous définissez une classe ou une structure, puis que vous utilisez une variable de ce `AndAlso` type dans une clause, `IsFalse` vous devez définir sur cette classe ou structure.  
  
 Le compilateur considère les `IsFalse` opérateurs `IsTrue` et comme une *paire correspondante*. Cela signifie que si vous définissez l’une d’entre elles, vous devez également définir l’autre.  
  
> [!NOTE]
> L' `IsFalse` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemples  
 L’exemple de code suivant définit le plan d’une structure qui comprend des définitions `IsFalse` pour `IsTrue` les opérateurs et.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [IsTrue (opérateur)](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Guide pratique : Définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso (opérateur)](../../../visual-basic/language-reference/operators/andalso-operator.md)
