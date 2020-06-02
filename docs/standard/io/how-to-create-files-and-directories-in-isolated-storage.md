---
title: 'Procédure : créer des fichiers et des répertoires dans un stockage isolé'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: b74bf62dabe24765e07ffa6820cc1675122a9122
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288548"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="6d82d-102">Procédure : créer des fichiers et des répertoires dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="6d82d-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="6d82d-103">Après avoir obtenu un magasin isolé, vous pouvez créer des répertoires et des fichiers pour le stockage des données.</span><span class="sxs-lookup"><span data-stu-id="6d82d-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="6d82d-104">Dans un magasin, les noms de répertoires et de fichiers sont spécifiées par rapport à la racine du système de fichiers virtuel.</span><span class="sxs-lookup"><span data-stu-id="6d82d-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="6d82d-105">Pour créer un répertoire, utilisez la méthode d’instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d82d-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="6d82d-106">Si vous spécifiez un sous-répertoire d’un répertoire qui n’existe pas, les deux répertoires sont créés.</span><span class="sxs-lookup"><span data-stu-id="6d82d-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="6d82d-107">Si vous spécifiez un répertoire qui existe déjà, la méthode retourne sans créer de répertoire et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="6d82d-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="6d82d-108">Toutefois, si vous spécifiez un nom de répertoire qui contient des caractères non valides, une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée.</span><span class="sxs-lookup"><span data-stu-id="6d82d-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="6d82d-109">Utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> pour créer un fichier.</span><span class="sxs-lookup"><span data-stu-id="6d82d-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6d82d-110">Dans le système d’exploitation Windows, les noms de fichiers et de répertoires du stockage isolé ne sont pas sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="6d82d-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="6d82d-111">Autrement dit, si vous créez un fichier nommé `ThisFile.txt`, puis créez un autre fichier nommé `THISFILE.TXT`, un seul fichier est créé.</span><span class="sxs-lookup"><span data-stu-id="6d82d-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="6d82d-112">Le nom de fichier conserve sa casse d’origine pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="6d82d-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d82d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d82d-113">Example</span></span>  
 <span data-ttu-id="6d82d-114">L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé.</span><span class="sxs-lookup"><span data-stu-id="6d82d-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6d82d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d82d-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="6d82d-116">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="6d82d-116">Isolated Storage</span></span>](isolated-storage.md)
