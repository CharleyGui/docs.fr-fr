---
title: Comment compter les occurrences d’un mot dans une chaîne (LINQ) (C#)
description: Cet exemple utilise une requête LINQ en C# pour compter les occurrences d’un mot spécifié dans une chaîne. Elle utilise la méthode Split pour créer un tableau de mots.
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: b354947c59747e49b5f3d099ebc3ea891fb4af90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159070"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="4adfa-104">Comment compter les occurrences d’un mot dans une chaîne (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4adfa-104">How to count occurrences of a word in a string (LINQ) (C#)</span></span>

<span data-ttu-id="4adfa-105">Cet exemple montre comment utiliser une requête LINQ pour compter les occurrences d’un mot spécifié dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4adfa-105">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="4adfa-106">Notez que, pour effectuer le décompte, la méthode <xref:System.String.Split%2A> est d’abord appelée pour créer un tableau de mots.</span><span class="sxs-lookup"><span data-stu-id="4adfa-106">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="4adfa-107">La méthode <xref:System.String.Split%2A> a un coût en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="4adfa-107">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="4adfa-108">Si la seule opération sur la chaîne consiste à compter les mots, il est préférable d’utiliser les méthodes <xref:System.Text.RegularExpressions.Regex.Matches%2A> ou <xref:System.String.IndexOf%2A>.</span><span class="sxs-lookup"><span data-stu-id="4adfa-108">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="4adfa-109">Toutefois, si les performances ne sont pas un facteur critique, ou si vous avez déjà fractionné la phrase pour effectuer d’autres types de requêtes sur elle, il est judicieux d’utiliser LINQ pour compter les mots ou les expressions.</span><span class="sxs-lookup"><span data-stu-id="4adfa-109">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4adfa-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="4adfa-110">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4adfa-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4adfa-111">Compiling the Code</span></span>  

 <span data-ttu-id="4adfa-112">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="4adfa-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adfa-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4adfa-113">See also</span></span>

- [<span data-ttu-id="4adfa-114">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="4adfa-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
