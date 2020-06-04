---
title: Sub ou Function non défini
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 9eb13d943f9f1cffc984847f7339111e06f5aa6b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373925"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou Function non défini (Visual Basic)
`Sub`Ou `Function` doit être défini pour être appelé. Cette erreur peut avoir plusieurs causes :  
  
- Orthographe du nom de la procédure.  
  
- Tentative d’appel d’une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans la boîte de dialogue **références** .  
  
- Spécification d’une procédure qui n’est pas visible pour la procédure appelante.  
  
- Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) Windows ou d’une routine de ressource de code Macintosh qui ne se trouve pas dans la bibliothèque ou la ressource de code spécifiée.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que le nom de la procédure est correctement orthographié.  
  
2. Recherchez le nom du projet contenant la procédure que vous souhaitez appeler dans la boîte de dialogue **références** . S’il n’apparaît pas, cliquez sur le bouton **Parcourir** pour le Rechercher. Activez la case à cocher située à gauche du nom du projet, puis cliquez sur **OK**.  
  
3. Vérifiez le nom de la routine.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [Sub (instruction)](../statements/sub-statement.md)
- [Function (instruction)](../statements/function-statement.md)
