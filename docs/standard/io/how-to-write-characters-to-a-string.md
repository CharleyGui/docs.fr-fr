---
title: 'Comment : écrire des caractères dans une chaîne'
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: d4a6bbc77a9feb16293fc88e1598d124d8d2d75d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829724"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="fac31-102">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="fac31-102">How to: Write characters to a string</span></span>

<span data-ttu-id="fac31-103">Les exemples de code suivants écrivent les caractères d’un tableau dans une chaîne de façon synchrone et asynchrone.</span><span class="sxs-lookup"><span data-stu-id="fac31-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="fac31-104">Exemple : écrire des caractères de façon synchrone dans une application console</span><span class="sxs-lookup"><span data-stu-id="fac31-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="fac31-105">L’exemple suivant utilise un <xref:System.IO.StringWriter> pour écrire cinq caractères dans un objet <xref:System.Text.StringBuilder> de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="fac31-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="fac31-106">Exemple : écrire des caractères de façon asynchrone dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="fac31-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="fac31-107">L’exemple suivant montre le code-behind d’une application WPF.</span><span class="sxs-lookup"><span data-stu-id="fac31-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="fac31-108">Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="fac31-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="fac31-109">Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="fac31-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fac31-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fac31-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="fac31-111">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="fac31-111">File and stream I/O</span></span>](index.md)  
- [<span data-ttu-id="fac31-112">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="fac31-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- [<span data-ttu-id="fac31-113">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="fac31-113">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="fac31-114">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="fac31-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="fac31-115">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="fac31-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="fac31-116">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="fac31-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="fac31-117">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="fac31-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="fac31-118">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="fac31-118">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)
