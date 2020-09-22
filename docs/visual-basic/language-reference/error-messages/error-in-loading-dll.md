---
title: Erreur de chargement de la DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874383"
---
# <a name="error-in-loading-dll-visual-basic"></a>Erreur de chargement de la DLL (Visual Basic)

Une bibliothèque de liens dynamiques (DLL) est une bibliothèque spécifiée dans la `Lib` clause d’une `Declare` instruction. Les raisons possibles de cette erreur sont les suivantes :  
  
- Le fichier n’est pas un fichier exécutable DLL.  
  
- Le fichier n’est pas une DLL Microsoft Windows.  
  
- La DLL fait référence à une autre DLL qui n’est pas présente.  
  
- La DLL ou la DLL référencée ne se trouve pas dans un répertoire spécifié dans le chemin d’accès.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si le fichier est un fichier de texte source et qu’il n’est par conséquent pas un exécutable DLL, il doit être compilé et lié à un formulaire exécutable DLL.  
  
- Si le fichier n’est pas une DLL Microsoft Windows, obtenez l’équivalent Microsoft Windows.  
  
- Si la DLL fait référence à une autre DLL qui n’est pas présente, obtenez la DLL référencée et rendez-la disponible.  
  
- Si la dll ou la DLL référencée ne se trouve pas dans un répertoire spécifié par le chemin d’accès, déplacez la DLL vers un répertoire référencé.  
  
## <a name="see-also"></a>Voir aussi

- [Declare Statement](../statements/declare-statement.md)
