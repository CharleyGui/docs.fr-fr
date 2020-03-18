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
# <a name="how-to-read-characters-from-a-string"></a>Comment: Lire les personnages d’une chaîne
Les exemples de code suivants montrent comment lire des caractères de façon synchrone et asynchrone à partir d’une chaîne.  
  
## <a name="example-read-characters-synchronously"></a>Exemple : Lisez les personnages de façon synchrone
 Cet exemple lit 13 caractères de façon synchrone à partir d’une chaîne, les stocke dans un tableau, puis les affiche. Ensuite, l’exemple lit les caractères restants de la chaîne, les stocke dans le tableau à partir du sixième élément, puis affiche le contenu du tableau.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Exemple : Lisez les personnages asynchronement  
 L’exemple suivant montre le code-behind d’une application WPF. Au chargement de la fenêtre, l’exemple lit tous les caractères de façon asynchrone à partir d’un contrôle <xref:System.Windows.Controls.TextBox> et les stocke dans un tableau. Ensuite, il écrit de façon asynchrone chaque lettre ou espace blanc sur une ligne distincte d’un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Fichier asynchrone I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Comment : Créer une liste d’annuaire](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Comment : Lire et écrire dans un fichier de données nouvellement créé](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Comment : Ouvrez et appendicez à un fichier journal](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Comment: Lire le texte d’un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Comment: Écrire du texte à un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment: Écrire des personnages à une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)
