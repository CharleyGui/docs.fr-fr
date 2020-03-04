---
title: 'Comment : lire du texte à partir d’un fichier'
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155722"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="9f802-102">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="9f802-102">How to: Read text from a file</span></span>
<span data-ttu-id="9f802-103">Les exemples suivants montrent comment lire le texte de façon synchrone et asynchrone à partir d'un fichier texte à l'aide du .NET pour les applications de bureau.</span><span class="sxs-lookup"><span data-stu-id="9f802-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="9f802-104">Dans les deux exemples, lorsque vous créez l’instance de la classe <xref:System.IO.StreamReader>, vous fournissez le chemin d’accès relatif ou absolu au fichier.</span><span class="sxs-lookup"><span data-stu-id="9f802-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9f802-105">Ces exemples de code ne s’appliquent pas au développement d’applications UWP, car le Windows Runtime fournit des types de flux différents pour la lecture et l’écriture des fichiers.</span><span class="sxs-lookup"><span data-stu-id="9f802-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="9f802-106">Pour obtenir un exemple qui montre comment lire le texte d’un fichier dans une application UWP, consultez [démarrage rapide : lecture et écriture de fichiers](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="9f802-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="9f802-107">Pour obtenir des exemples qui montrent comment effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime, consultez [Comment : effectuer une conversion entre des flux de .NET Framework et des](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)flux de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="9f802-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="9f802-108">Exemple : lecture synchrone dans une application console</span><span class="sxs-lookup"><span data-stu-id="9f802-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="9f802-109">L’exemple suivant montre une opération de lecture synchrone dans une application console.</span><span class="sxs-lookup"><span data-stu-id="9f802-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="9f802-110">Cet exemple ouvre le fichier texte à l’aide d’un lecteur de flux, copie le contenu dans une chaîne, puis retourne une chaîne dans la console.</span><span class="sxs-lookup"><span data-stu-id="9f802-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9f802-111">L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.</span><span class="sxs-lookup"><span data-stu-id="9f802-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="9f802-112">Exemple : lecture asynchrone dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="9f802-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="9f802-113">L’exemple suivant montre une opération de lecture asynchrone dans une application WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="9f802-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9f802-114">L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.</span><span class="sxs-lookup"><span data-stu-id="9f802-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f802-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f802-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="9f802-116">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="9f802-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="9f802-117">[Procédure : créer une liste de répertoires](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9f802-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="9f802-118">Démarrage rapide : lire et écrire dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="9f802-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="9f802-119">Comment : effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="9f802-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="9f802-120">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="9f802-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="9f802-121">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="9f802-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="9f802-122">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="9f802-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="9f802-123">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="9f802-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="9f802-124">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="9f802-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="9f802-125">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="9f802-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
