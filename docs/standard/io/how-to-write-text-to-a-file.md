---
title: 'Comment : écrire du texte dans un fichier'
description: Apprenez comment écrire ou ajouter du texte dans un fichier pour une application .NET. Utilisez les méthodes des classes StreamWriter ou file pour écrire du texte de façon synchrone ou asynchrone.
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: 52d3d07f4ffdbdc6510425a65fc173d36e674d06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447210"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="305d8-104">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="305d8-104">How to: Write text to a file</span></span>
<span data-ttu-id="305d8-105">Cette rubrique présente différentes façons d’écrire du texte dans un fichier pour une application .NET.</span><span class="sxs-lookup"><span data-stu-id="305d8-105">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="305d8-106">Les classes et méthodes suivantes sont généralement utilisées pour écrire du texte dans un fichier :</span><span class="sxs-lookup"><span data-stu-id="305d8-106">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="305d8-107"><xref:System.IO.StreamWriter> contient des méthodes permettant d’écrire dans un fichier de façon synchrone (<xref:System.IO.StreamWriter.Write%2A> et <xref:System.IO.TextWriter.WriteLine%2A>) ou asynchrone (<xref:System.IO.StreamWriter.WriteAsync%2A> et <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="305d8-107"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="305d8-108"><xref:System.IO.File> fournit des méthodes statiques pour écrire du texte dans un fichier, comme <xref:System.IO.File.WriteAllLines%2A> et <xref:System.IO.File.WriteAllText%2A>, ou pour ajouter du texte à un fichier, comme <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> et <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="305d8-108"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="305d8-109"><xref:System.IO.Path> concerne les chaînes qui contiennent des informations relatives au chemin d’un fichier ou d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="305d8-109"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="305d8-110">Elle contient la méthode <xref:System.IO.Path.Combine%2A> et, dans .NET Core versions 2.1 et ultérieures, les méthodes <xref:System.IO.Path.Join%2A> et <xref:System.IO.Path.TryJoin%2A>, qui permettent la concaténation de chaînes pour générer un chemin de fichier ou de répertoire.</span><span class="sxs-lookup"><span data-stu-id="305d8-110">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="305d8-111">Les exemples suivants ne montrent que la quantité minimale de code nécessaire.</span><span class="sxs-lookup"><span data-stu-id="305d8-111">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="305d8-112">Une application réelle fournit généralement une vérification des erreurs et une gestion des exceptions plus robuste.</span><span class="sxs-lookup"><span data-stu-id="305d8-112">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="305d8-113">Exemple : écrire du texte de façon synchrone avec StreamWriter</span><span class="sxs-lookup"><span data-stu-id="305d8-113">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="305d8-114">L’exemple suivant montre comment utiliser la classe <xref:System.IO.StreamWriter> pour écrire, ligne par ligne, du texte de façon synchrone dans un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="305d8-114">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="305d8-115">Étant donné que l’objet <xref:System.IO.StreamWriter> est déclaré et instancié dans une instruction `using`, la méthode <xref:System.IO.StreamWriter.Dispose%2A> est appelée, ce qui vide et ferme automatiquement le flux.</span><span class="sxs-lookup"><span data-stu-id="305d8-115">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="305d8-116">Exemple : ajouter de façon synchrone du texte avec StreamWriter</span><span class="sxs-lookup"><span data-stu-id="305d8-116">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="305d8-117">L’exemple suivant montre comment utiliser la classe <xref:System.IO.StreamWriter> pour ajouter du texte de façon synchrone au fichier texte créé dans le premier exemple.</span><span class="sxs-lookup"><span data-stu-id="305d8-117">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="305d8-118">Exemple : écrire du texte de façon asynchrone avec StreamWriter</span><span class="sxs-lookup"><span data-stu-id="305d8-118">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="305d8-119">L’exemple suivant montre comment écrire du texte de façon asynchrone dans un nouveau fichier à l’aide de la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="305d8-119">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="305d8-120">Pour appeler la méthode <xref:System.IO.StreamWriter.WriteAsync%2A>, l’appel de méthode doit se trouver dans une méthode `async`.</span><span class="sxs-lookup"><span data-stu-id="305d8-120">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="305d8-121">L’exemple C# nécessite C# 7.1 ou version ultérieure, qui ajoute la prise en charge du modificateur `async` sur le point d’entrée du programme.</span><span class="sxs-lookup"><span data-stu-id="305d8-121">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="305d8-122">Exemple : écrire et ajouter du texte avec la classe file</span><span class="sxs-lookup"><span data-stu-id="305d8-122">Example: Write and append text with the File class</span></span>

<span data-ttu-id="305d8-123">L’exemple suivant montre comment écrire du texte dans un nouveau fichier et ajouter de nouvelles lignes de texte à ce même fichier à l’aide de la classe <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="305d8-123">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="305d8-124">Les méthodes <xref:System.IO.File.WriteAllText%2A> et <xref:System.IO.File.AppendAllLines%2A> ouvrent et ferment automatiquement le fichier.</span><span class="sxs-lookup"><span data-stu-id="305d8-124">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="305d8-125">Si le chemin que vous fournissez à la méthode <xref:System.IO.File.WriteAllText%2A> existe déjà, le fichier est remplacé.</span><span class="sxs-lookup"><span data-stu-id="305d8-125">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="305d8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305d8-126">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="305d8-127">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="305d8-127">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="305d8-128">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="305d8-128">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="305d8-129">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="305d8-129">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="305d8-130">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="305d8-130">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="305d8-131">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="305d8-131">File and stream I/O</span></span>](index.md)
