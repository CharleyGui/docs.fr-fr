---
title: Alias (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408469"
---
# <a name="alias-clause-visual-basic"></a>Alias, clause (Visual Basic)
Indique qu’une procédure externe a un autre nom dans sa DLL.  
  
## <a name="remarks"></a>Notes  
 Le `Alias` mot clé peut être utilisé dans ce contexte :  
  
 [Declare Statement](declare-statement.md)  
  
 Dans l’exemple suivant, le `Alias` mot clé est utilisé pour fournir le nom de la fonction dans advapi32. dll, `GetUserNameA` , qui `getUserName` est utilisé à la place de dans cet exemple. La fonction `getUserName` est appelée dans Sub `getUser` , qui affiche le nom de l’utilisateur actuel.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../keywords/index.md)
