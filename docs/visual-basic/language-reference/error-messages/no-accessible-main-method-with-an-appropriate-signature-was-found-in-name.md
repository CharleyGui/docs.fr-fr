---
title: Aucune méthode 'Main' accessible avec une signature appropriée n'a été trouvée dans '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6958e778701066760aa74e3b4d566800b7527b76
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871480"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Aucune méthode 'Main' accessible avec une signature appropriée n'a été trouvée dans '\<name>'

Les applications en ligne de commande doivent avoir un `Sub Main` défini. `Main` doit être déclaré comme `Public Shared` s’il est défini dans une classe, ou comme `Public` s’il est défini dans un module.  
  
 **ID d’erreur :** BC30737  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Définissez une `Public Sub Main` procédure pour votre projet. Déclarez-le comme `Shared` If et uniquement si vous le définissez à l’intérieur d’une classe.  
  
## <a name="see-also"></a>Voir aussi

- [Structure d'un programme Visual Basic](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
