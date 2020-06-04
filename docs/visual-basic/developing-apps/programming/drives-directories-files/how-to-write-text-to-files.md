---
title: 'Procédure : écrire du texte dans des fichiers'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f95a0c4df4a2eab0069a6dab0d4c3fa338d1d8ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411536"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Guide pratique pour écrire du texte dans des fichiers en Visual Basic

Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pour écrire du texte dans des fichiers. Si le fichier spécifié n’existe pas, il est créé.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-write-text-to-a-file"></a>Pour écrire du texte dans un fichier  
  
- Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier et le texte à écrire. Cet exemple écrit la ligne `"This is new text."` dans le fichier nommé `test.txt`. Le texte est ajouté au texte existant dans le fichier.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Pour écrire une série de chaînes dans un fichier  
  
- Parcourez la collection de chaînes. Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier cible et la chaîne à ajouter, puis en affectant la valeur `True` au paramètre `append`.  
  
     Cet exemple écrit les noms des fichiers dans le répertoire `Documents and Settings` dans `FileList.txt`, et insère un retour chariot entre chacun d’eux pour une meilleure lisibilité.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
- Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).  
  
- Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).  
  
- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
- Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).  
  
- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
- Le disque est plein et l’appel à `WriteAllText` échoue (<xref:System.IO.IOException>).  
  
 Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Comment : lire des fichiers texte](how-to-read-from-text-files.md)
