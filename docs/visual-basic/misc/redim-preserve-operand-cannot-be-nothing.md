---
title: L’opérande 'ReDim' ne peut pas être Nothing
ms.date: 07/20/2015
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
ms.openlocfilehash: 7dc57d328f04b8210adec3cb2bf2c2e29af66313
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358100"
---
# <a name="redim-preserve-operand-cannot-be-nothing"></a>L’opérande 'ReDim' ne peut pas être Nothing
Une instruction `ReDim` tente d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension, mais elle ne fournit pas de valeur valide pour son opérande.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Remplacez l’opérande `Preserve` par une valeur valide.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux en Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensions de tableau dans Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim (instruction)](../language-reference/statements/redim-statement.md)
- [Dim (instruction)](../language-reference/statements/dim-statement.md)
