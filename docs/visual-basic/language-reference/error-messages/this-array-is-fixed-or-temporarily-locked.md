---
title: Ce tableau a une taille fixe ou est temporairement verrouillé
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 4a86460104b6c4d9d6791e60f6f377cec0030425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363031"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)
Cette erreur a les causes possibles suivantes :  
  
- Utilisation de `ReDim` pour modifier le nombre d’éléments d’un tableau de taille fixe.  
  
- Redimensionnement d’un tableau dynamique au niveau du module, dans lequel un élément a été passé comme argument à une procédure. Si un élément est passé, le tableau est verrouillé pour empêcher la désallocation de mémoire pour le paramètre de référence dans la procédure.  
  
- Tentative d’assignation d’une valeur à une `Variant` variable contenant un tableau, mais le `Variant` est actuellement verrouillé.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Rendez le tableau d’origine dynamique plutôt que fixe en le déclarant avec `ReDim` (si le tableau est déclaré dans une procédure) ou en le déclarant sans spécifier le nombre d’éléments (si le tableau est déclaré au niveau du module.  
  
2. Déterminez si vous devez vraiment passer l’élément, car il est visible dans toutes les procédures du module.  
  
3. Déterminez ce qui verrouille le `Variant` et résolvez-le.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux](../../programming-guide/language-features/arrays/index.md)
