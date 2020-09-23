---
title: "'ReDim' ne peut pas changer le nombre de dimensions"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 8d80af7682f27b403e0f463fdbebbcac71f18b01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077369"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' ne peut pas changer le nombre de dimensions

Une opération tente d’utiliser l’instruction `ReDim` pour modifier le rang (nombre de dimensions) d’un tableau. L’instruction`ReDim` peut modifier la taille d’une ou plusieurs dimensions d’un tableau qui a déjà été déclaré en bonne et due forme, mais elle ne peut pas modifier le rang d’un tableau.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous de bien vouloir modifier le rang du tableau et non la taille de ses dimensions et, si possible, utilisez `Dim` pour déclarer un nouveau tableau avec le rang souhaité.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux dans Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensions de tableau dans Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim (instruction)](../language-reference/statements/redim-statement.md)
- [Dim (instruction)](../language-reference/statements/dim-statement.md)
