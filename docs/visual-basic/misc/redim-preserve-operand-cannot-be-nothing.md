---
title: L’opérande 'ReDim' ne peut pas être Nothing
ms.date: 07/20/2015
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
ms.openlocfilehash: 274b616387d214f32dd9cf05eaa17eb97898ffa4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077343"
---
# <a name="redim-preserve-operand-cannot-be-nothing"></a>L’opérande 'ReDim' ne peut pas être Nothing

Une instruction `ReDim` tente d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension, mais elle ne fournit pas de valeur valide pour son opérande.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Remplacez l’opérande `Preserve` par une valeur valide.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux dans Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensions de tableau dans Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim (instruction)](../language-reference/statements/redim-statement.md)
- [Dim (instruction)](../language-reference/statements/dim-statement.md)
