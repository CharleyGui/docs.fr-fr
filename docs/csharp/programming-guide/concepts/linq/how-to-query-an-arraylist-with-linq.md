---
title: Comment interroger un ArrayList avec LINQ (C#)
description: Cet exemple utilise LINQ pour interroger une ArrayList en C#. Vous devez déclarer le type de la variable de portée pour refléter le type des objets dans la collection.
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 5c251e17de062a4578f06fc1a40ea3ede9f3ab67
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104605"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="6c2aa-104">Comment interroger un ArrayList avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="6c2aa-104">How to query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="6c2aa-105">Quand vous utilisez LINQ pour interroger des collections <xref:System.Collections.IEnumerable> non génériques telles que <xref:System.Collections.ArrayList>, vous devez déclarer explicitement le type de la variable de portée pour qu’il reflète le type spécifique des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-105">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="6c2aa-106">Par exemple, si vous avez un <xref:System.Collections.ArrayList> d’objets `Student`, votre [clause from](../../../language-reference/keywords/from-clause.md) doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="6c2aa-106">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="6c2aa-107">En spécifiant le type de la variable de portée, vous effectuez un cast de chaque élément du `Student` en <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-107">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="6c2aa-108">L’utilisation d’une variable de portée explicitement typée dans une expression de requête équivaut à appeler la méthode <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-108">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="6c2aa-109"><xref:System.Linq.Enumerable.Cast%2A> lève une exception si le cast spécifié ne peut pas être effectué.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-109"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="6c2aa-110"><xref:System.Linq.Enumerable.Cast%2A> et <xref:System.Linq.Enumerable.OfType%2A> sont les deux méthodes d’opérateur de requête standard qui fonctionnent sur les types <xref:System.Collections.IEnumerable> non génériques.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-110"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="6c2aa-111">Pour plus d’informations, consultez [relations de types dans les opérations de requête LINQ](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6c2aa-111">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c2aa-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c2aa-112">Example</span></span>  
 <span data-ttu-id="6c2aa-113">L’exemple suivant montre une requête simple sur un <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="6c2aa-114">Notez que cet exemple utilise des initialiseurs d’objets quand le code appelle la méthode <xref:System.Collections.ArrayList.Add%2A>, mais cela n’est pas une obligation.</span><span class="sxs-lookup"><span data-stu-id="6c2aa-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c2aa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c2aa-115">See also</span></span>

- [<span data-ttu-id="6c2aa-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="6c2aa-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
