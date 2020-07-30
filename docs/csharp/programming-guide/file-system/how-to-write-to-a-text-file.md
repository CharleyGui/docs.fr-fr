---
title: Comment écrire dans un fichier texte-Guide de programmation C#
description: Découvrez comment écrire un fichier texte avec C#. Consultez plusieurs exemples de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301643"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Comment écrire dans un fichier texte (Guide de programmation C#)
Ces exemples montrent différentes manières d'écrire du texte dans un fichier. Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout `IEnumerable<string>` et une chaîne dans un fichier texte. L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier. Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.  
  
 Ces exemples écrivent tous des littéraux de chaîne dans des fichiers. Pour mettre en forme le texte écrit dans un fichier, utilisez la méthode <xref:System.String.Format%2A> ou la fonctionnalité d’[interpolation de chaîne](../../language-reference/tokens/interpolated.md) C#.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier existe déjà et est en lecture seule.  
  
- Le nom du chemin d'accès peut s'avérer trop long.  
  
- Le disque est peut-être plein.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](./index.md)
- [Exemple : Enregistrer une collection sur un emplacement de stockage d’application](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
