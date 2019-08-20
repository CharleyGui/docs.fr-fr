---
title: Système de fichiers et Registre - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: ef6c1da09ea0435643caba0f5e2819c064f8db01
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589912"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="e33b7-102">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e33b7-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="e33b7-103">Les rubriques suivantes montrent comment utiliser C# et .NET Framework pour effectuer différentes opérations de base sur les fichiers, les dossiers et le Registre.</span><span class="sxs-lookup"><span data-stu-id="e33b7-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e33b7-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e33b7-104">In This Section</span></span>  
  
|<span data-ttu-id="e33b7-105">**Titre**</span><span class="sxs-lookup"><span data-stu-id="e33b7-105">**Title**</span></span>|<span data-ttu-id="e33b7-106">**Description**</span><span class="sxs-lookup"><span data-stu-id="e33b7-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="e33b7-107">Guide pratique pour itérer au sein d’une arborescence de répertoires</span><span class="sxs-lookup"><span data-stu-id="e33b7-107">How to: Iterate Through a Directory Tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="e33b7-108">Montre comment itérer manuellement au sein d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="e33b7-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="e33b7-109">Guide pratique pour obtenir des informations sur les fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="e33b7-109">How to: Get Information About Files, Folders, and Drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="e33b7-110">Montre comment extraire des informations, par exemple l’heure de création et la taille, sur les fichiers, dossiers et lecteurs.</span><span class="sxs-lookup"><span data-stu-id="e33b7-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="e33b7-111">Guide pratique pour créer un fichier ou un dossier</span><span class="sxs-lookup"><span data-stu-id="e33b7-111">How to: Create a File or Folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="e33b7-112">Montre comment créer un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="e33b7-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="e33b7-113">Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e33b7-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="e33b7-114">Montre comment copier, supprimer et déplacer des fichiers et dossiers (C#).</span><span class="sxs-lookup"><span data-stu-id="e33b7-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="e33b7-115">Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers</span><span class="sxs-lookup"><span data-stu-id="e33b7-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="e33b7-116">Montre comment afficher une boîte de dialogue de progression Windows standard pour certaines opérations de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e33b7-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="e33b7-117">Guide pratique pour écrire dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="e33b7-117">How to: Write to a Text File</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="e33b7-118">Montre comment écrire dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e33b7-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="e33b7-119">Guide pratique pour lire à partir d'un fichier texte</span><span class="sxs-lookup"><span data-stu-id="e33b7-119">How to: Read From a Text File</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="e33b7-120">Montre comment lire un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e33b7-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="e33b7-121">Guide pratique pour lire un fichier texte ligne par ligne</span><span class="sxs-lookup"><span data-stu-id="e33b7-121">How to: Read a Text File One Line at a Time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="e33b7-122">Montre comment récupérer du texte dans un fichier une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="e33b7-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="e33b7-123">Guide pratique pour créer une clé dans le Registre</span><span class="sxs-lookup"><span data-stu-id="e33b7-123">How to: Create a Key In the Registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="e33b7-124">Montre comment écrire une clé dans le registre du système.</span><span class="sxs-lookup"><span data-stu-id="e33b7-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="e33b7-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="e33b7-125">Related Sections</span></span>  
 [<span data-ttu-id="e33b7-126">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="e33b7-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="e33b7-127">Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e33b7-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="e33b7-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e33b7-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="e33b7-129">Fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="e33b7-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
