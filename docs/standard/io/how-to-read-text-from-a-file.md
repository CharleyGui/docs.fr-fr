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
# <a name="how-to-read-text-from-a-file"></a>Comment : lire du texte à partir d’un fichier

Les exemples suivants montrent comment lire le texte de façon synchrone et asynchrone à partir d'un fichier texte à l'aide du .NET pour les applications de bureau. Dans les deux exemples, lorsque vous créez l’instance de la classe <xref:System.IO.StreamReader>, vous fournissez le chemin d’accès relatif ou absolu au fichier.
  
> [!NOTE]
> Ces exemples de code ne s’appliquent pas aux applications Windows universelles, car le Windows Runtime fournit différents types de flux pour la lecture et l’écriture dans des fichiers. Pour obtenir un exemple qui montre comment lire le texte d’un fichier dans une application UWP, consultez [démarrage rapide : lecture et écriture de fichiers](/previous-versions/windows/apps/hh758325(v=win.10)). Pour obtenir des exemples qui montrent comment effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime, consultez [Comment : effectuer une conversion entre des flux de .NET Framework et des](how-to-convert-between-dotnet-streams-and-winrt-streams.md)flux de Windows Runtime.  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Exemple : lecture synchrone dans une application console  
L’exemple suivant montre une opération de lecture synchrone dans une application console. Cet exemple ouvre le fichier texte à l’aide d’un lecteur de flux, copie le contenu dans une chaîne, puis retourne une chaîne dans la console.  
  
> [!IMPORTANT]
> L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Exemple : lecture asynchrone dans une application WPF
 L’exemple suivant montre une opération de lecture asynchrone dans une application WPF (Windows Presentation Foundation).  
  
> [!IMPORTANT]
> L’exemple suppose qu’un fichier nommé *TestFile.txt* existe déjà dans le dossier où se trouve l’application.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [E/S sur fichier asynchrones](asynchronous-file-i-o.md)  
- [Procédure : créer une liste de répertoires](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Démarrage rapide : lire et écrire dans des fichiers](/previous-versions/windows/apps/hh758325(v=win.10))  
- [Comment : effectuer une conversion entre des flux de .NET Framework et des flux de Windows Runtime](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Comment : lire et écrire dans un fichier de données nouvellement créé](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Procédure : ouvrir un fichier journal et y ajouter des éléments](how-to-open-and-append-to-a-log-file.md)  
- [Comment : écrire du texte dans un fichier](how-to-write-text-to-a-file.md)  
- [Comment : lire les caractères d’une chaîne](how-to-read-characters-from-a-string.md)  
- [Comment : écrire des caractères dans une chaîne](how-to-write-characters-to-a-string.md)  
- [E/s de fichier et de flux](index.md)
