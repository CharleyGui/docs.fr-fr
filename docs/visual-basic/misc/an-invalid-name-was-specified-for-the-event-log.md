---
title: Un nom de fichier non valide a été spécifié pour le journal des événements
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412921"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Un nom de fichier non valide a été spécifié pour le journal des événements
Un nom de fichier non valide a été spécifié pour le journal des événements. Cette erreur est généralement due à des caractères non valides dans le nom, à un nom de fichier vide ou à un nom de fichier trop long.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si le nom spécifié fait plus de huit caractères, vérifiez qu’il n’existe aucun conflit avec les noms des autres journaux des événements. Seuls les huit premiers caractères sont évalués pour déterminer si le nom est unique.  
  
- Si vous fournissez un chemin, vérifiez qu’il est correctement analysé.  
  
- Vérifiez que le nom ne contient aucun caractère non valide. Les caractères `<`, `>`, `:`, `"`, `/`, `\`et `|`ne peuvent pas être utilisés dans un nom de fichier.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : analyser des chemins de fichiers](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Procédure : renommer un fichier](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
