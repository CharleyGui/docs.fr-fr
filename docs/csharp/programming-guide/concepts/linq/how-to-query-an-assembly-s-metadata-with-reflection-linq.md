---
title: Comment interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 092cb386af0c3f2e2241c2c2ac8e50eab74cc43b
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241537"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Comment interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)

Les API de réflexion .NET peuvent être utilisées pour examiner les métadonnées dans un assembly .NET et créer des collections de types, des membres de type, des paramètres, etc., qui se trouvent dans cet assembly. Comme ces collections prennent en charge l’interface générique <xref:System.Collections.Generic.IEnumerable%601>, elles peuvent être interrogées à l’aide de LINQ.  
  
L’exemple suivant montre comment utiliser LINQ avec la réflexion pour récupérer des métadonnées spécifiques concernant des méthodes qui correspondent à un critère de recherche spécifié. Ici, la requête va rechercher les noms de toutes les méthodes dans l’assembly qui retournent des types énumérables tels que des tableaux.  
  
## <a name="example"></a>Exemple  
  
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

L’exemple utilise la méthode <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> pour retourner un tableau de types de l’assembly spécifié. Le filtre [where](../../../language-reference/keywords/where-clause.md) est appliqué pour que seuls des types publics soient retournés. Pour chaque type public, une sous-requête est générée en utilisant le tableau <xref:System.Reflection.MethodInfo> qui est retourné à partir de l’appel <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Ces résultats sont filtrés pour retourner uniquement les méthodes dont le type de retour est un tableau ou un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>. Pour finir, ces résultats sont regroupés en utilisant le nom de type comme clé.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (C#)](./linq-to-objects.md)
