---
title: Comment combiner et comparer des collections de chaînes (LINQ) (C#)
description: Cet exemple fusionne les fichiers qui contiennent des lignes de texte. Découvrez comment effectuer une concaténation simple, une Union et une intersection sur les ensembles de lignes dans LINQ en C#.
ms.date: 07/20/2015
ms.assetid: 25926e5b-fde2-4dc1-86a0-16ead7aa13d2
ms.openlocfilehash: bfbdb9a0a3d531b56578b242c91596d9e41b6cd6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105355"
---
# <a name="how-to-combine-and-compare-string-collections-linq-c"></a><span data-ttu-id="73c2e-104">Comment combiner et comparer des collections de chaînes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="73c2e-104">How to combine and compare string collections (LINQ) (C#)</span></span>
<span data-ttu-id="73c2e-105">Cet exemple montre comment fusionner des fichiers qui contiennent des lignes de texte, puis comment trier les résultats.</span><span class="sxs-lookup"><span data-stu-id="73c2e-105">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="73c2e-106">Il montre plus précisément comment effectuer une concaténation simple, une union et une intersection avec les deux ensembles de lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="73c2e-106">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>  
  
### <a name="to-set-up-the-project-and-the-text-files"></a><span data-ttu-id="73c2e-107">Pour configurer le projet et les fichiers texte</span><span class="sxs-lookup"><span data-stu-id="73c2e-107">To set up the project and the text files</span></span>  
  
1. <span data-ttu-id="73c2e-108">Copiez ces noms dans un fichier texte nommé names1.txt, puis enregistrez-le dans votre dossier de projet :</span><span class="sxs-lookup"><span data-stu-id="73c2e-108">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="73c2e-109">Copiez ces noms dans un fichier texte nommé names2.txt, puis enregistrez-le dans votre dossier de projet :</span><span class="sxs-lookup"><span data-stu-id="73c2e-109">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="73c2e-110">Notez que les deux fichiers ont des noms en commun.</span><span class="sxs-lookup"><span data-stu-id="73c2e-110">Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="73c2e-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="73c2e-111">Example</span></span>  
  
```csharp  
class MergeStrings  
    {  
        static void Main(string[] args)  
        {  
            //Put text files in your solution folder  
            string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
            string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
            //Simple concatenation and sort. Duplicates are preserved.  
            IEnumerable<string> concatQuery =  
                fileA.Concat(fileB).OrderBy(s => s);  
  
            // Pass the query variable to another function for execution.  
            OutputQueryResults(concatQuery, "Simple concatenate and sort. Duplicates are preserved:");  
  
            // Concatenate and remove duplicate names based on  
            // default string comparer.  
            IEnumerable<string> uniqueNamesQuery =  
                fileA.Union(fileB).OrderBy(s => s);  
            OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:");  
  
            // Find the names that occur in both files (based on  
            // default string comparer).  
            IEnumerable<string> commonNamesQuery =  
                fileA.Intersect(fileB);  
            OutputQueryResults(commonNamesQuery, "Merge based on intersect:");  
  
            // Find the matching fields in each list. Merge the two
            // results by using Concat, and then  
            // sort using the default string comparer.  
            string nameMatch = "Garcia";  
  
            IEnumerable<String> tempQuery1 =  
                from name in fileA  
                let n = name.Split(',')  
                where n[0] == nameMatch  
                select name;  
  
            IEnumerable<string> tempQuery2 =  
                from name2 in fileB  
                let n2 = name2.Split(',')  
                where n2[0] == nameMatch  
                select name2;  
  
            IEnumerable<string> nameMatchQuery =  
                tempQuery1.Concat(tempQuery2).OrderBy(s => s);  
            OutputQueryResults(nameMatchQuery, $"Concat based on partial name match \"{nameMatch}\":");
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
  
        static void OutputQueryResults(IEnumerable<string> query, string message)  
        {  
            Console.WriteLine(System.Environment.NewLine + message);  
            foreach (string item in query)  
            {  
                Console.WriteLine(item);  
            }  
            Console.WriteLine("{0} total names in list", query.Count());  
        }  
    }  
    /* Output:  
        Simple concatenate and sort. Duplicates are preserved:  
        Aw, Kam Foo  
        Bankov, Peter  
        Bankov, Peter  
        Beebe, Ann  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        20 total names in list  
  
        Union removes duplicate names:  
        Aw, Kam Foo  
        Bankov, Peter  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        16 total names in list  
  
        Merge based on intersect:  
        Bankov, Peter  
        Holm, Michael  
        Garcia, Hugo  
        Beebe, Ann  
        4 total names in list  
  
        Concat based on partial name match "Garcia":  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        3 total names in list  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73c2e-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="73c2e-112">Compiling the Code</span></span>  
 <span data-ttu-id="73c2e-113">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="73c2e-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c2e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73c2e-114">See also</span></span>

- [<span data-ttu-id="73c2e-115">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="73c2e-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="73c2e-116">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="73c2e-116">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
