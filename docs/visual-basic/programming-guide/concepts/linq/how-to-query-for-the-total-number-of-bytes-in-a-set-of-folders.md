---
title: 'Procédure : rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c8e1ee66c2c9b570acd2c815bdc1ba0324380eda
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100202"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Comment : Rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)

Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers d’un dossier spécifié, ainsi que par tous ses sous-dossiers.  
  
## <a name="example"></a>Exemple  

 La méthode <xref:System.Linq.Enumerable.Sum%2A> ajoute les valeurs de tous les éléments sélectionnés dans la clause `select`. Vous pouvez facilement modifier cette requête pour récupérer le fichier le plus grand ou le plus petit de l’arborescence du répertoire spécifié en appelant la méthode <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> plutôt que <xref:System.Linq.Enumerable.Sum%2A>.  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Si vous devez seulement compter le nombre d’octets dans une arborescence de répertoires spécifiée, pour être plus efficace, ne créez pas de requête LINQ, car cela induit la surcharge liée à la création de la collection de listes comme source de données. Plus la requête est complexe, plus l’approche LINQ devient utile. C’est également valable lorsque vous devez exécuter plusieurs requêtes sur une même source de données.  
  
 La requête appelle une méthode distincte pour obtenir la longueur du fichier. Elle procède ainsi pour utiliser l’exception qui sera éventuellement levée si le fichier a été supprimé sur un autre thread après la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`. Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> avec la longueur la plus récente lors du premier accès à la propriété. En plaçant cette opération dans un bloc try-catch en dehors de la requête, le code respecte la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires. En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.  
  
## <a name="compile-the-code"></a>Compiler le code  

Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
- [LINQ et répertoires de fichiers (Visual Basic)](linq-and-file-directories.md)
