---
title: 'Comment: Lire les personnages d’une chaîne'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155761"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="3916e-102">Comment: Lire les personnages d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="3916e-102">How to: Read characters from a string</span></span>
<span data-ttu-id="3916e-103">Les exemples de code suivants montrent comment lire des caractères de façon synchrone et asynchrone à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3916e-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="3916e-104">Exemple : Lisez les personnages de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="3916e-104">Example: Read characters synchronously</span></span>
 <span data-ttu-id="3916e-105">Cet exemple lit 13 caractères de façon synchrone à partir d’une chaîne, les stocke dans un tableau, puis les affiche.</span><span class="sxs-lookup"><span data-stu-id="3916e-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="3916e-106">Ensuite, l’exemple lit les caractères restants de la chaîne, les stocke dans le tableau à partir du sixième élément, puis affiche le contenu du tableau.</span><span class="sxs-lookup"><span data-stu-id="3916e-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="3916e-107">Exemple : Lisez les personnages asynchronement</span><span class="sxs-lookup"><span data-stu-id="3916e-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="3916e-108">L’exemple suivant montre le code-behind d’une application WPF.</span><span class="sxs-lookup"><span data-stu-id="3916e-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="3916e-109">Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="3916e-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="3916e-110">Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="3916e-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3916e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3916e-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="3916e-112">Fichier asynchrone I/O</span><span class="sxs-lookup"><span data-stu-id="3916e-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="3916e-113">[Comment : Créer une liste d’annuaire](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3916e-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="3916e-114">Comment : Lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="3916e-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="3916e-115">Comment : Ouvrez et appendicez à un fichier journal</span><span class="sxs-lookup"><span data-stu-id="3916e-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="3916e-116">Comment: Lire le texte d’un fichier</span><span class="sxs-lookup"><span data-stu-id="3916e-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="3916e-117">Comment: Écrire du texte à un fichier</span><span class="sxs-lookup"><span data-stu-id="3916e-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="3916e-118">Comment: Écrire des personnages à une chaîne</span><span class="sxs-lookup"><span data-stu-id="3916e-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="3916e-119">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="3916e-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
