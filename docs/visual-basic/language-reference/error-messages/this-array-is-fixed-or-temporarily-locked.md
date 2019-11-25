---
title: Ce tableau a une taille fixe ou est temporairement verrouillé
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350788"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)
This error has the following possible causes:  
  
- Using `ReDim` to change the number of elements of a fixed-size array.  
  
- Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure. If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.  
  
- Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.  
  
2. Determine whether you really need to pass the element, since it is visible within all procedures in the module.  
  
3. Determine what is locking the `Variant` and remedy it.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
