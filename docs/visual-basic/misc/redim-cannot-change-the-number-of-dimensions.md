---
title: "'ReDim' ne peut pas changer le nombre de dimensions"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b2404927c2faf30d1d058d2163fd5d67e1a52e1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358165"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' ne peut pas changer le nombre de dimensions
Une opération tente d’utiliser l’instruction `ReDim` pour modifier le rang (nombre de dimensions) d’un tableau. L’instruction`ReDim` peut modifier la taille d’une ou plusieurs dimensions d’un tableau qui a déjà été déclaré en bonne et due forme, mais elle ne peut pas modifier le rang d’un tableau.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous de bien vouloir modifier le rang du tableau et non la taille de ses dimensions et, si possible, utilisez `Dim` pour déclarer un nouveau tableau avec le rang souhaité.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux en Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensions de tableau dans Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim (instruction)](../language-reference/statements/redim-statement.md)
- [Dim (instruction)](../language-reference/statements/dim-statement.md)
