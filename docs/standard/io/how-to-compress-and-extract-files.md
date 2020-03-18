---
title: Guide pratique pour compresser et extraire des fichiers
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: 5aa25e265ed6ffb613e9916414c6f2335a4aaf57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159375"
---
# <a name="how-to-compress-and-extract-files"></a>Guide pratique pour compresser et extraire des fichiers

L'espace de noms <xref:System.IO.Compression> contient les types suivants pour la compression et la décompression de fichiers et de flux. Vous pouvez également utiliser ces types pour lire et modifier le contenu d’un fichier compressé.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Les exemples suivants présentent certaines des opérations que vous pouvez effectuer avec des fichiers compressés.

## <a name="example-1-create-and-extract-a-zip-file"></a>Exemple 1 : Créer et extraire un fichier .zip

L’exemple suivant montre comment créer et extraire un fichier *.zip* à l’aide de la classe <xref:System.IO.Compression.ZipFile>. Cet exemple compresse le contenu d’un dossier dans un nouveau fichier *.zip*, puis extrait ce fichier zip dans un nouveau dossier.

Pour exécuter l’exemple, créez un dossier *start* dans le dossier de votre programme, puis placez-y les fichiers à compresser.

Si vous obtenez l’erreur de build indiquant que le nom « FichierZip» n’existe pas dans le contexte actuel, ajoutez une référence à l’assembly `System.IO.Compression.FileSystem` à votre projet.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Exemple 2 : Extraire des extensions de fichiers spécifiques

L’exemple suivant montre comment parcourir le contenu d’un fichier *.zip* existant et en extraire les fichiers ayant une extension *.txt*. Il utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder au fichier zip, et la classe <xref:System.IO.Compression.ZipArchiveEntry> pour inspecter chaque entrée. La méthode d’extension <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> de l’objet <xref:System.IO.Compression.ZipArchiveEntry> est disponible dans la classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.

Pour exécuter l’exemple, placez un fichier *.zip* appelé *result.zip* dans le dossier de votre programme. Lorsque vous y êtes invité, fournissez le nom du dossier vers lequel extraire les fichiers.

Si vous obtenez l’erreur de build indiquant que le nom « FichierZip» n’existe pas dans le contexte actuel, ajoutez une référence à l’assembly `System.IO.Compression.FileSystem` à votre projet.

Si vous obtenez l’erreur indiquant que le type 'ArchiveZip' est défini dans un assembly qui n’est pas référencé, ajoutez une référence à l’assembly `System.IO.Compression` de votre projet.

> [!IMPORTANT]
> Lors de la décompression des fichiers, vous devez rechercher les chemins malveillants qui risquent d’extraire les fichiers en dehors du répertoire. Il s’agit d’une attaque par chemin transversal. L’exemple suivant montre comment rechercher les chemins malveillants et garantir une décompression sûre.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Exemple 3 : Ajouter un fichier à une fermeture éclair existante

L’exemple suivant utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder à un fichier *.zip* existant, et y ajouter un fichier. Le nouveau fichier est compressé quand vous l’ajoutez au fichier zip existant.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Exemple 4 : Fichiers Compress et décompresser .gz

Vous pouvez également utiliser les classes <xref:System.IO.Compression.GZipStream> et <xref:System.IO.Compression.DeflateStream> pour compresser et décompresser des données. Elles utilisent le même algorithme de compression. Vous pouvez décompresser les objets <xref:System.IO.Compression.GZipStream> qui sont écrits dans un fichier *.gz* à l’aide de nombreux outils courants. L’exemple suivant montre comment compresser et décompresser un répertoire de fichiers à l’aide de la classe <xref:System.IO.Compression.GZipStream> :

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)
