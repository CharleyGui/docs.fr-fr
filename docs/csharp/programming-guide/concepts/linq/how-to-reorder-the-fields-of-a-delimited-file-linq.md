---
title: Comment réorganiser les champs d’un fichier délimité (LINQ) (C)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 6bc502ff12a908edf43f9ff7f5f63f98c3ff29c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347652"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="c59e2-102">Comment réorganiser les champs d’un fichier délimité (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="c59e2-102">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="c59e2-103">Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte qui est souvent utilisé pour stocker des données de feuille de calcul ou autres données tabulaires qui sont représentées sous forme de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="c59e2-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="c59e2-104">En utilisant la méthode <xref:System.String.Split%2A> pour séparer les champs, il est très facile d’interroger et de manipuler des fichiers CSV à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="c59e2-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="c59e2-105">En fait, la même technique peut servir à réorganiser les sections de n’importe quelle ligne de texte structurée et ne se limite donc pas aux fichiers CSV.</span><span class="sxs-lookup"><span data-stu-id="c59e2-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="c59e2-106">Dans l’exemple suivant, supposons que les trois colonnes représentent le nom, le prénom et l’ID de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="c59e2-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="c59e2-107">Les champs sont classés par ordre alphabétique, selon le nom des étudiants.</span><span class="sxs-lookup"><span data-stu-id="c59e2-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="c59e2-108">La requête produit une séquence dans laquelle la colonne ID apparaît en premier, suivie d’une deuxième colonne qui comprend à la fois le prénom et le nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="c59e2-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="c59e2-109">Les lignes sont réorganisées d’après le champ ID.</span><span class="sxs-lookup"><span data-stu-id="c59e2-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="c59e2-110">Les résultats sont enregistrés dans un nouveau fichier et les données d’origine ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="c59e2-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="c59e2-111">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="c59e2-111">To create the data file</span></span>  
  
1. <span data-ttu-id="c59e2-112">Copiez les lignes suivantes dans un fichier texte nommé spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="c59e2-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="c59e2-113">Enregistrez le fichier dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="c59e2-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c59e2-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c59e2-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c59e2-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c59e2-115">Compiling the Code</span></span>  
<span data-ttu-id="c59e2-116">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="c59e2-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c59e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c59e2-117">See also</span></span>

- [<span data-ttu-id="c59e2-118">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="c59e2-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="c59e2-119">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="c59e2-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="c59e2-120">Comment générer XML à partir de fichiers CSV (C)</span><span class="sxs-lookup"><span data-stu-id="c59e2-120">How to generate XML from CSV files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
