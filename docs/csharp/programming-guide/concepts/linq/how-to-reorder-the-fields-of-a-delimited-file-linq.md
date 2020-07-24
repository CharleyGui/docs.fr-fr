---
title: Comment réorganiser les champs d’un fichier délimité (LINQ) (C#)
description: Découvrez comment réorganiser des champs dans un fichier. csv dans LINQ en C#. L’exemple modifie les ordres des colonnes, fusionne les colonnes et trie les lignes par valeur de colonne.
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 3ebc56b418d2732a296896a19d770136a56e2fbb
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103404"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="a4a66-104">Comment réorganiser les champs d’un fichier délimité (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4a66-104">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="a4a66-105">Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte qui est souvent utilisé pour stocker des données de feuille de calcul ou autres données tabulaires qui sont représentées sous forme de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="a4a66-105">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="a4a66-106">En utilisant la méthode <xref:System.String.Split%2A> pour séparer les champs, il est très facile d’interroger et de manipuler des fichiers CSV à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="a4a66-106">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="a4a66-107">En fait, la même technique peut servir à réorganiser les sections de n’importe quelle ligne de texte structurée et ne se limite donc pas aux fichiers CSV.</span><span class="sxs-lookup"><span data-stu-id="a4a66-107">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="a4a66-108">Dans l’exemple suivant, supposons que les trois colonnes représentent le nom, le prénom et l’ID de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="a4a66-108">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="a4a66-109">Les champs sont classés par ordre alphabétique, selon le nom des étudiants.</span><span class="sxs-lookup"><span data-stu-id="a4a66-109">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="a4a66-110">La requête produit une séquence dans laquelle la colonne ID apparaît en premier, suivie d’une deuxième colonne qui comprend à la fois le prénom et le nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="a4a66-110">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="a4a66-111">Les lignes sont réorganisées d’après le champ ID.</span><span class="sxs-lookup"><span data-stu-id="a4a66-111">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="a4a66-112">Les résultats sont enregistrés dans un nouveau fichier et les données d’origine ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="a4a66-112">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="a4a66-113">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="a4a66-113">To create the data file</span></span>  
  
1. <span data-ttu-id="a4a66-114">Copiez les lignes suivantes dans un fichier texte nommé spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="a4a66-114">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="a4a66-115">Enregistrez le fichier dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="a4a66-115">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a4a66-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4a66-116">Example</span></span>  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4a66-117">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a4a66-117">Compiling the Code</span></span>  
<span data-ttu-id="a4a66-118">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="a4a66-118">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a4a66-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4a66-119">See also</span></span>

- [<span data-ttu-id="a4a66-120">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="a4a66-120">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="a4a66-121">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="a4a66-121">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="a4a66-122">Comment générer du code XML à partir de fichiers CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="a4a66-122">How to generate XML from CSV files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
