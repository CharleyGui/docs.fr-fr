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
# <a name="accessing-attributes-by-using-reflection-c"></a>Accès à des attributs à l’aide de la réflexion (C#)
La définition d’attributs personnalisés et leur ajout à votre code source présentent peu d’intérêt si vous ne pouvez pas ensuite récupérer et manipuler ces informations. La réflexion vous permet de récupérer les informations qui ont été définies à l’aide d’attributs personnalisés. La méthode clé est `GetCustomAttributes`. Elle retourne un tableau d’objets qui sont les équivalents des attributs du code source au moment de l’exécution. Cette méthode a plusieurs versions surchargées. Pour plus d’informations, consultez <xref:System.Attribute>.  
  
 Par exemple, cette spécification d’attribut :  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 est semblable à celle-ci d’un point de vue conceptuel :  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Toutefois, le code n’est pas exécuté tant qu’une requête n’est pas effectuée sur `SampleClass` pour obtenir les attributs. L’appel de `GetCustomAttributes` sur `SampleClass` entraîne la construction et l’initialisation d’un objet `Author` comme illustré ci-dessus. Si la classe a d’autres attributs, les autres objets attribut sont construits de la même façon. `GetCustomAttributes` retourne ensuite l’objet `Author` et les autres objets attribut dans un tableau. Vous pouvez ensuite itérer sur ce tableau, déterminer quels attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations des objets attribut.  
  
## <a name="example"></a> Exemple  
 Voici un exemple complet. Un attribut personnalisé est défini, appliqué à plusieurs entités, puis récupéré par réflexion.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guide de programmation C#](../../index.md)
- [Récupération des informations stockées dans les attributs](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Réflexion (C#)](../reflection.md)
- [Attributs (C#)](./index.md)
- [Création d’attributs personnalisés (C#)](./creating-custom-attributes.md)
