---
title: 'Procédure : rechercher des fichiers avec un modèle spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401639"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Guide pratique pour rechercher des fichiers avec un modèle spécifique en Visual Basic

La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des fichiers. Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique. Si vous voulez inclure des sous-répertoires dans la recherche, affectez la valeur `SearchOption.SearchAllSubDirectories` au paramètre `searchType`.  
  
 Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est détecté.  
  
> [!NOTE]
> Pour plus d’informations sur la façon de retourner une liste de fichiers à l’aide de la classe `DirectoryInfo` de l’espace de noms `System.IO`, consultez <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Pour rechercher des fichiers avec un modèle spécifique  
  
- Utilisez la méthode `GetFiles`, en fournissant le nom et le chemin du répertoire à rechercher et en spécifiant le modèle. L’exemple suivant retourne tous les fichiers ayant l’extension `.dll` contenus dans le répertoire, et il les ajoute à `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
- Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` pointe vers un fichier existant (<xref:System.IO.IOException>).  
  
- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
- Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).  
  
- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
- L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Procédure : rechercher des sous-répertoires avec un modèle spécifique](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Résolution des problèmes : lecture et écriture dans des fichiers texte](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Procédure : placer la collection de fichiers dans un répertoire](how-to-get-the-collection-of-files-in-a-directory.md)
