---
title: Longueur d'enregistrement incorrecte
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869258"
---
# <a name="bad-record-length"></a>Longueur d'enregistrement incorrecte

Cette erreur peut avoir plusieurs causes, dont les suivantes :  
  
- La longueur d’une variable d’enregistrement spécifiée dans `FileGet` une `FileGetObject` `FilePut` instruction, ou `FilePutObject` diffère de la longueur spécifiée dans l' `FileOpen` instruction correspondante.  
  
- La variable dans une `FilePut` `FilePutObject` instruction ou est ou contient une chaîne de longueur variable.  
  
- La variable dans `FilePut` ou `FilePutObject` est ou comprend un `Variant` type.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que la somme des tailles des variables de longueur fixe dans le type défini par l’utilisateur qui définit le type de la variable d’enregistrement est identique à la valeur indiquée dans la `FileOpen` clause de l’instruction `Len` .  
  
2. Si la variable dans une `FilePut` `FilePutObject` instruction ou est ou contient une chaîne de longueur variable, assurez-vous que la chaîne de longueur variable comporte au moins 2 caractères plus courts que la longueur d’enregistrement spécifiée dans la `Len` clause de l' `FileOpen` instruction.  
  
3. Si la variable dans un `FilePut` ou `FilePutObject` est ou s’il comprend une, assurez-vous que `Variant` la chaîne de longueur variable est d’au moins 4 octets plus courts que la longueur d’enregistrement spécifiée dans la `Len` clause de l' `FileOpen` instruction.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
