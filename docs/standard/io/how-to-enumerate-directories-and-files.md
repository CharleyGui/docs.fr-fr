---
title: 'Comment : énumérer des répertoires et des fichiers'
description: Apprenez à énumérer des répertoires et des fichiers à l’aide de collections énumérables, qui peuvent fournir de meilleures performances que les tableaux dans .NET.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 7a757fc97fd934f02592264c3a495c3efc435fd5
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187890"
---
# <a name="how-to-enumerate-directories-and-files"></a>Comment : énumérer des répertoires et des fichiers
Les collections énumérables offrent de meilleures performances que les tableaux lorsque vous travaillez avec collections volumineuses de fichiers et de répertoires. Pour énumérer des répertoires et des fichiers, utilisez des méthodes qui retournent une collection énumérable de noms de répertoire ou de fichier ou leurs objets <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> ou <xref:System.IO.FileSystemInfo>.  
  
Si vous souhaitez parcourir et retourner uniquement les noms des répertoires ou des fichiers, utilisez les méthodes d’énumération de la classe <xref:System.IO.Directory>. Si vous souhaitez parcourir et retourner d’autres propriétés des répertoires ou des fichiers, utilisez les classes <xref:System.IO.DirectoryInfo> et <xref:System.IO.FileSystemInfo>.  
  
Vous pouvez utiliser les collections énumérables issues de ces méthodes en tant que paramètre <xref:System.Collections.Generic.IEnumerable%601> pour les constructeurs de classes de collection, comme <xref:System.Collections.Generic.List%601>.  
  
Le tableau suivant récapitule les méthodes qui retournent des collections énumérables de fichiers et de répertoires .  
  
|Pour parcourir et retourner|Utiliser la méthode|  
|------------------|-------------------------------------|-------------------|  
|Noms de répertoires|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informations sur le répertoire (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Noms de fichiers|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informations sur le fichier (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Noms d’entrée de système de fichiers|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informations sur les entrées de système de fichiers (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Noms de répertoires et de fichiers |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Bien que vous puissiez énumérer immédiatement tous les fichiers dans les sous-répertoires d’un répertoire parent à l’aide de l’option <xref:System.IO.SearchOption.AllDirectories> de l’énumération <xref:System.IO.SearchOption> facultative, des erreurs <xref:System.UnauthorizedAccessException> peuvent rendre l’énumération incomplète. Vous pouvez intercepter ces exceptions en énumérant d’abord les répertoires, puis les fichiers.  
  
## <a name="examples-use-the-directory-class"></a>Exemples : utiliser la classe Directory  
  
L’exemple suivant utilise la méthode <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> pour obtenir une liste des noms de répertoires de niveau supérieur dans un chemin spécifié.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

L’exemple suivant utilise la méthode <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> pour énumérer de manière récursive tous les noms de fichiers dans un répertoire et dans les sous-répertoires qui correspondent à un certain modèle. Il lit chaque ligne de chaque fichier et affiche les lignes qui contiennent la chaîne spécifiée, avec les noms de fichiers et chemins correspondants.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Exemples : utiliser la classe DirectoryInfo  
  
L’exemple suivant utilise la méthode <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> pour lister une collection de répertoires de niveau supérieur dont <xref:System.IO.FileSystemInfo.CreationTimeUtc> est antérieur à une certaine valeur <xref:System.DateTime>.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
L’exemple suivant utilise la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> pour lister tous les fichiers dont <xref:System.IO.FileInfo.Length> dépasse 10 Mo. Cet exemple énumère d’abord les répertoires de niveau supérieur, pour intercepter les éventuelles exceptions d’accès non autorisé, puis énumère les fichiers.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [E/s de fichier et de flux](index.md)
