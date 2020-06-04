---
title: Les instructions 'Module' ne peuvent intervenir qu'au niveau du fichier ou de l'espace de noms
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397205"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Les instructions 'Module' ne peuvent intervenir qu'au niveau du fichier ou de l'espace de noms
`Module`les instructions doivent apparaître en haut de votre fichier source immédiatement après `Option` et `Imports` les instructions, les attributs globaux et les déclarations d’espaces de noms, mais avant toutes les autres déclarations.  
  
 **ID d’erreur :** BC30617  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez l’instruction `Module` en haut de votre déclaration d’espace de noms ou de votre fichier source.  
  
## <a name="see-also"></a>Voir aussi

- [Module, instruction](../statements/module-statement.md)
