---
title: 'Procédure : copier un répertoire vers un autre répertoire en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9a02407ea805db4ae23f001de49ed6610f807b8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628882"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="0194f-102">Procédure : copier un répertoire vers un autre répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0194f-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="0194f-103">Utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> pour copier un répertoire vers un autre répertoire.</span><span class="sxs-lookup"><span data-stu-id="0194f-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="0194f-104">Cette méthode copie le contenu du répertoire, ainsi que le répertoire lui-même.</span><span class="sxs-lookup"><span data-stu-id="0194f-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="0194f-105">Si le répertoire cible n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="0194f-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="0194f-106">Si un répertoire portant le même nom existe à l’emplacement cible et que `overwrite` a la valeur `False`, le contenu des deux répertoires est fusionné.</span><span class="sxs-lookup"><span data-stu-id="0194f-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="0194f-107">Vous pouvez spécifier un nouveau nom pour le répertoire pendant l’opération.</span><span class="sxs-lookup"><span data-stu-id="0194f-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="0194f-108">Lors de la copie des fichiers dans un répertoire, des exceptions provoquées par un fichier spécifique peuvent être levées, par exemple si un fichier existe au cours d’une fusion alors que `overwrite` a la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="0194f-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="0194f-109">Quand ces exceptions sont levées, elles sont consolidées en une exception unique dont la propriété `Data` contient des entrées dans lesquelles le chemin du fichier ou répertoire est la clé et le message d’exception spécifique est contenu dans la valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="0194f-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="0194f-110">Pour copier un répertoire vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="0194f-110">To copy a directory to another directory</span></span>  
  
- <span data-ttu-id="0194f-111">Utilisez la méthode `CopyDirectory`, en spécifiant les noms des répertoires source et de destination.</span><span class="sxs-lookup"><span data-stu-id="0194f-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="0194f-112">L’exemple suivant copie le répertoire nommé `TestDirectory1` dans `TestDirectory2`, en remplaçant les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="0194f-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     <span data-ttu-id="0194f-113">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0194f-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="0194f-114">Dans le sélecteur d’extraits de code, il se trouve dans **Système de fichiers - Traitement des lecteurs, dossiers et fichiers**.</span><span class="sxs-lookup"><span data-stu-id="0194f-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="0194f-115">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="0194f-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0194f-116">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="0194f-116">Robust Programming</span></span>  
 <span data-ttu-id="0194f-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="0194f-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0194f-118">Le nouveau nom spécifié pour le répertoire contient un signe deux-points ( :) ou une barre oblique (\ ou /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0194f-119">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0194f-120">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0194f-121">`destinationDirectoryName` est soit `Nothing` soit une chaîne vide (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="0194f-122">Le répertoire source n’existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="0194f-123">Le répertoire source est un répertoire racine (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0194f-124">Le chemin combiné pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0194f-125">Le chemin source et le chemin cible sont identiques (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0194f-126">`ShowUI` a la valeur `UIOption.AllDialogs` et l’utilisateur annule l’opération, ou un ou plusieurs fichiers dans le répertoire ne peuvent pas être copiés (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="0194f-127">L’opération est cyclique (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
- <span data-ttu-id="0194f-128">Le chemin contient un signe deux-points (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0194f-129">Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0194f-130">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0194f-131">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0194f-132">Un fichier de destination existe mais n’est pas accessible (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0194f-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0194f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0194f-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="0194f-134">Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="0194f-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="0194f-135">Guide pratique pour placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="0194f-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
