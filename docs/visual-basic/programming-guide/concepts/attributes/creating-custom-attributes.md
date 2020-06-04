---
title: Création d'attributs personnalisés
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400692"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="b5c13-102">Créer des attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c13-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="b5c13-103">Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs. Cette classe dérive directement ou indirectement d’<xref:System.Attribute>, ce qui permet d’identifier rapidement et facilement des définitions d’attributs dans des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b5c13-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="b5c13-104">Supposons que vous souhaitiez baliser des types avec le nom du programmeur qui les a écrits.</span><span class="sxs-lookup"><span data-stu-id="b5c13-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="b5c13-105">Vous pouvez définir une classe d’attributs `Author` personnalisés :</span><span class="sxs-lookup"><span data-stu-id="b5c13-105">You might define a custom `Author` attribute class:</span></span>

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

<span data-ttu-id="b5c13-106">Le nom de la classe est le nom de l’attribut, `Author`.</span><span class="sxs-lookup"><span data-stu-id="b5c13-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="b5c13-107">Étant dérivée de `System.Attribute`, il s’agit donc d’une classe d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b5c13-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="b5c13-108">Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b5c13-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="b5c13-109">Dans cet exemple, `name` est un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="b5c13-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="b5c13-110">Les propriétés ou champs de type public accessibles en lecture/écriture sont des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="b5c13-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="b5c13-111">Dans le cas présent, `version` est le seul paramètre nommé.</span><span class="sxs-lookup"><span data-stu-id="b5c13-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="b5c13-112">Notez l’utilisation de l’attribut `AttributeUsage` pour rendre l’attribut `Author` valide uniquement sur les déclarations de classe et de `Structure`.</span><span class="sxs-lookup"><span data-stu-id="b5c13-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="b5c13-113">Vous pouvez utiliser ce nouvel attribut de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="b5c13-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="b5c13-114">`AttributeUsage` a un paramètre nommé, `AllowMultiple`, qui permet de déclarer un attribut personnalisé comme étant à usage unique ou multiple.</span><span class="sxs-lookup"><span data-stu-id="b5c13-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="b5c13-115">Dans l’exemple de code suivant, un attribut à usage multiple est créé.</span><span class="sxs-lookup"><span data-stu-id="b5c13-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="b5c13-116">Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.</span><span class="sxs-lookup"><span data-stu-id="b5c13-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="b5c13-117">Si votre classe d’attributs contient une propriété, celle-ci doit être en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="b5c13-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c13-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5c13-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="b5c13-119">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5c13-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="b5c13-120">Écriture des attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="b5c13-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="b5c13-121">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c13-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="b5c13-122">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c13-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="b5c13-123">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c13-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="b5c13-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5c13-124">AttributeUsage (Visual Basic)</span></span>](attributeusage.md)
