---
title: "'#ElseIf' doit être précédé d'un '#If' ou '#ElseIf' correspondant"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 06af269508db6a2b258251272fdc18ef20eb1c0f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874449"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' doit être précédé d'un '#If' ou '#ElseIf' correspondant

`#ElseIf` est une directive de compilation conditionnelle. Une `#ElseIf` clause doit être précédée d’une `#If` clause ou correspondante `#ElseIf` .  
  
 **ID d’erreur :** BC30014  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez que le précédent `#If` ou `#ElseIf` le n’a pas été séparé de ce `#ElseIf` par un bloc de compilation conditionnelle intermédiaire ou qu’il a été placé de manière incorrecte `#End If` .  
  
2. Si le `#ElseIf` est précédé d’une `#Else` directive, supprimez `#Else` ou remplacez-le par un `#ElseIf` .  
  
3. Si tout le reste est en ordre, ajoutez une directive `#If` au début du bloc de compilation conditionnelle.  
  
## <a name="see-also"></a>Voir aussi

- [#If... Then... #Else directives](../directives/if-then-else-directives.md)
