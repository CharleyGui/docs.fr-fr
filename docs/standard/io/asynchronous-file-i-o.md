---
title: E/S sur fichier asynchrones
description: En savoir plus sur les e/s de fichier asynchrones dans .NET. Découvrez les méthodes Async pour simplifier les opérations asynchrones, telles que ReadAsync, WriteAsync, etc.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: 9506a366b6f1e363ec13550e5ed68c7176dd4d0a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598617"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="7706b-104">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="7706b-104">Asynchronous File I/O</span></span>

<span data-ttu-id="7706b-105">Les opérations asynchrones vous permettent d'exécuter des opérations d'E/S consommant beaucoup de ressources sans bloquer le thread principal.</span><span class="sxs-lookup"><span data-stu-id="7706b-105">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="7706b-106">Cette considération de performance est particulièrement importante dans une application de Windows 8. x Store ou une application de bureau où une opération de flux de temps peut bloquer le thread d’interface utilisateur et faire apparaître votre application comme si elle ne fonctionnait pas.</span><span class="sxs-lookup"><span data-stu-id="7706b-106">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="7706b-107">Depuis .NET Framework 4.5, les types d’E/S incluent des méthodes asynchrones pour simplifier les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="7706b-107">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="7706b-108">Une méthode asynchrone contient `Async` dans son nom, comme <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, et <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="7706b-108">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="7706b-109">Ces méthodes asynchrones sont implémentées sur les classes de flux, telles que <xref:System.IO.Stream>, <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, et les classes qui sont utilisées pour lire ou écrire dans des flux, comme <xref:System.IO.TextReader> et l' <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="7706b-109">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="7706b-110">Dans .NET Framework 4 et les versions antérieures, on doit utiliser des méthodes telles que <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> pour implémenter les opérations d'E/S asynchrones.</span><span class="sxs-lookup"><span data-stu-id="7706b-110">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="7706b-111">Ces méthodes sont toujours disponibles dans .NET Framework 4.5 pour prendre en charge le code hérité. Toutefois, les méthodes asynchrones vous aident à implémenter les opérations d’E/S asynchrones plus facilement.</span><span class="sxs-lookup"><span data-stu-id="7706b-111">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="7706b-112">C# et Visual Basic ont chacun deux mots clés pour la programmation asynchrone :</span><span class="sxs-lookup"><span data-stu-id="7706b-112">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="7706b-113">`Async` (Visual Basic) ou `async` modificateur (C#), qui est utilisé pour marquer une méthode contenant une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7706b-113">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="7706b-114">`Await` (Visual Basic) ou `await` opérateur (C#), qui est appliqué au résultat d'une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7706b-114">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="7706b-115">Pour implémenter des opérations d'E/S asynchrones, utilisez ces mots clés conjointement aux méthodes async, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="7706b-115">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="7706b-116">Pour plus d'informations, consultez [Programmation asynchrone avec async et await (C#)](../../csharp/programming-guide/concepts/async/index.md) et [Programmation asynchrone avec Async et Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7706b-116">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="7706b-117">L'exemple suivant montre comment utiliser deux objets <xref:System.IO.FileStream> pour copier des fichiers de façon asynchrone d'un répertoire à un autre.</span><span class="sxs-lookup"><span data-stu-id="7706b-117">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="7706b-118">Notez que le gestionnaire d'événements <xref:System.Web.UI.WebControls.Button.Click> pour le contrôle <xref:System.Windows.Controls.Button> est marqué avec le modificateur `async` car il appelle une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7706b-118">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="7706b-119">L'exemple suivant est semblable au précédent, mais utilise des objets <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> pour lire et écrire le contenu d'un fichier texte de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7706b-119">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="7706b-120">L’exemple suivant montre le fichier code-behind et le fichier XAML utilisés pour ouvrir un fichier en tant que <xref:System.IO.Stream> dans une application du Windows 8. x Store et lire son contenu à l’aide d’une instance de la <xref:System.IO.StreamReader> classe.</span><span class="sxs-lookup"><span data-stu-id="7706b-120">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="7706b-121">Il utilise des méthodes asynchrones pour ouvrir le fichier en tant que flux et lire son contenu.</span><span class="sxs-lookup"><span data-stu-id="7706b-121">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="7706b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7706b-122">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="7706b-123">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="7706b-123">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="7706b-124">Programmation asynchrone avec Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="7706b-124">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="7706b-125">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7706b-125">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
