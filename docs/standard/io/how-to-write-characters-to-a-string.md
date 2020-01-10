---
title: 'Comment : écrire des caractères dans une chaîne'
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
ms.openlocfilehash: b53513ef0b373cdde7703eddcd182ab7fd15cb9b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706619"
---
# <a name="how-to-write-characters-to-a-string"></a>Comment : écrire des caractères dans une chaîne
Les exemples de code suivants écrivent les caractères d’un tableau dans une chaîne de façon synchrone et asynchrone.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Exemple : écrire des caractères de façon synchrone dans une application console  
 L’exemple suivant utilise un <xref:System.IO.StringWriter> pour écrire cinq caractères dans un objet <xref:System.Text.StringBuilder> de façon synchrone. 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Exemple : écrire des caractères de façon asynchrone dans une application WPF 
 L’exemple suivant montre le code-behind d’une application WPF. Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau. Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)  
- [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Comment : lire et écrire dans un fichier de données nouvellement créé](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Procédure : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Comment : lire du texte à partir d’un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment : lire les caractères d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
