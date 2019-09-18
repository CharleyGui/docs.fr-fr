---
title: 'Procédure : lire des fichiers texte dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 26e6d8f9cc64f0f1238afaaf6aaf85d69f6c32ce
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039432"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Procédure : lire des fichiers texte dans Visual Basic

La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> de l'objet `My.Computer.FileSystem` vous permet de lire un fichier texte. L'encodage du fichier peut être spécifié si le contenu de ce dernier utilise l'encodage ASCII ou UTF-8.

Si vous lisez un fichier avec des caractères étendus, vous devez spécifier son encodage.

> [!NOTE]
> Pour lire un fichier, une ligne de texte à la fois, utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> de l'objet `My.Computer.FileSystem`. La méthode `OpenTextFileReader` retourne un objet <xref:System.IO.StreamReader>. Vous pouvez utiliser la méthode <xref:System.IO.StreamReader.ReadLine%2A> de l"objet `StreamReader` pour lire un fichier une ligne à la fois. Vous pouvez tester la fin du fichier à l'aide de la méthode <xref:System.IO.StreamReader.EndOfStream%2A> de l'objet `StreamReader`.

## <a name="to-read-from-a-text-file"></a>Pour lire un fichier texte

Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès. L'exemple suivant lit le contenu du fichier test.txt dans une chaîne puis l'affiche dans un message.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Pour lire un fichier texte encodé

Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès et le type d'encodage du fichier. L'exemple suivant lit le contenu du fichier UTF32 test.txt dans une chaîne puis l'affiche dans un message.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Programmation fiable

Les conditions ci-dessous peuvent générer une exception.

- Le chemin d'accès n'est pas valide pour une des raisons suivantes : il s'agit d'une chaîne de longueur nulle ; il ne contient que des espaces blancs ; il contient des caractères non valides ou il s'agit d'un chemin d'accès de périphérique (<xref:System.ArgumentException>).

- Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).

- Le fichier n'existe pas (<xref:System.IO.FileNotFoundException>).

- Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).

- Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).

- Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).

- Il n'y a pas assez de mémoire pour écrire la chaîne dans la mémoire tampon (<xref:System.OutOfMemoryException>).

- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).

Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.

Vérifiez toutes les entrées avant d'utiliser les données dans votre application. Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Lecture à partir de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Guide pratique pour lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Guide pratique pour lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Résolution des problèmes : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Procédure pas à pas : Manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Codages de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
