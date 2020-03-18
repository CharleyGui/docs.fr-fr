---
title: Comment obtenir des informations sur les fichiers, les dossiers et les lecteurs - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705208"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="aa9e6-102">Comment obtenir des informations sur les fichiers, les dossiers et les lecteurs (Guide de programmation CMD)</span><span class="sxs-lookup"><span data-stu-id="aa9e6-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="aa9e6-103">Dans le .NET Framework, vous pouvez accéder aux informations sur le système de fichiers en utilisant les classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa9e6-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="aa9e6-104">Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo> représentent un fichier ou un répertoire. Elles contiennent des propriétés qui exposent une grande partie des attributs de fichiers pris en charge par le système de fichiers NTFS.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="aa9e6-105">Elles contiennent également des méthodes pour ouvrir, fermer, déplacer et supprimer des fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="aa9e6-106">Vous pouvez créer des instances de ces classes en passant une chaîne qui représente le nom du fichier, dossier ou lecteur dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="aa9e6-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="aa9e6-107">Vous pouvez aussi obtenir les noms des fichiers, dossiers ou lecteurs en appelant <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> et <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="aa9e6-108">Les classes <xref:System.IO.Directory?displayProperty=nameWithType> et <xref:System.IO.File?displayProperty=nameWithType> fournissent des méthodes statiques pour récupérer des informations sur les répertoires et les fichiers.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa9e6-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="aa9e6-109">Example</span></span>  
 <span data-ttu-id="aa9e6-110">L’exemple suivant illustre différentes manières d’accéder aux informations sur les fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aa9e6-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="aa9e6-111">Robust Programming</span></span>  
 <span data-ttu-id="aa9e6-112">Quand vous traitez des chaînes de chemin spécifiées par l’utilisateur, vous devez également gérer les exceptions dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="aa9e6-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="aa9e6-113">Le nom de fichier est mal formé.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-113">The file name is malformed.</span></span> <span data-ttu-id="aa9e6-114">Par exemple, il contient des caractères non valides ou uniquement des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="aa9e6-115">Le nom de fichier est null.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-115">The file name is null.</span></span>  
  
- <span data-ttu-id="aa9e6-116">Le nom de fichier est plus long que la longueur maximale définie par le système.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="aa9e6-117">Le nom de fichier contient un signe deux-points (:).</span><span class="sxs-lookup"><span data-stu-id="aa9e6-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="aa9e6-118">Si l’application ne dispose pas des autorisations suffisantes pour lire le fichier spécifié, la méthode `Exists` retourne `false` indépendamment de l’existence d’un chemin. La méthode ne lève pas d’exception.</span><span class="sxs-lookup"><span data-stu-id="aa9e6-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9e6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa9e6-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="aa9e6-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aa9e6-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aa9e6-121">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="aa9e6-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
