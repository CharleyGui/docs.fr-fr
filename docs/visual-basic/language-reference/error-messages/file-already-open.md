---
title: Le fichier est déjà ouvert.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874172"
---
# <a name="file-already-open"></a>Le fichier est déjà ouvert.

Parfois, un fichier doit être fermé avant une autre `FileOpen` opération ou une autre opération. Cette erreur peut avoir plusieurs causes, dont les suivantes :  
  
- Une `FileOpen` opération de mode de sortie séquentielle a été exécutée pour un fichier qui est déjà ouvert  
  
- Une instruction fait référence à un fichier ouvert.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Fermez le fichier avant d’exécuter l’instruction.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
