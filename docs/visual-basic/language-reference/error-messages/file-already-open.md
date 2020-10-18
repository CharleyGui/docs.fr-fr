---
title: Le fichier est déjà ouvert.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162750"
---
# <a name="file-already-open"></a>Le fichier est déjà ouvert.

Parfois, un fichier doit être fermé avant une autre `FileOpen` opération ou une autre opération. Cette erreur peut avoir plusieurs causes, dont les suivantes :

- Une `FileOpen` opération de mode de sortie séquentielle a été exécutée pour un fichier qui est déjà ouvert

- Une instruction fait référence à un fichier ouvert.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Fermez le fichier avant d’exécuter l’instruction.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
