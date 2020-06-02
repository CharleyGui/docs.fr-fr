---
title: 'Procédure : supprimer des fichiers et des répertoires dans un stockage isolé'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: dc84fefbde1177993b17e9ec687a1ef759b74735
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291901"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Procédure : supprimer des fichiers et des répertoires dans un stockage isolé
Vous pouvez supprimer des répertoires et des fichiers dans un fichier de stockage isolé. Dans un magasin, les noms de répertoires et de fichiers dépendent du système d’exploitation et sont spécifiées par rapport à la racine du système de fichiers virtuel. Ils ne sont pas sensibles à la casse sur les systèmes d’exploitation Windows.  
  
 La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> fournit deux méthodes pour supprimer des répertoires et des fichiers : <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée si vous essayez de supprimer un fichier ou un répertoire qui n’existe pas. Si vous incluez un caractère générique dans le nom, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lève une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lève une exception <xref:System.ArgumentException>.  
  
 La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> échoue si le répertoire contient des fichiers ou des sous-répertoires. Vous pouvez utiliser les méthodes <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour récupérer les fichiers et les répertoires existants. Pour plus d’informations sur la recherche dans le système de fichiers virtuel d’un magasin, consultez [Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé](how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant crée et supprime ensuite plusieurs fichiers et répertoires.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Stockage isolé](isolated-storage.md)
