---
title: Accès à des attributs à l’aide de la réflexion (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595496"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="7edf7-102">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="7edf7-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="7edf7-103">La définition d’attributs personnalisés et leur ajout à votre code source présentent peu d’intérêt si vous ne pouvez pas ensuite récupérer et manipuler ces informations.</span><span class="sxs-lookup"><span data-stu-id="7edf7-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="7edf7-104">La réflexion vous permet de récupérer les informations qui ont été définies à l’aide d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7edf7-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="7edf7-105">La méthode clé est `GetCustomAttributes`. Elle retourne un tableau d’objets qui sont les équivalents des attributs du code source au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7edf7-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="7edf7-106">Cette méthode a plusieurs versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="7edf7-106">This method has several overloaded versions.</span></span> <span data-ttu-id="7edf7-107">Pour plus d’informations, consultez <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="7edf7-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="7edf7-108">Par exemple, cette spécification d’attribut :</span><span class="sxs-lookup"><span data-stu-id="7edf7-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="7edf7-109">est semblable à celle-ci d’un point de vue conceptuel :</span><span class="sxs-lookup"><span data-stu-id="7edf7-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="7edf7-110">Toutefois, le code n’est pas exécuté tant qu’une requête n’est pas effectuée sur `SampleClass` pour obtenir les attributs.</span><span class="sxs-lookup"><span data-stu-id="7edf7-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="7edf7-111">L’appel de `GetCustomAttributes` sur `SampleClass` entraîne la construction et l’initialisation d’un objet `Author` comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7edf7-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="7edf7-112">Si la classe a d’autres attributs, les autres objets attribut sont construits de la même façon.</span><span class="sxs-lookup"><span data-stu-id="7edf7-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="7edf7-113">`GetCustomAttributes` retourne ensuite l’objet `Author` et les autres objets attribut dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="7edf7-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="7edf7-114">Vous pouvez ensuite itérer sur ce tableau, déterminer quels attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations des objets attribut.</span><span class="sxs-lookup"><span data-stu-id="7edf7-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7edf7-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7edf7-115">Example</span></span>  
 <span data-ttu-id="7edf7-116">Voici un exemple complet.</span><span class="sxs-lookup"><span data-stu-id="7edf7-116">Here is a complete example.</span></span> <span data-ttu-id="7edf7-117">Un attribut personnalisé est défini, appliqué à plusieurs entités, puis récupéré par réflexion.</span><span class="sxs-lookup"><span data-stu-id="7edf7-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="7edf7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7edf7-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="7edf7-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7edf7-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="7edf7-120">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="7edf7-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="7edf7-121">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="7edf7-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="7edf7-122">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="7edf7-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="7edf7-123">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="7edf7-123">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
