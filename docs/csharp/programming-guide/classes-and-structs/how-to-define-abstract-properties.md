---
title: 'Procédure : Définir des propriétés abstraites - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: ef19b80e7f4c32830aabfcf1ad595348c2107228
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599989"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="2678c-102">Procédure : Définir des propriétés abstraites (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2678c-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="2678c-103">L’exemple suivant montre comment définir des propriétés [abstract](../../../csharp/language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="2678c-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="2678c-104">Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="2678c-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="2678c-105">L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="2678c-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="2678c-106">Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :</span><span class="sxs-lookup"><span data-stu-id="2678c-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="2678c-107">abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.</span><span class="sxs-lookup"><span data-stu-id="2678c-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="2678c-108">shapes.cs : sous-classes de la classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="2678c-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="2678c-109">shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.</span><span class="sxs-lookup"><span data-stu-id="2678c-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="2678c-110">Pour compiler l’exemple, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2678c-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="2678c-111">Cette commande crée le fichier exécutable shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="2678c-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2678c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="2678c-112">Example</span></span>  
 <span data-ttu-id="2678c-113">Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.</span><span class="sxs-lookup"><span data-stu-id="2678c-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="2678c-114">Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="2678c-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="2678c-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2678c-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="2678c-116">Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas.</span><span class="sxs-lookup"><span data-stu-id="2678c-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="2678c-117">Dans cet exemple, seul un accesseur [get](../../../csharp/language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="2678c-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2678c-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="2678c-118">Example</span></span>  
 <span data-ttu-id="2678c-119">Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="2678c-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="2678c-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="2678c-120">Example</span></span>  
 <span data-ttu-id="2678c-121">Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.</span><span class="sxs-lookup"><span data-stu-id="2678c-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2678c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2678c-122">See also</span></span>

- [<span data-ttu-id="2678c-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2678c-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2678c-124">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="2678c-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="2678c-125">Classes abstract et sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="2678c-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="2678c-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2678c-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="2678c-127">Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2678c-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
