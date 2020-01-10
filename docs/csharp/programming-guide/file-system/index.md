---
title: Système de fichiers et Registre - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 2540c816a102a7f11f1f103b993194cccf0f4688
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75704519"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="83161-102">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="83161-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="83161-103">Les rubriques suivantes montrent comment utiliser C# et .NET Framework pour effectuer différentes opérations de base sur les fichiers, les dossiers et le Registre.</span><span class="sxs-lookup"><span data-stu-id="83161-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83161-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="83161-104">In This Section</span></span>  
  
|<span data-ttu-id="83161-105">**Titre**</span><span class="sxs-lookup"><span data-stu-id="83161-105">**Title**</span></span>|<span data-ttu-id="83161-106">**Description**</span><span class="sxs-lookup"><span data-stu-id="83161-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="83161-107">Comment itérer au sein d’une arborescence de répertoires</span><span class="sxs-lookup"><span data-stu-id="83161-107">How to iterate through a directory tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="83161-108">Montre comment itérer manuellement au sein d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="83161-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="83161-109">Obtention d’informations sur les fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="83161-109">How to get information about files, folders, and drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="83161-110">Montre comment extraire des informations, par exemple l’heure de création et la taille, sur les fichiers, dossiers et lecteurs.</span><span class="sxs-lookup"><span data-stu-id="83161-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="83161-111">Comment créer un fichier ou un dossier</span><span class="sxs-lookup"><span data-stu-id="83161-111">How to create a file or folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="83161-112">Montre comment créer un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="83161-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="83161-113">Comment copier, supprimer et déplacer des fichiers et des dossiers (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="83161-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="83161-114">Montre comment copier, supprimer et déplacer des fichiers et dossiers (C#).</span><span class="sxs-lookup"><span data-stu-id="83161-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="83161-115">Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers</span><span class="sxs-lookup"><span data-stu-id="83161-115">How to provide a progress dialog box for file operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="83161-116">Montre comment afficher une boîte de dialogue de progression Windows standard pour certaines opérations de fichiers.</span><span class="sxs-lookup"><span data-stu-id="83161-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="83161-117">Comment écrire dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="83161-117">How to write to a text file</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="83161-118">Montre comment écrire dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="83161-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="83161-119">Comment lire un fichier texte</span><span class="sxs-lookup"><span data-stu-id="83161-119">How to read from a text file</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="83161-120">Montre comment lire un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="83161-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="83161-121">Comment lire un fichier texte ligne par ligne</span><span class="sxs-lookup"><span data-stu-id="83161-121">How to read a text file one line at a time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="83161-122">Montre comment récupérer du texte dans un fichier une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="83161-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="83161-123">Comment créer une clé dans le registre</span><span class="sxs-lookup"><span data-stu-id="83161-123">How to create a key in the registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="83161-124">Montre comment écrire une clé dans le registre du système.</span><span class="sxs-lookup"><span data-stu-id="83161-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="83161-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="83161-125">Related Sections</span></span>  
 [<span data-ttu-id="83161-126">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="83161-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="83161-127">Comment copier, supprimer et déplacer des fichiers et des dossiers (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="83161-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)
  
 [<span data-ttu-id="83161-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="83161-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="83161-129">Fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="83161-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
