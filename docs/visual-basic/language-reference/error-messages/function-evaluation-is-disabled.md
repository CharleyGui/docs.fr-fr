---
title: L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d004c89b742944622ce45e6a2be8d96116252745
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197567"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré
L’évaluation de fonction est désactivée, car une évaluation de fonction précédente a expiré. Pour réactiver l’évaluation de fonction, recommencez l’opération ou redémarrez le débogage.  
  
 Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre évaluation a dépassé le délai d’attente.  
  
 Les causes possibles de l’expiration d’un appel de procédure incluent une boucle infinie ou une *boucle*infinie. Pour plus d’informations, consultez [pour... Instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 La *récursivité*est un cas particulier de boucle infinie. Pour plus d’informations, consultez [procédures récursives](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID d’erreur :** BC30957  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Si possible, déterminez l’évaluation de la fonction précédente et la raison de l’expiration du délai d’attente. Dans le cas contraire, vous risquez de rencontrer cette erreur.  
  
2. Effectuez une nouvelle opération sur le débogueur, ou arrêtez et redémarrez le débogage.  
  
## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Naviguer dans le code avec le débogueur](/visualstudio/debugger/navigating-through-code-with-the-debugger)
