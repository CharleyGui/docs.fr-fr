---
title: 'Procédure : Nombre des Occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: 2292b0b943eefb5e837256f273db73699de30a2d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593218"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Procédure : Nombre des Occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)
Cet exemple montre comment utiliser une requête LINQ pour compter les occurrences d’un mot spécifié dans une chaîne. Notez que, pour effectuer le décompte, la méthode <xref:System.String.Split%2A> est d’abord appelée pour créer un tableau de mots. La méthode <xref:System.String.Split%2A> a un coût en matière de performances. Si la seule opération sur la chaîne consiste à compter les mots, il est préférable d’utiliser les méthodes <xref:System.Text.RegularExpressions.Regex.Matches%2A> ou <xref:System.String.IndexOf%2A>. Toutefois, si les performances ne sont pas un facteur critique, ou si vous avez déjà fractionné la phrase pour effectuer d’autres types de requêtes sur elle, il est judicieux d’utiliser LINQ pour compter les mots ou les expressions.  
  
## <a name="example"></a>Exemple  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
Créer un projet d’application console VB.NET, avec un `Imports` instruction pour l’espace de noms System.Linq.
  
## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
