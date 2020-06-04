---
title: Erreur d’accès au chemin de fichier
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387255"
---
# <a name="pathfile-access-error"></a>Erreur dans le chemin d’accès
Au cours d’une opération d’accès au fichier ou d’accès au disque, le système d’exploitation n’a pas pu établir de connexion entre le chemin d’accès et le nom de fichier.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que la spécification de fichier est correctement mise en forme. Un nom de fichier peut contenir un chemin d’accès complet (absolu) ou relatif. Un chemin d’accès complet commence par le nom du lecteur (si le chemin d’accès se trouve sur un autre lecteur) et indique le chemin d’accès explicite de la racine au fichier. Tout chemin d’accès qui n’est pas complet est relatif au lecteur et au répertoire actifs.  
  
2. Assurez-vous que vous n’avez pas tenté d’enregistrer un fichier qui remplacerait un fichier en lecture seule existant. Si c’est le cas, modifiez l’attribut de lecture seule du fichier cible ou enregistrez le fichier sous un autre nom de fichier.  
  
3. Assurez-vous que vous n’avez pas tenté d’ouvrir un fichier en lecture seule en `Output` mode séquentiel ou en `Append` mode. Si c’est le cas, ouvrez le fichier en `Input` mode ou modifiez l’attribut de lecture seule du fichier.  
  
4. Assurez-vous que vous n’avez pas tenté de modifier un projet de Visual Basic dans une base de données ou un document.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
