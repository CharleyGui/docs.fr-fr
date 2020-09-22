---
title: Alias (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 77d4685f242864842e5a84b3a3de3ba1793e9aa4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866679"
---
# <a name="alias-clause-visual-basic"></a>Alias, clause (Visual Basic)

Indique qu’une procédure externe a un autre nom dans sa DLL.  
  
## <a name="remarks"></a>Notes  

 Le `Alias` mot clé peut être utilisé dans ce contexte :  
  
 [Declare Statement](declare-statement.md)  
  
 Dans l’exemple suivant, le `Alias` mot clé est utilisé pour fournir le nom de la fonction dans advapi32.dll, `GetUserNameA` , qui `getUserName` est utilisé à la place de dans cet exemple. La fonction `getUserName` est appelée dans Sub `getUser` , qui affiche le nom de l’utilisateur actuel.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../keywords/index.md)
