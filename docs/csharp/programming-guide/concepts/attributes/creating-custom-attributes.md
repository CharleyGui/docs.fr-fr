---
title: Création d’attributs personnalisés (C#)
description: Découvrez comment créer des attributs personnalisés en C# en définissant une classe d’attributs qui dérive de la classe d’attributs.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 6946b707134b2bdbc245b8786f144517a5870440
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202602"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="05347-103">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="05347-103">Creating Custom Attributes (C#)</span></span>

<span data-ttu-id="05347-104">Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs. Cette classe dérive directement ou indirectement d’<xref:System.Attribute>, ce qui permet d’identifier rapidement et facilement des définitions d’attributs dans des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="05347-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="05347-105">Supposons que vous souhaitiez baliser des types avec le nom du programmeur qui les a écrits.</span><span class="sxs-lookup"><span data-stu-id="05347-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="05347-106">Vous pouvez définir une classe d’attributs `Author` personnalisés :</span><span class="sxs-lookup"><span data-stu-id="05347-106">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="05347-107">Le nom de la classe `AuthorAttribute` est le nom de l’attribut, `Author` , et le `Attribute` suffixe.</span><span class="sxs-lookup"><span data-stu-id="05347-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="05347-108">Étant dérivée de `System.Attribute`, il s’agit donc d’une classe d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="05347-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="05347-109">Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="05347-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="05347-110">Dans cet exemple, `name` est un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="05347-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="05347-111">Les propriétés ou champs de type public accessibles en lecture/écriture sont des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="05347-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="05347-112">Dans le cas présent, `version` est le seul paramètre nommé.</span><span class="sxs-lookup"><span data-stu-id="05347-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="05347-113">Notez l’utilisation de l’attribut `AttributeUsage` pour rendre l’attribut `Author` valide uniquement sur les déclarations de classe et de `struct`.</span><span class="sxs-lookup"><span data-stu-id="05347-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="05347-114">Vous pouvez utiliser ce nouvel attribut de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="05347-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="05347-115">`AttributeUsage` a un paramètre nommé, `AllowMultiple`, qui permet de déclarer un attribut personnalisé comme étant à usage unique ou multiple.</span><span class="sxs-lookup"><span data-stu-id="05347-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="05347-116">Dans l’exemple de code suivant, un attribut à usage multiple est créé.</span><span class="sxs-lookup"><span data-stu-id="05347-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="05347-117">Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.</span><span class="sxs-lookup"><span data-stu-id="05347-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="05347-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05347-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="05347-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="05347-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="05347-120">Écriture des attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="05347-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="05347-121">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="05347-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="05347-122">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="05347-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="05347-123">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="05347-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="05347-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="05347-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
