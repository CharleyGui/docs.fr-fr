---
title: 'Procédure : ouvrir un fichier journal et y ajouter des éléments'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155709"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Procédure : ouvrir un fichier journal et y ajouter des éléments
<xref:System.IO.StreamWriter> et <xref:System.IO.StreamReader> écrivent des caractères dans et lisent des caractères à partir des flux. L’exemple de code suivant ouvre le fichier *log.txt* pour l’entrée, ou crée le fichier s’il n’existe pas déjà, puis ajoute les informations à la fin du fichier. Ensuite, l’exemple écrit le contenu du fichier dans la sortie standard en vue de son affichage.

Comme alternative à cet exemple, vous pourriez stocker les informations dans une chaîne ou un tableau de chaînes, puis utiliser la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ou <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> pour obtenir la même fonctionnalité.  
  
> [!NOTE]
> Les utilisateurs Visual Basic peuvent choisir d’utiliser les méthodes et les propriétés fournies par la classe <xref:Microsoft.VisualBasic.Logging.Log> ou la classe <xref:Microsoft.VisualBasic.FileIO.FileSystem> pour la création ou l’écriture dans des fichiers journaux.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Comment : lire et écrire dans un fichier de données nouvellement créé](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Comment : lire du texte à partir d’un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment : lire les caractères d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
