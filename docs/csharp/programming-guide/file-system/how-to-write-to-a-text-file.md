---
title: 'Procédure : Écrire dans un fichier texte - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: e3fa0eb12c9259629ff8151ff2d057f2744e9e36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595629"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Procédure : Écrire dans un fichier texte (Guide de programmation C#)
Ces exemples montrent différentes manières d'écrire du texte dans un fichier. Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout `IEnumerable<string>` et une chaîne dans un fichier texte. L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier. Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.  
  
 Ces exemples écrivent tous des littéraux de chaîne dans des fichiers. Pour mettre en forme le texte écrit dans un fichier, utilisez la méthode <xref:System.String.Format%2A> ou la fonctionnalité d’[interpolation de chaîne](../../../csharp/language-reference/tokens/interpolated.md) C#.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier existe déjà et est en lecture seule.  
  
- Le nom du chemin d'accès peut s'avérer trop long.  
  
- Le disque est peut-être plein.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
- [Exemple : Enregistrer une collection sur un emplacement de stockage d’application](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
