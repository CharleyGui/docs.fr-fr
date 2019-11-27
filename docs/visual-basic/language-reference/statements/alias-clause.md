---
title: Alias (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: a7f67224c5d26816bdc1974dc4aa82d796c41284
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349149"
---
# <a name="alias-clause-visual-basic"></a>Alias, clause (Visual Basic)
Indique qu’une procédure externe a un autre nom dans sa DLL.  
  
## <a name="remarks"></a>Notes  
 Le mot clé `Alias` peut être utilisé dans ce contexte :  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 Dans l’exemple suivant, le mot clé `Alias` est utilisé pour fournir le nom de la fonction dans advapi32. dll, `GetUserNameA`, que `getUserName` est utilisé à la place de dans cet exemple. La fonction `getUserName` est appelée dans Sub `getUser`, qui affiche le nom de l’utilisateur actuel.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
