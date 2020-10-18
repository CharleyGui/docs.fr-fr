---
title: Aucune méthode 'Main' accessible avec une signature appropriée n'a été trouvée dans '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: e1f95484a153bdcac9543508b7f2708dc6b7d942
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160039"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>BC30737 : aucune méthode’main’accessible avec une signature appropriée n’a été trouvée dans' \<name> '

Les applications en ligne de commande doivent avoir un `Sub Main` défini. `Main` doit être déclaré comme `Public Shared` s’il est défini dans une classe, ou comme `Public` s’il est défini dans un module.

 **ID d’erreur :** BC30737

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Définissez une `Public Sub Main` procédure pour votre projet. Déclarez-le comme `Shared` If et uniquement si vous le définissez à l’intérieur d’une classe.

## <a name="see-also"></a>Voir aussi

- [Structure d'un programme Visual Basic](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
