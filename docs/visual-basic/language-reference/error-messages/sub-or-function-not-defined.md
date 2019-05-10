---
title: Sub ou Function non défini (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 3a56d5596c79900bb5818a6ed7f8736859b5ea15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593198"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou Function non défini (Visual Basic)
Un `Sub` ou `Function` doit être défini pour pouvoir être appelés. Cette erreur peut avoir plusieurs causes :  
  
- Faute d’orthographe dans le nom de la procédure.  
  
- Essayez d’appeler une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans le **références** boîte de dialogue.  
  
- Spécification d’une procédure qui n’est pas visible à la procédure appelante.  
  
- Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que le nom de la procédure est correctement orthographié.  
  
2. Rechercher le nom du projet contenant la procédure que vous souhaitez appeler le **références** boîte de dialogue. Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton pour le rechercher. Cochez la case située à gauche du nom du projet, puis cliquez sur **OK**.  
  
3. Vérifiez le nom de la routine.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
