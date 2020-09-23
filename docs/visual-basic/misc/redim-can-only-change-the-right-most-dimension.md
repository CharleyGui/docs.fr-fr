---
title: "'ReDim' ne peut changer que la dimension la plus à droite"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: c3a18bb93d1253628d73919b18fe4614d742d280
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077382"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' ne peut changer que la dimension la plus à droite

Une instruction `ReDim` a tenté d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension. Lors de l’utilisation de `Preserve`, vous pouvez redimensionner uniquement la dernière dimension d’un tableau. Pour toutes les autres dimensions, vous devez spécifier la même taille que pour le tableau existant.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez le mot clé `Preserve` .  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux dans Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensions de tableau dans Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim (instruction)](../language-reference/statements/redim-statement.md)
- [Dim (instruction)](../language-reference/statements/dim-statement.md)
