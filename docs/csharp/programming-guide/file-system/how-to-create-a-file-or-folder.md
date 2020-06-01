---
title: Guide de création d’un fichier ou d’un dossier-Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 5efe3b7dc600645488816d6f931df57fc236efc9
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241641"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Comment créer un fichier ou un dossier (Guide de programmation C#)
Vous pouvez par programmationcréer un dossier sur votre ordinateur, créer un sous-dossier, créer un fichier dans le sous-dossier et écrire des données dans le fichier.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Si le dossier existe déjà, <xref:System.IO.Directory.CreateDirectory%2A> est sans effet et aucune exception n’est levée. Toutefois, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> remplace un fichier existant par un nouveau fichier. L’exemple utilise une instruction `if`-`else` pour éviter qu’un fichier existant soit pas remplacé.  
  
 En apportant les modifications suivantes dans l’exemple, vous pouvez spécifier des résultats différents si un fichier avec un nom spécifique existe déjà. Si un tel fichier n’existe pas, le code en crée un. Si un tel fichier existe, le code ajoute des données à ce fichier.  
  
- Spécifiez un nom de fichier non aléatoire.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Remplacez l’instruction `if`-`else` par l’instruction `using` dans le code suivant.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Exécutez l’exemple plusieurs fois pour vérifier que les données sont ajoutées au fichier à chaque fois.  
  
 Pour découvrir d’autres valeurs `FileMode` que vous pouvez essayer, consultez <xref:System.IO.FileMode>.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le nom du dossier est mal formé. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (classe <xref:System.ArgumentException>). Utilisez la classe <xref:System.IO.Path> pour créer des noms de chemin valides.  
  
- Le dossier parent du dossier à créer est en lecture seule (classe <xref:System.IO.IOException>).  
  
- Le nom du dossier est `null` (classe <xref:System.ArgumentNullException>).  
  
- Le nom du dossier est trop long (classe <xref:System.IO.PathTooLongException>).  
  
- Le nom du dossier est uniquement un signe deux-points, « : » (classe <xref:System.IO.PathTooLongException>).  
  
## <a name="net-security"></a>Sécurité .NET  
 Une instance de la classe <xref:System.Security.SecurityException> peut être levée dans les situations de confiance partielle.  
  
 Si vous n’êtes pas autorisé à créer le dossier, l’exemple lève une instance de la <xref:System.UnauthorizedAccessException> classe.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](./index.md)
