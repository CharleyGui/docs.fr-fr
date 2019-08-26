---
title: 'Procédure : interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: fb0fb118eaabbd9d66c5c4a445b0393a69dd2355
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592913"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a><span data-ttu-id="e36cb-102">Procédure : interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e36cb-102">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>

<span data-ttu-id="e36cb-103">Vous pouvez utiliser les API de réflexion de la bibliothèque de classes .NET Framework pour examiner les métadonnées dans un assembly .NET et pour créer des collections de types, de membres de type, de paramètres, etc., qui se trouvent dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="e36cb-103">The .NET Framework class library reflection APIs can be used to examine the metadata in a .NET assembly and create collections of types, type members, parameters, and so on that are in that assembly.</span></span> <span data-ttu-id="e36cb-104">Comme ces collections prennent en charge l’interface générique <xref:System.Collections.Generic.IEnumerable%601>, elles peuvent être interrogées à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="e36cb-104">Because these collections support the generic <xref:System.Collections.Generic.IEnumerable%601> interface, they can be queried by using LINQ.</span></span>  
  
<span data-ttu-id="e36cb-105">L’exemple suivant montre comment utiliser LINQ avec la réflexion pour récupérer des métadonnées spécifiques concernant des méthodes qui correspondent à un critère de recherche spécifié.</span><span class="sxs-lookup"><span data-stu-id="e36cb-105">The following example shows how LINQ can be used with reflection to retrieve specific metadata about methods that match a specified search criterion.</span></span> <span data-ttu-id="e36cb-106">Ici, la requête va rechercher les noms de toutes les méthodes dans l’assembly qui retournent des types énumérables tels que des tableaux.</span><span class="sxs-lookup"><span data-stu-id="e36cb-106">In this case, the query will find the names of all the methods in the assembly that return enumerable types such as arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e36cb-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="e36cb-107">Example</span></span>  
  
```csharp  
using System;
using System.Linq;
using System.Reflection;  

class ReflectionHowTO  
{  
    static void Main()  
    {  
        Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
        var pubTypesQuery = from type in assembly.GetTypes()  
                    where type.IsPublic  
                        from method in type.GetMethods()  
                        where method.ReturnType.IsArray == true 
                            || ( method.ReturnType.GetInterface(  
                                typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                            && method.ReturnType.FullName != "System.String" )  
                        group method.ToString() by type.ToString();  

        foreach (var groupOfMethods in pubTypesQuery)  
        {  
            Console.WriteLine("Type: {0}", groupOfMethods.Key);  
            foreach (var method in groupOfMethods)  
            {  
                Console.WriteLine("  {0}", method);  
            }  
        }  

        Console.WriteLine("Press any key to exit... ");  
        Console.ReadKey();  
    }  
}
```  

<span data-ttu-id="e36cb-108">L’exemple utilise la méthode <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> pour retourner un tableau de types de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="e36cb-108">The example uses the <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> method to return an array of types in the specified assembly.</span></span> <span data-ttu-id="e36cb-109">Le filtre [where](../../../language-reference/keywords/where-clause.md) est appliqué pour que seuls des types publics soient retournés.</span><span class="sxs-lookup"><span data-stu-id="e36cb-109">The [where](../../../language-reference/keywords/where-clause.md) filter is applied so that only public types are returned.</span></span> <span data-ttu-id="e36cb-110">Pour chaque type public, une sous-requête est générée en utilisant le tableau <xref:System.Reflection.MethodInfo> qui est retourné à partir de l’appel <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e36cb-110">For each public type, a subquery is generated by using the <xref:System.Reflection.MethodInfo> array that is returned from the <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="e36cb-111">Ces résultats sont filtrés pour retourner uniquement les méthodes dont le type de retour est un tableau ou un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e36cb-111">These results are filtered to return only those methods whose return type is an array or else a type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e36cb-112">Pour finir, ces résultats sont regroupés en utilisant le nom de type comme clé.</span><span class="sxs-lookup"><span data-stu-id="e36cb-112">Finally, these results are grouped by using the type name as a key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36cb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e36cb-113">See also</span></span>

- [<span data-ttu-id="e36cb-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e36cb-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
