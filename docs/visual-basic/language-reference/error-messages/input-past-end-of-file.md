---
title: L'entrée dépasse la fin du fichier
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873964"
---
# <a name="input-past-end-of-file"></a>L'entrée dépasse la fin du fichier

Soit une `Input` instruction lit à partir d’un fichier vide, soit une instruction dans laquelle toutes les données sont utilisées, ou vous avez utilisé la `EOF` fonction avec un fichier ouvert pour un accès binaire.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Utilisez la `EOF` fonction immédiatement avant l' `Input` instruction pour détecter la fin du fichier.  
  
2. Si le fichier est ouvert pour un accès binaire, utilisez `Seek` et `Loc` .  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
