---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 84c3d175aede5d8066198592ffac601c0bd97620
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351815"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="58dbd-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dbd-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="58dbd-103">Détermine de quelle manière une classe d’attributs personnalisés peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="58dbd-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="58dbd-104">`AttributeUsage` est un attribut qui peut être appliqué à des définitions d’attributs personnalisés pour contrôler le mode d’application du nouvel attribut.</span><span class="sxs-lookup"><span data-stu-id="58dbd-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="58dbd-105">Voici le code quand les paramètres par défaut sont appliqués de manière explicite :</span><span class="sxs-lookup"><span data-stu-id="58dbd-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="58dbd-106">Dans cet exemple, la classe `NewAttribute` peut être appliquée à toutes les entités de code acceptant un attribut, mais uniquement une fois par entité.</span><span class="sxs-lookup"><span data-stu-id="58dbd-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="58dbd-107">Elle est héritée par les classes dérivées quand elle est appliquée à une classe de base.</span><span class="sxs-lookup"><span data-stu-id="58dbd-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="58dbd-108">Les arguments `AllowMultiple` et `Inherited` étant facultatifs, ce code produit le même résultat :</span><span class="sxs-lookup"><span data-stu-id="58dbd-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="58dbd-109">Le premier argument `AttributeUsage` doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="58dbd-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="58dbd-110">Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :</span><span class="sxs-lookup"><span data-stu-id="58dbd-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="58dbd-111">Si l’argument `AllowMultiple` est défini sur `true`, l’attribut qui en résulte peut être appliqué plusieurs fois à une même entité, comme suit :</span><span class="sxs-lookup"><span data-stu-id="58dbd-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 <span data-ttu-id="58dbd-112">Dans ce cas, `MultiUseAttr` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="58dbd-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="58dbd-113">Les deux formats indiqués pour appliquer plusieurs attributs sont valides.</span><span class="sxs-lookup"><span data-stu-id="58dbd-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="58dbd-114">Si `Inherited` est défini sur `false`, l’attribut n’est pas hérité par les classes qui sont dérivées d’une classe avec attributs.</span><span class="sxs-lookup"><span data-stu-id="58dbd-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="58dbd-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="58dbd-115">For example:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 <span data-ttu-id="58dbd-116">Dans ce cas, `Attr1` n’est pas appliqué à `DClass` par héritage.</span><span class="sxs-lookup"><span data-stu-id="58dbd-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58dbd-117">Notes</span><span class="sxs-lookup"><span data-stu-id="58dbd-117">Remarks</span></span>  
 <span data-ttu-id="58dbd-118">L’attribut `AttributeUsage` est un attribut à usage unique : il ne peut pas être appliqué plusieurs fois à la même classe.</span><span class="sxs-lookup"><span data-stu-id="58dbd-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="58dbd-119">`AttributeUsage` est un alias pour <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58dbd-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="58dbd-120">Pour plus d’informations, consultez la page [Accéder à des attributs grâce à la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="58dbd-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58dbd-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="58dbd-121">Example</span></span>  
 <span data-ttu-id="58dbd-122">L’exemple suivant illustre l’effet des arguments `Inherited` et `AllowMultiple` sur l’attribut `AttributeUsage`, et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="58dbd-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a><span data-ttu-id="58dbd-123">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="58dbd-123">Sample Output</span></span>  
  
```console  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="58dbd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58dbd-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="58dbd-125">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58dbd-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="58dbd-126">Attributs</span><span class="sxs-lookup"><span data-stu-id="58dbd-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="58dbd-127">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dbd-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="58dbd-128">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dbd-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="58dbd-129">Créer des attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dbd-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="58dbd-130">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dbd-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
