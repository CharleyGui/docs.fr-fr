---
title: Accès aux fichiers
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: 22bcd0f1f3acb0c0ad899b83ad2d879ead948f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348895"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="f8d98-102">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8d98-102">File Access with Visual Basic</span></span>

<span data-ttu-id="f8d98-103">L’objet `My.Computer.FileSystem` fournit des outils pour l’utilisation des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="f8d98-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="f8d98-104">Ses propriétés, méthodes et événements permettent de créer, copier, déplacer, examiner et supprimer des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="f8d98-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="f8d98-105">`My.Computer.FileSystem` offre de meilleures performances que les fonctions héritées (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) qui sont fournies par Visual Basic pour une compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="f8d98-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8d98-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f8d98-106">In This Section</span></span>  

 [<span data-ttu-id="f8d98-107">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="f8d98-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="f8d98-108">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour lire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="f8d98-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="f8d98-109">Écrire dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="f8d98-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="f8d98-110">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour écrire dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="f8d98-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="f8d98-111">Création, suppression et déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="f8d98-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="f8d98-112">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour la création, la copie, la suppression et le déplacement de fichiers et de dossiers.</span><span class="sxs-lookup"><span data-stu-id="f8d98-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="f8d98-113">Analyse des fichiers texte avec l'objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="f8d98-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="f8d98-114">Explique comment utiliser `TextFieldReader` pour analyser des fichiers texte tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="f8d98-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="f8d98-115">Encodages de fichiers</span><span class="sxs-lookup"><span data-stu-id="f8d98-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="f8d98-116">Décrit les encodages de fichiers et leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="f8d98-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="f8d98-117">Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8d98-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="f8d98-118">Montre comment créer un utilitaire qui fournit des informations sur les fichiers et les dossiers.</span><span class="sxs-lookup"><span data-stu-id="f8d98-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="f8d98-119">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="f8d98-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="f8d98-120">Répertorie les problèmes courants rencontrés lors des opérations de lecture et d’écriture dans des fichiers texte, et suggère des solutions pour chaque problème.</span><span class="sxs-lookup"><span data-stu-id="f8d98-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
