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
# <a name="how-to-write-characters-to-a-string"></a>Comment: Écrire des personnages à une chaîne
Les exemples de code suivants écrivent les caractères d’un tableau dans une chaîne de façon synchrone et asynchrone.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Exemple : Écrivez des caractères de façon synchronisée dans une application de console  
 L’exemple suivant utilise un <xref:System.IO.StringWriter> pour écrire cinq caractères dans un objet <xref:System.Text.StringBuilder> de façon synchrone.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Exemple : Écrivez des caractères asynchronement dans une application WPF
 L’exemple suivant montre le code-behind d’une application WPF. Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau. Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)  
- [Fichier asynchrone I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Comment : Énumérer les répertoires et les fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Comment : Lire et écrire dans un fichier de données nouvellement créé](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Comment : Ouvrez et appendicez à un fichier journal](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Comment: Lire le texte d’un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Comment: Écrire du texte à un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment: Lire les personnages d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
