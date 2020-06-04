---
title: 'Procédure : rechercher la différence ensembliste entre deux listes (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: f533b63b40325b34c5881c1e2f14aa4e576191c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396595"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Comment : Rechercher la différence définie entre deux listes (LINQ) (Visual Basic)
Cet exemple montre comment utiliser LINQ pour comparer deux listes de chaînes et sortir les lignes qui sont présentes dans names1.txt, mais pas dans names2.txt.  
  
### <a name="to-create-the-data-files"></a>Pour créer le fichier de données  
  
1. Copiez names1. txt et names2. txt dans votre dossier de solution, comme indiqué dans [Comment : combiner et comparer des collections de chaînes (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Exemple  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Certains types d’opérations de requête dans Visual Basic, tels que <xref:System.Linq.Enumerable.Except%2A> ,, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Concat%2A> , peuvent uniquement être exprimés dans une syntaxe basée sur une méthode.  
  
## <a name="compile-the-code"></a>Compiler le code  
Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.
  
## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (Visual Basic)](linq-and-strings.md)
