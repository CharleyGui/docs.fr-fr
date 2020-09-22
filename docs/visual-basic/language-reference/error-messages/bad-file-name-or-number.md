---
title: Nom ou numéro de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874901"
---
# <a name="bad-file-name-or-number"></a>Nom ou numéro de fichier incorrect

Une erreur s’est produite lors de la tentative d’accès au fichier spécifié. Cette erreur peut avoir plusieurs causes :  
  
- Une instruction fait référence à un fichier avec un nom ou un numéro de fichier qui n’a pas été spécifié dans l' `FileOpen` instruction ou qui a été spécifié dans une `FileOpen` instruction, mais qui a été fermé par la suite.  
  
- Une instruction fait référence à un fichier avec un nombre qui est en dehors de la plage de numéros de fichiers.  
  
- Une instruction fait référence à un nom de fichier ou à un nombre qui n’est pas valide.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que le nom de fichier est spécifié dans une `FileOpen` instruction. Notez que si vous avez appelé l' `FileClose` instruction sans arguments, vous avez peut-être fermé par inadvertance tous les fichiers ouverts.  
  
2. Si votre code génère des numéros de fichier algorithmiquement, assurez-vous que les nombres sont valides.  
  
3. Vérifiez les noms de fichiers pour vous assurer qu’ils sont conformes aux conventions du système d’exploitation.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Conventions d'affectation de noms Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
