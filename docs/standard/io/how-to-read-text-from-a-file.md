---
title: 'Comment: Lire le texte d’un fichier'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155722"
---
# <a name="how-to-read-text-from-a-file"></a>Comment: Lire le texte d’un fichier
Les exemples suivants montrent comment lire le texte de façon synchrone et asynchrone à partir d'un fichier texte à l'aide du .NET pour les applications de bureau. Dans les deux exemples, lorsque vous créez l’instance de la classe <xref:System.IO.StreamReader>, vous fournissez le chemin d’accès relatif ou absolu au fichier.
  
> [!NOTE]
> Ces exemples de code ne s’appliquent pas au développement d’applications UWP, car le Windows Runtime fournit des types de flux différents pour la lecture et l’écriture des fichiers. Pour un exemple qui montre comment lire le texte d’un fichier dans une application UWP, voir [Quickstart: Lecture et rédaction de fichiers](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Pour des exemples qui montrent comment convertir entre les flux .NET Framework et les flux Windows Runtime, voir [Comment: Convertir entre les flux cadre .NET et les flux Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Exemple : Synchronous lu dans une application de console  
L’exemple suivant montre une opération de lecture synchrone dans une application console. Cet exemple ouvre le fichier texte à l’aide d’un lecteur de flux, copie le contenu dans une chaîne, puis retourne une chaîne dans la console.  
  
> [!IMPORTANT]
> L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Exemple : Asynchrone lu dans une application WPF
 L’exemple suivant montre une opération de lecture asynchrone dans une application WPF (Windows Presentation Foundation).  
  
> [!IMPORTANT]
> L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Fichier asynchrone I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Comment : Créer une liste d’annuaire](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Démarrage rapide : lire et écrire dans des fichiers](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Comment : Convertir entre les flux cadre .NET et les flux Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Comment : Lire et écrire dans un fichier de données nouvellement créé](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Comment : Ouvrez et appendicez à un fichier journal](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Comment: Écrire du texte à un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment: Lire les personnages d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Comment: Écrire des personnages à une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)
