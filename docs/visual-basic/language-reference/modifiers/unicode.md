---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402679"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode, quel que soit le nom de la procédure externe qui est déclarée.  
  
 Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations qu’il doit avoir pour pouvoir appeler la procédure correctement. Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise. L' [instruction DECLARE](../statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La `charsetmodifier` partie de l' `Declare` instruction fournit les informations du jeu de caractères pour marshaler les chaînes pendant un appel à la procédure externe. Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe. Le `Unicode` modificateur spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode et doit rechercher la procédure sans modifier son nom au cours de la recherche.  
  
 Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.  
  
## <a name="remarks"></a>Notes  
 Le `Unicode` modificateur peut être utilisé dans ce contexte :  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  
 Ce mot clé n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Ansi](ansi.md)
- [Auto](auto.md)
- [Mots clés](../keywords/index.md)
