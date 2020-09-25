---
title: Comment interroger des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)
description: Découvrez comment utiliser LINQ en C# pour rechercher des phrases dans un fichier texte qui contiennent des correspondances pour chacun d’un ensemble de mots, qui peut être rempli au moment de l’exécution.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 7c5979fc42b6446948ae974e599807b5cb8db04a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176277"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="02833-103">Comment interroger des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="02833-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>

<span data-ttu-id="02833-104">Cet exemple montre comment rechercher dans un fichier texte les phrases qui contiennent des correspondances pour chaque ensemble de mots spécifié.</span><span class="sxs-lookup"><span data-stu-id="02833-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="02833-105">Même si le tableau des termes de recherche est codé en dur dans cet exemple, il pourrait aussi être rempli dynamiquement lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="02833-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="02833-106">Dans cet exemple, la requête retourne les phrases qui contiennent les mots « Historically », « data » et « integrated ».</span><span class="sxs-lookup"><span data-stu-id="02833-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="02833-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="02833-107">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="02833-108">La requête fractionne d’abord le texte en phrases, puis fractionne les phrases en tableaux de chaînes contenant chacun des mots.</span><span class="sxs-lookup"><span data-stu-id="02833-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="02833-109">Pour chacun de ces tableaux, la méthode <xref:System.Linq.Enumerable.Distinct%2A> supprime tous les mots en double, puis la requête effectue une opération <xref:System.Linq.Enumerable.Intersect%2A> sur le tableau de mots et le tableau `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="02833-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="02833-110">Si le nombre de l’intersection est identique à celui du tableau `wordsToMatch`, cela signifie que tous les mots ont été trouvés et la phrase d’origine est donc retournée.</span><span class="sxs-lookup"><span data-stu-id="02833-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="02833-111">Dans l’appel à <xref:System.String.Split%2A>, les signes de ponctuation sont utilisés comme séparateurs pour être supprimés de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="02833-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="02833-112">Si vous ne l’avez pas fait, vous pourriez avoir, par exemple, la chaîne « Historically, », qui ne correspondrait pas au mot « Historically » du tableau `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="02833-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="02833-113">Vous devrez peut-être utiliser des séparateurs supplémentaires, selon le type des signes de ponctuation qui se trouvent dans le texte source.</span><span class="sxs-lookup"><span data-stu-id="02833-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02833-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="02833-114">Compiling the Code</span></span>  

<span data-ttu-id="02833-115">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="02833-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="02833-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02833-116">See also</span></span>

- [<span data-ttu-id="02833-117">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="02833-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
