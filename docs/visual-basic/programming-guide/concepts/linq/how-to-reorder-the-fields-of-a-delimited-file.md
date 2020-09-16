---
title: 'Procédure : réorganiser les champs d’un fichier délimité (LINQ)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 62c21dfb67ef35591a8ffe214bc132e63a2433bd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535382"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic)

Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte qui est souvent utilisé pour stocker des données de feuille de calcul ou autres données tabulaires qui sont représentées sous forme de lignes et de colonnes. En utilisant la méthode <xref:System.String.Split%2A> pour séparer les champs, il est très facile d’interroger et de manipuler des fichiers CSV à l’aide de LINQ. En fait, la même technique peut servir à réorganiser les sections de n’importe quelle ligne de texte structurée et ne se limite donc pas aux fichiers CSV.

Dans l’exemple suivant, supposons que les trois colonnes représentent le nom, le prénom et l’ID de l’étudiant. Les champs sont classés par ordre alphabétique, selon le nom des étudiants. La requête produit une séquence dans laquelle la colonne ID apparaît en premier, suivie d’une deuxième colonne qui comprend à la fois le prénom et le nom de l’étudiant. Les lignes sont réorganisées d’après le champ ID. Les résultats sont enregistrés dans un nouveau fichier et les données d’origine ne sont pas modifiées.

### <a name="to-create-the-data-file"></a>Pour créer le fichier de données

1. Copiez les lignes suivantes dans un fichier texte nommé spreadsheet1.csv. Enregistrez le fichier dans votre dossier de projet.

    ```csv
    Adams,Terry,120
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Cesar,114
    Garcia,Debra,115
    Garcia,Hugo,118
    Mortensen,Sven,113
    O'Donnell,Claire,112
    Omelchenko,Svetlana,111
    Tucker,Lance,119
    Tucker,Michael,122
    Zabokritski,Eugene,121
    ```

## <a name="example"></a>Exemple

```vb
Class CSVFiles

    Shared Sub Main()

        ' Create the IEnumerable data source.
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")

        ' Execute the query. Put field 2 first, then
        ' reverse and combine fields 0 and 1 from the old field
        Dim lineQuery = From line In lines
                        Let x = line.Split(New Char() {","})
                        Order By x(2)
                        Select x(2) & ", " & (x(1) & " " & x(0))

        ' Execute the query and write out the new file. Note that WriteAllLines
        ' takes a string array, so ToArray is called on the query.
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())

        ' Keep console window open in debug mode.
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output to spreadsheet2.csv:
' 111, Svetlana Omelchenko
' 112, Claire O'Donnell
' 113, Sven Mortensen
' 114, Cesar Garcia
' 115, Debra Garcia
' 116, Fadi Fakhouri
' 117, Hanying Feng
' 118, Hugo Garcia
' 119, Lance Tucker
' 120, Terry Adams
' 121, Eugene Zabokritski
' 122, Michael Tucker
```

## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (Visual Basic)](linq-and-strings.md)
- [LINQ et répertoires de fichiers (Visual Basic)](linq-and-file-directories.md)
- [Comment : générer du code XML à partir de fichiers CSV](../../../../standard/linq/generate-xml-csv-files.md)
