---
title: Système de fichiers et registre - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900561"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="ed994-102">Système de fichiers et registre (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="ed994-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="ed994-103">Les articles suivants montrent comment utiliser C et .NET pour effectuer diverses opérations de base sur les fichiers, les dossiers et le registre.</span><span class="sxs-lookup"><span data-stu-id="ed994-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ed994-104">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="ed994-104">In this section</span></span>

|<span data-ttu-id="ed994-105">**Titre**</span><span class="sxs-lookup"><span data-stu-id="ed994-105">**Title**</span></span>|<span data-ttu-id="ed994-106">**Description**</span><span class="sxs-lookup"><span data-stu-id="ed994-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="ed994-107">Comment itérer au sein d’une arborescence de répertoires</span><span class="sxs-lookup"><span data-stu-id="ed994-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="ed994-108">Montre comment itérer manuellement au sein d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="ed994-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="ed994-109">Comment obtenir des informations sur les fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="ed994-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="ed994-110">Montre comment extraire des informations, par exemple l’heure de création et la taille, sur les fichiers, dossiers et lecteurs.</span><span class="sxs-lookup"><span data-stu-id="ed994-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="ed994-111">Comment créer un fichier ou un dossier</span><span class="sxs-lookup"><span data-stu-id="ed994-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="ed994-112">Montre comment créer un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="ed994-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="ed994-113">Comment copier, supprimer et déplacer des fichiers et des dossiers (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="ed994-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="ed994-114">Montre comment copier, supprimer et déplacer des fichiers et dossiers (C#).</span><span class="sxs-lookup"><span data-stu-id="ed994-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="ed994-115">Comment fournir une boîte de dialogue de progression pour les opérations de fichier</span><span class="sxs-lookup"><span data-stu-id="ed994-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="ed994-116">Montre comment afficher une boîte de dialogue de progression Windows standard pour certaines opérations de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ed994-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="ed994-117">Comment écrire dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="ed994-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="ed994-118">Montre comment écrire dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="ed994-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="ed994-119">Comment lire à partir d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="ed994-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="ed994-120">Montre comment lire un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="ed994-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="ed994-121">Comment lire un fichier texte ligne par ligne</span><span class="sxs-lookup"><span data-stu-id="ed994-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="ed994-122">Montre comment récupérer du texte dans un fichier une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="ed994-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="ed994-123">Comment créer une clé dans le Registre</span><span class="sxs-lookup"><span data-stu-id="ed994-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="ed994-124">Montre comment écrire une clé dans le registre du système.</span><span class="sxs-lookup"><span data-stu-id="ed994-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="ed994-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="ed994-125">Related sections</span></span>

- [<span data-ttu-id="ed994-126">Fichier et stream I/O</span><span class="sxs-lookup"><span data-stu-id="ed994-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="ed994-127">Comment copier, supprimer et déplacer des fichiers et des dossiers (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="ed994-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="ed994-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ed994-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
