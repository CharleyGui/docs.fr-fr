---
title: Les instructions 'Module' ne peuvent intervenir qu'au niveau du fichier ou de l'espace de noms
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 91e6c81bb64c259411cbef8a36629b8b320ea584
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873752"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Les instructions 'Module' ne peuvent intervenir qu'au niveau du fichier ou de l'espace de noms

`Module` les instructions doivent apparaître en haut de votre fichier source immédiatement après `Option` et `Imports` les instructions, les attributs globaux et les déclarations d’espaces de noms, mais avant toutes les autres déclarations.  
  
 **ID d’erreur :** BC30617  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez l’instruction `Module` en haut de votre déclaration d’espace de noms ou de votre fichier source.  
  
## <a name="see-also"></a>Voir aussi

- [Module, instruction](../statements/module-statement.md)
