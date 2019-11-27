---
title: Erreur de chargement de la DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329557"
---
# <a name="error-in-loading-dll-visual-basic"></a>Erreur de chargement de la DLL (Visual Basic)
Une bibliothèque de liens dynamiques (DLL) est une bibliothèque spécifiée dans la clause `Lib` d’une instruction `Declare`. Les raisons possibles de cette erreur sont les suivantes :  
  
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

- [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)
