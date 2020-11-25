---
title: 'Procédure : rechercher des fichiers et des répertoires existants dans un stockage isolé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: 43685a6ecb92510ad8d80c472a1c774d46cbb5f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734632"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Procédure : rechercher des fichiers et des répertoires existants dans un stockage isolé

Pour rechercher un répertoire dans un stockage isolé, utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>. Cette méthode prend une chaîne qui représente un modèle de recherche. Vous pouvez utiliser des caractères génériques à caractère unique (?) et à caractères multiples (\*) dans le modèle de recherche, mais les caractères génériques doivent apparaître dans la partie finale du nom. Par exemple, `directory1/*ect*` est une chaîne de recherche valide, mais `*ect*/directory2` ne l’est pas.  
  
 Utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> pour rechercher un fichier. La restriction des caractères génériques dans des chaînes de recherche qui s’applique à <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> s’applique également à <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Aucune de ces méthodes n’est récursive ; la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ne fournit pas de méthode pour répertorier tous les répertoires ou fichiers de votre magasin. Toutefois, les méthodes récursives sont affichées dans l’exemple de code suivant.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé. Tout d’abord, un magasin isolé pour l’utilisateur, le domaine et l’assembly est récupéré et placé dans la variable `isoStore`. La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> est utilisée pour configurer quelques répertoires différents dans lesquels le constructeur <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> crée des fichiers. Le code parcourt ensuite en boucle les résultats de la méthode `GetAllDirectories`. Cette méthode utilise <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour rechercher tous les noms de répertoires dans le répertoire actif. Ces noms sont stockés dans un tableau, puis `GetAllDirectories` appelle lui-même en passant dans chaque répertoire détecté. Par conséquent, tous les noms de répertoires sont retournés dans un tableau. Ensuite, le code appelle la méthode `GetAllFiles`. Cette méthode appelle `GetAllDirectories` pour connaître les noms de tous les répertoires, puis recherche des fichiers dans chaque répertoire à l’aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>. Le résultat est retourné dans un tableau pour y être affiché.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Stockage isolé](isolated-storage.md)
