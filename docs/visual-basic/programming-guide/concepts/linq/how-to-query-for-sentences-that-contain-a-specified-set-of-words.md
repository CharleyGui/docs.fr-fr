---
title: 'Procédure : Rechercher des phrases qui contiennent un ensemble spécifié de mots (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: a88171d86ad820870ee72d224415d96931066abe
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593298"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="51590-102">Procédure : Rechercher des phrases qui contiennent un ensemble spécifié de mots (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51590-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="51590-103">Cet exemple montre comment rechercher dans un fichier texte les phrases qui contiennent des correspondances pour chaque ensemble de mots spécifié.</span><span class="sxs-lookup"><span data-stu-id="51590-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="51590-104">Même si le tableau des termes de recherche est codé en dur dans cet exemple, il pourrait aussi être rempli dynamiquement lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="51590-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="51590-105">Dans cet exemple, la requête retourne les phrases qui contiennent les mots « Historically », « data » et « integrated ».</span><span class="sxs-lookup"><span data-stu-id="51590-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="51590-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="51590-106">Example</span></span>  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 <span data-ttu-id="51590-107">La requête fractionne d’abord le texte en phrases, puis fractionne les phrases en tableaux de chaînes contenant chacun des mots.</span><span class="sxs-lookup"><span data-stu-id="51590-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="51590-108">Pour chacun de ces tableaux, la méthode <xref:System.Linq.Enumerable.Distinct%2A> supprime tous les mots en double, puis la requête effectue une opération <xref:System.Linq.Enumerable.Intersect%2A> sur le tableau de mots et le tableau `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="51590-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="51590-109">Si le nombre de l’intersection est identique à celui du tableau `wordsToMatch`, cela signifie que tous les mots ont été trouvés et la phrase d’origine est donc retournée.</span><span class="sxs-lookup"><span data-stu-id="51590-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="51590-110">Dans l’appel à <xref:System.String.Split%2A>, les signes de ponctuation sont utilisés comme séparateurs pour être supprimés de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="51590-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="51590-111">Si vous ne l’avez pas fait, vous pourriez avoir, par exemple, la chaîne « Historically, », qui ne correspondrait pas au mot « Historically » du tableau `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="51590-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="51590-112">Vous devrez peut-être utiliser des séparateurs supplémentaires, selon le type des signes de ponctuation qui se trouvent dans le texte source.</span><span class="sxs-lookup"><span data-stu-id="51590-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51590-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="51590-113">Compiling the Code</span></span>  
<span data-ttu-id="51590-114">Créer un projet d’application console VB.NET, avec un `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="51590-114">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51590-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51590-115">See also</span></span>

- [<span data-ttu-id="51590-116">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51590-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
