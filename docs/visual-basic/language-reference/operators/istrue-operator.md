---
title: IsTrue, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370646"
---
# <a name="istrue-operator-visual-basic"></a>Opérateur IsTrue (Visual Basic)
Détermine si une expression est `True` .  
  
 Vous ne pouvez pas appeler `IsTrue` explicitement dans votre code, mais le compilateur Visual Basic peut l’utiliser pour générer du code à partir de `OrElse` clauses. Si vous définissez une classe ou une structure, puis que vous utilisez une variable de ce type dans une `OrElse` clause, vous devez définir `IsTrue` sur cette classe ou structure.  
  
 Le compilateur considère les `IsTrue` `IsFalse` opérateurs et comme une *paire correspondante*. Cela signifie que si vous définissez l’une d’entre elles, vous devez également définir l’autre.  
  
## <a name="compiler-use-of-istrue"></a>Utilisation de IsTrue par le compilateur  
 Lorsque vous avez défini une classe ou une structure, vous pouvez utiliser une variable de ce type dans `For` une `If` instruction,, `Else If` ou `While` , ou dans une `When` clause. Dans ce cas, le compilateur requiert un opérateur qui convertit votre type en `Boolean` valeur afin de pouvoir tester une condition. Il recherche un opérateur approprié dans l’ordre suivant :  
  
1. Opérateur de conversion étendue de votre classe ou structure en `Boolean` .  
  
2. Opérateur de conversion étendue de votre classe ou structure en `Boolean?` .  
  
3. `IsTrue`Opérateur sur votre classe ou structure.  
  
4. Conversion restrictive vers `Boolean?` qui n’implique pas de conversion de `Boolean` en `Boolean?` .  
  
5. Opérateur de conversion restrictive de votre classe ou structure en `Boolean` .  
  
 Si vous n’avez défini aucune conversion vers `Boolean` ou un `IsTrue` opérateur, le compilateur signale une erreur.  
  
> [!NOTE]
> L' `IsTrue` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit le plan d’une structure qui comprend des définitions pour les `IsFalse` `IsTrue` opérateurs et.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [IsFalse, opérateur](isfalse-operator.md)
- [Comment : définir un opérateur](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse, opérateur](orelse-operator.md)
