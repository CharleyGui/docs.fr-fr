---
title: Création d’attributs personnalisés (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e4b55f92466fde47011937d08c946c9c75ca07b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966329"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="91c6c-102">Création d’attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c6c-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="91c6c-103">Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs. Cette classe dérive directement ou indirectement d’<xref:System.Attribute>, ce qui permet d’identifier rapidement et facilement des définitions d’attributs dans des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="91c6c-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="91c6c-104">Supposons que vous souhaitiez baliser des types avec le nom du programmeur qui les a écrits.</span><span class="sxs-lookup"><span data-stu-id="91c6c-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="91c6c-105">Vous pouvez définir une classe d’attributs `Author` personnalisés :</span><span class="sxs-lookup"><span data-stu-id="91c6c-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="91c6c-106">Le nom de la classe est le nom de l’attribut, `Author`.</span><span class="sxs-lookup"><span data-stu-id="91c6c-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="91c6c-107">Étant dérivée de `System.Attribute`, il s’agit donc d’une classe d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="91c6c-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="91c6c-108">Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="91c6c-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="91c6c-109">Dans cet exemple, `name` est un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="91c6c-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="91c6c-110">Les propriétés ou champs de type public accessibles en lecture/écriture sont des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="91c6c-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="91c6c-111">Dans le cas présent, `version` est le seul paramètre nommé.</span><span class="sxs-lookup"><span data-stu-id="91c6c-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="91c6c-112">Notez l’utilisation de l’attribut `AttributeUsage` pour rendre l’attribut `Author` valide uniquement sur les déclarations de classe et de `Structure`.</span><span class="sxs-lookup"><span data-stu-id="91c6c-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="91c6c-113">Vous pouvez utiliser ce nouvel attribut de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="91c6c-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="91c6c-114">`AttributeUsage` a un paramètre nommé, `AllowMultiple`, qui permet de déclarer un attribut personnalisé comme étant à usage unique ou multiple.</span><span class="sxs-lookup"><span data-stu-id="91c6c-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="91c6c-115">Dans l’exemple de code suivant, un attribut à usage multiple est créé.</span><span class="sxs-lookup"><span data-stu-id="91c6c-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="91c6c-116">Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.</span><span class="sxs-lookup"><span data-stu-id="91c6c-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
> <span data-ttu-id="91c6c-117">Si votre classe d’attributs contient une propriété, celle-ci doit être en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="91c6c-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c6c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91c6c-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="91c6c-119">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91c6c-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="91c6c-120">Écriture des attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="91c6c-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="91c6c-121">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c6c-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="91c6c-122">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c6c-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="91c6c-123">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c6c-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="91c6c-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91c6c-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
