---
title: Comment réorganiser les champs d’un fichier délimité (LINQ) (C#)
description: Découvrez comment réorganiser des champs dans un fichier. csv dans LINQ en C#. L’exemple modifie les ordres des colonnes, fusionne les colonnes et trie les lignes par valeur de colonne.
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: a3bbc2690ded24629b313b24ee7a604bcacce850
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547295"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="b0ba5-104">Comment réorganiser les champs d’un fichier délimité (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ba5-104">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="b0ba5-105">Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte qui est souvent utilisé pour stocker des données de feuille de calcul ou autres données tabulaires qui sont représentées sous forme de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-105">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="b0ba5-106">En utilisant la méthode <xref:System.String.Split%2A> pour séparer les champs, il est très facile d’interroger et de manipuler des fichiers CSV à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-106">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="b0ba5-107">En fait, la même technique peut servir à réorganiser les sections de n’importe quelle ligne de texte structurée et ne se limite donc pas aux fichiers CSV.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-107">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="b0ba5-108">Dans l’exemple suivant, supposons que les trois colonnes représentent le nom, le prénom et l’ID de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-108">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="b0ba5-109">Les champs sont classés par ordre alphabétique, selon le nom des étudiants.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-109">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="b0ba5-110">La requête produit une séquence dans laquelle la colonne ID apparaît en premier, suivie d’une deuxième colonne qui comprend à la fois le prénom et le nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-110">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="b0ba5-111">Les lignes sont réorganisées d’après le champ ID.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-111">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="b0ba5-112">Les résultats sont enregistrés dans un nouveau fichier et les données d’origine ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-112">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="b0ba5-113">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="b0ba5-113">To create the data file</span></span>  
  
1. <span data-ttu-id="b0ba5-114">Copiez les lignes suivantes dans un fichier texte nommé spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-114">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="b0ba5-115">Enregistrez le fichier dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-115">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b0ba5-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b0ba5-116">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0ba5-117">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b0ba5-117">Compiling the Code</span></span>  
<span data-ttu-id="b0ba5-118">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="b0ba5-118">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b0ba5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ba5-119">See also</span></span>

- [<span data-ttu-id="b0ba5-120">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ba5-120">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="b0ba5-121">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ba5-121">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="b0ba5-122">Comment générer du code XML à partir de fichiers CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ba5-122">How to generate XML from CSV files (C#)</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
