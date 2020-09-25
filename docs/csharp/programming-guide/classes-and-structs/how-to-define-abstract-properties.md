---
title: Comment définir des propriétés abstraites-Guide de programmation C#
description: Découvrez comment définir des propriétés abstraites en C#. La déclaration d’une propriété abstraite signifie qu’une classe prend en charge une propriété. Les classes dérivées implémentent des accesseurs.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 01af1446097bbed25874b45d57a5dde85ae63891
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199157"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="3870e-105">Comment définir des propriétés abstraites (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3870e-105">How to define abstract properties (C# Programming Guide)</span></span>

<span data-ttu-id="3870e-106">L’exemple suivant montre comment définir des propriétés [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="3870e-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="3870e-107">Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="3870e-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="3870e-108">L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="3870e-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="3870e-109">Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :</span><span class="sxs-lookup"><span data-stu-id="3870e-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="3870e-110">abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.</span><span class="sxs-lookup"><span data-stu-id="3870e-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="3870e-111">shapes.cs : sous-classes de la classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="3870e-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="3870e-112">shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.</span><span class="sxs-lookup"><span data-stu-id="3870e-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="3870e-113">Pour compiler l’exemple, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3870e-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="3870e-114">Cette commande crée le fichier exécutable shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="3870e-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3870e-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="3870e-115">Example</span></span>  

 <span data-ttu-id="3870e-116">Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.</span><span class="sxs-lookup"><span data-stu-id="3870e-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="3870e-117">Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="3870e-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="3870e-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3870e-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="3870e-119">Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas.</span><span class="sxs-lookup"><span data-stu-id="3870e-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="3870e-120">Dans cet exemple, seul un accesseur [get](../../language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3870e-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3870e-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="3870e-121">Example</span></span>  

 <span data-ttu-id="3870e-122">Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="3870e-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="3870e-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="3870e-123">Example</span></span>  

 <span data-ttu-id="3870e-124">Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.</span><span class="sxs-lookup"><span data-stu-id="3870e-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3870e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3870e-125">See also</span></span>

- [<span data-ttu-id="3870e-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3870e-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3870e-127">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="3870e-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="3870e-128">Classes abstract et sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="3870e-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="3870e-129">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3870e-129">Properties</span></span>](./properties.md)
