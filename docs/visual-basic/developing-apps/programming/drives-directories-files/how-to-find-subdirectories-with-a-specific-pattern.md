---
title: 'Comment : rechercher des sous-répertoires avec un modèle spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348772"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique en Visual Basic

La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des sous-répertoires d’un répertoire. Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique. Si vous souhaitez inclure le contenu des sous-répertoires dans la recherche, affectez la valeur `SearchOption.SearchAllSubDirectories` au paramètre `searchType`.

Une collection vide est retournée si aucun répertoire correspondant au modèle spécifié n’est détecté.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Pour rechercher des sous-répertoires avec un modèle spécifique

Utilisez la méthode `GetDirectories`, en fournissant le nom et le chemin du répertoire à rechercher. L’exemple suivant retourne tous les répertoires dans la structure de répertoires dont le nom contient le mot « Logs », et il les ajoute à `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Programmation fiable

Les conditions ci-dessous peuvent générer une exception.

- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).

- Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).

- Un ou plusieurs des caractères génériques spécifiés sont `Nothing`, une chaîne vide ou contiennent uniquement des espaces (<xref:System.ArgumentNullException>).

- `directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).

- `directory` pointe vers un fichier existant (<xref:System.IO.IOException>).

- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).

- Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).

- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).

- L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Comment : rechercher des fichiers avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
