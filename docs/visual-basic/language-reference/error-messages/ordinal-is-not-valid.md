---
title: Nombre non valide
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413051"
---
# <a name="ordinal-is-not-valid"></a>Nombre non valide
Votre appel à une bibliothèque de liens dynamiques (DLL) indiquait d’utiliser un nombre au lieu d’un nom de procédure, à l’aide de la `#num` syntaxe. Cette erreur a les causes possibles suivantes :  
  
- Une tentative de conversion `#num` de l’expression en ordinal a échoué.  
  
- Le `#num` spécifié ne spécifie pas de fonction dans la dll.  
  
- Une bibliothèque de types a une déclaration non valide, ce qui entraîne l’utilisation interne d’un nombre ordinal non valide.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que l’expression représente un nombre valide ou appelez la procédure par nom.  
  
2. Assurez-vous que `#num` identifie une fonction valide dans la dll.  
  
3. Isolez l’appel de procédure à l’origine du problème en commentant le code. Écrivez une `Declare` instruction pour la procédure et signalez le problème au fournisseur de la bibliothèque de types.  
  
## <a name="see-also"></a>Voir aussi

- [Declare Statement](../statements/declare-statement.md)
