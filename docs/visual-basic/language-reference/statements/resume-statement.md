---
title: Resume, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957688"
---
# <a name="resume-statement"></a>Resume, instruction
Reprend l’exécution après la fin d’une routine de gestion des erreurs.  
  
 Nous vous suggérons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d' `On Error` utiliser `Resume` la gestion non structurée des exceptions et les instructions et. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Composants  
 `Resume`  
 Requis. Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui a provoqué l’erreur. Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend au niveau de l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs.  
  
 `Next`  
 facultatif. Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a provoqué l’erreur. Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a appelé en dehors de la procédure qui contient la routine `On Error Resume Next` de gestion des erreurs (ou l’instruction).  
  
 `line`  
 facultatif. L’exécution reprend à la ligne spécifiée dans l’argument `line` requis. L' `line` argument est une étiquette de ligne ou un numéro de ligne et doit être dans la même procédure que le gestionnaire d’erreurs.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Nous vous recommandons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser `On Error` la `Resume` gestion des exceptions non structurées et les instructions et. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Si vous utilisez une `Resume` instruction n’importe où dans une routine de gestion des erreurs, une erreur se produit.  
  
 L' `Resume` instruction ne peut pas être utilisée dans une procédure qui `Try...Catch...Finally` contient une instruction.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l' `Resume` instruction pour terminer la gestion des erreurs dans une procédure, puis reprendre l’exécution avec l’instruction qui a provoqué l’erreur. L’erreur numéro 55 est générée pour illustrer l' `Resume` utilisation de l’instruction.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Chargeur** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error (instruction)](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
