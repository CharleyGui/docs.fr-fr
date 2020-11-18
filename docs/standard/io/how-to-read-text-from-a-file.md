---
title: 'Comment : lire du texte à partir d’un fichier'
description: Dans cet article, consultez des exemples montrant comment lire du texte de façon synchrone ou asynchrone à partir d’un fichier texte, à l’aide de la classe StreamReader dans .NET pour les applications de bureau.
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 7c772ec1de41d0ba2b4ef0d924a252326ee6909e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823366"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="bf134-103">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="bf134-103">How to: Read text from a file</span></span>

<span data-ttu-id="bf134-104">Les exemples suivants montrent comment lire le texte de façon synchrone et asynchrone à partir d'un fichier texte à l'aide du .NET pour les applications de bureau.</span><span class="sxs-lookup"><span data-stu-id="bf134-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="bf134-105">Dans les deux exemples, lorsque vous créez l’instance de la classe <xref:System.IO.StreamReader>, vous fournissez le chemin d’accès relatif ou absolu au fichier.</span><span class="sxs-lookup"><span data-stu-id="bf134-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bf134-106">Ces exemples de code ne s’appliquent pas aux applications Windows universelles, car le Windows Runtime fournit différents types de flux pour la lecture et l’écriture dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="bf134-106">These code examples do not apply to Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="bf134-107">Pour obtenir un exemple qui montre comment lire le texte d’un fichier dans une application UWP, consultez [démarrage rapide : lecture et écriture de fichiers](/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="bf134-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="bf134-108">Pour obtenir des exemples qui montrent comment effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime, consultez [Comment : effectuer une conversion entre des flux de .NET Framework et des](how-to-convert-between-dotnet-streams-and-winrt-streams.md)flux de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="bf134-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="bf134-109">Exemple : lecture synchrone dans une application console</span><span class="sxs-lookup"><span data-stu-id="bf134-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="bf134-110">L’exemple suivant montre une opération de lecture synchrone dans une application console.</span><span class="sxs-lookup"><span data-stu-id="bf134-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="bf134-111">Cet exemple ouvre le fichier texte à l’aide d’un lecteur de flux, copie le contenu dans une chaîne, puis retourne une chaîne dans la console.</span><span class="sxs-lookup"><span data-stu-id="bf134-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf134-112">L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.</span><span class="sxs-lookup"><span data-stu-id="bf134-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="bf134-113">Exemple : lecture asynchrone dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="bf134-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="bf134-114">L’exemple suivant montre une opération de lecture asynchrone dans une application WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="bf134-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf134-115">L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.</span><span class="sxs-lookup"><span data-stu-id="bf134-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a><span data-ttu-id="bf134-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf134-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="bf134-117">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="bf134-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="bf134-118">[Procédure : créer une liste de répertoires](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bf134-118">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- <span data-ttu-id="bf134-119">[Démarrage rapide : lire et écrire dans des fichiers](/previous-versions/windows/apps/hh758325(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bf134-119">[Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10))</span></span>  
- [<span data-ttu-id="bf134-120">Comment : effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="bf134-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="bf134-121">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="bf134-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="bf134-122">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="bf134-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="bf134-123">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="bf134-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="bf134-124">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="bf134-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="bf134-125">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="bf134-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="bf134-126">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="bf134-126">File and stream I/O</span></span>](index.md)
