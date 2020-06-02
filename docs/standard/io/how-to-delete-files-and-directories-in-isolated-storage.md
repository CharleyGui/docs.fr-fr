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
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="d5531-102">Procédure : supprimer des fichiers et des répertoires dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="d5531-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="d5531-103">Vous pouvez supprimer des répertoires et des fichiers dans un fichier de stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="d5531-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="d5531-104">Dans un magasin, les noms de répertoires et de fichiers dépendent du système d’exploitation et sont spécifiées par rapport à la racine du système de fichiers virtuel.</span><span class="sxs-lookup"><span data-stu-id="d5531-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="d5531-105">Ils ne sont pas sensibles à la casse sur les systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="d5531-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="d5531-106">La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> fournit deux méthodes pour supprimer des répertoires et des fichiers : <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5531-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="d5531-107">Une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée si vous essayez de supprimer un fichier ou un répertoire qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d5531-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="d5531-108">Si vous incluez un caractère générique dans le nom, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lève une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lève une exception <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d5531-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="d5531-109">La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> échoue si le répertoire contient des fichiers ou des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="d5531-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="d5531-110">Vous pouvez utiliser les méthodes <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour récupérer les fichiers et les répertoires existants.</span><span class="sxs-lookup"><span data-stu-id="d5531-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="d5531-111">Pour plus d’informations sur la recherche dans le système de fichiers virtuel d’un magasin, consultez [Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="d5531-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5531-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5531-112">Example</span></span>  
 <span data-ttu-id="d5531-113">L’exemple de code suivant crée et supprime ensuite plusieurs fichiers et répertoires.</span><span class="sxs-lookup"><span data-stu-id="d5531-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d5531-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5531-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="d5531-115">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="d5531-115">Isolated Storage</span></span>](isolated-storage.md)
