---
title: Resume, instruction
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
ms.openlocfilehash: db9d47798d087d60f4318b06fe3291fb895e6618
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871866"
---
# <a name="resume-statement"></a>Resume, instruction

Reprend l’exécution après la fin d’une routine de gestion des erreurs.  
  
 Nous vous suggérons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser la gestion non structurée des exceptions et les `On Error` `Resume` instructions et. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Éléments  

 `Resume`  
 Obligatoire. Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui a provoqué l’erreur. Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend au niveau de l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs.  
  
 `Next`  
 Optionnel. Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a provoqué l’erreur. Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs (ou l' `On Error Resume Next` instruction).  
  
 `line`  
 Optionnel. L’exécution reprend à la ligne spécifiée dans l' `line` argument requis. L' `line` argument est une étiquette de ligne ou un numéro de ligne et doit être dans la même procédure que le gestionnaire d’erreurs.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Nous vous recommandons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser la gestion des exceptions non structurées et les `On Error` `Resume` instructions et. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](try-catch-finally-statement.md).  
  
 Si vous utilisez une `Resume` instruction n’importe où dans une routine de gestion des erreurs, une erreur se produit.  
  
 L' `Resume` instruction ne peut pas être utilisée dans une procédure qui contient une `Try...Catch...Finally` instruction.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise l' `Resume` instruction pour terminer la gestion des erreurs dans une procédure, puis reprendre l’exécution avec l’instruction qui a provoqué l’erreur. L’erreur numéro 55 est générée pour illustrer l’utilisation de l' `Resume` instruction.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Spécifications  

 **Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Assembly :** Visual Basic la bibliothèque Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
- [Error, instruction](error-statement.md)
- [On Error (instruction)](on-error-statement.md)
