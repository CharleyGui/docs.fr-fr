---
title: 'Comment: Écrire des personnages à une chaîne'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160276"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="b3ece-102">Comment: Écrire des personnages à une chaîne</span><span class="sxs-lookup"><span data-stu-id="b3ece-102">How to: Write characters to a string</span></span>
<span data-ttu-id="b3ece-103">Les exemples de code suivants écrivent les caractères d’un tableau dans une chaîne de façon synchrone et asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b3ece-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="b3ece-104">Exemple : Écrivez des caractères de façon synchronisée dans une application de console</span><span class="sxs-lookup"><span data-stu-id="b3ece-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="b3ece-105">L’exemple suivant utilise un <xref:System.IO.StringWriter> pour écrire cinq caractères dans un objet <xref:System.Text.StringBuilder> de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="b3ece-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="b3ece-106">Exemple : Écrivez des caractères asynchronement dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="b3ece-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="b3ece-107">L’exemple suivant montre le code-behind d’une application WPF.</span><span class="sxs-lookup"><span data-stu-id="b3ece-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="b3ece-108">Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="b3ece-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="b3ece-109">Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b3ece-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b3ece-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3ece-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="b3ece-111">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="b3ece-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="b3ece-112">Fichier asynchrone I/O</span><span class="sxs-lookup"><span data-stu-id="b3ece-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="b3ece-113">Comment : Énumérer les répertoires et les fichiers</span><span class="sxs-lookup"><span data-stu-id="b3ece-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="b3ece-114">Comment : Lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="b3ece-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="b3ece-115">Comment : Ouvrez et appendicez à un fichier journal</span><span class="sxs-lookup"><span data-stu-id="b3ece-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="b3ece-116">Comment: Lire le texte d’un fichier</span><span class="sxs-lookup"><span data-stu-id="b3ece-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="b3ece-117">Comment: Écrire du texte à un fichier</span><span class="sxs-lookup"><span data-stu-id="b3ece-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="b3ece-118">Comment: Lire les personnages d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="b3ece-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
