---
description: abstract - Référence C#
title: abstract - Référence C#
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 276e3f6ab50a069e3852c529c13eaad3c64e42ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168879"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="94ad2-103">abstract (référence C#)</span><span class="sxs-lookup"><span data-stu-id="94ad2-103">abstract (C# Reference)</span></span>

<span data-ttu-id="94ad2-104">Le modificateur `abstract` indique que l’élément en cours de modification a une implémentation manquante ou incomplète.</span><span class="sxs-lookup"><span data-stu-id="94ad2-104">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="94ad2-105">Le modificateur abstract peut être utilisé avec des classes, des méthodes, des propriétés, des indexeurs et des événements.</span><span class="sxs-lookup"><span data-stu-id="94ad2-105">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="94ad2-106">Dans une déclaration de classe, utilisez le modificateur `abstract` pour indiquer qu’une classe doit uniquement servir de classe de base pour d’autres classes, et ne pas être instanciée toute seule.</span><span class="sxs-lookup"><span data-stu-id="94ad2-106">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="94ad2-107">Les membres définis comme abstraits doivent être implémentés par des classes non abstraites dérivées de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="94ad2-107">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="94ad2-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="94ad2-108">Example</span></span>  

 <span data-ttu-id="94ad2-109">Dans cet exemple, la classe `Square` doit fournir une implémentation de `GetArea`, car elle dérive de la classe `Shape` :</span><span class="sxs-lookup"><span data-stu-id="94ad2-109">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="94ad2-110">Les classes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="94ad2-110">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="94ad2-111">Une classe abstraite ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="94ad2-111">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="94ad2-112">Une classe abstraite peut contenir des méthodes et accesseurs abstraits.</span><span class="sxs-lookup"><span data-stu-id="94ad2-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="94ad2-113">Il n’est pas possible de modifier une classe abstraite avec le modificateur [sealed](./sealed.md), car les deux modificateurs ont des significations opposées.</span><span class="sxs-lookup"><span data-stu-id="94ad2-113">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="94ad2-114">Le modificateur `sealed` empêche qu’une classe soit héritée et le modificateur `abstract` exige qu’une classe soit héritée.</span><span class="sxs-lookup"><span data-stu-id="94ad2-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="94ad2-115">Une classe non abstraite dérivée d’une classe abstraite doit inclure des implémentations réelles de tous les accesseurs et méthodes abstraits hérités.</span><span class="sxs-lookup"><span data-stu-id="94ad2-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="94ad2-116">Dans une déclaration de méthode ou de propriété, utilisez le modificateur `abstract` pour indiquer que la méthode ou la propriété ne contient pas d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="94ad2-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="94ad2-117">Les méthodes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="94ad2-117">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="94ad2-118">Une méthode abstraite est implicitement une méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="94ad2-118">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="94ad2-119">Les déclarations de méthodes abstraites sont autorisées uniquement dans les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="94ad2-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="94ad2-120">Comme une déclaration de méthode abstraite ne fournit pas d’implémentation réelle, il n’y a pas de corps de méthode ; la déclaration de méthode se termine simplement par un point-virgule, et la signature n’est pas suivie d’accolades ({ }).</span><span class="sxs-lookup"><span data-stu-id="94ad2-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="94ad2-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="94ad2-121">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="94ad2-122">L’implémentation est fournie par une méthode [override](./override.md), qui est membre d’une classe non abstraite.</span><span class="sxs-lookup"><span data-stu-id="94ad2-122">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="94ad2-123">L’utilisation des modificateurs [static](./static.md) ou [virtual](./virtual.md) dans une déclaration de méthode abstraite serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="94ad2-123">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="94ad2-124">Les propriétés abstraites se comportent comme les méthodes abstraites, à l’exception des différences dans la syntaxe de déclaration et d’appel.</span><span class="sxs-lookup"><span data-stu-id="94ad2-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="94ad2-125">L’utilisation du modificateur `abstract` sur une propriété statique serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="94ad2-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="94ad2-126">Une propriété abstraite héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur [override](./override.md).</span><span class="sxs-lookup"><span data-stu-id="94ad2-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="94ad2-127">Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="94ad2-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="94ad2-128">Une classe abstraite doit fournir une implémentation pour tous les membres d’interface.</span><span class="sxs-lookup"><span data-stu-id="94ad2-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="94ad2-129">Une classe abstraite qui implémente une interface peut mapper les méthodes d’interface à des méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="94ad2-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="94ad2-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="94ad2-130">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="94ad2-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="94ad2-131">Example</span></span>  

 <span data-ttu-id="94ad2-132">Dans cet exemple, la classe `DerivedClass` est dérivée de la classe abstraite `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="94ad2-132">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="94ad2-133">La classe abstraite contient une méthode abstraite, `AbstractMethod`, et deux propriétés abstraites, `X` et `Y`.</span><span class="sxs-lookup"><span data-stu-id="94ad2-133">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="94ad2-134">Dans l’exemple précédent, si vous tentez d’instancier la classe abstraite en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="94ad2-134">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="94ad2-135">Vous obtenez une erreur indiquant que le compilateur ne peut pas créer une instance de la classe abstraite BaseClass.</span><span class="sxs-lookup"><span data-stu-id="94ad2-135">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="94ad2-136">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="94ad2-136">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94ad2-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94ad2-137">See also</span></span>

- [<span data-ttu-id="94ad2-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="94ad2-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="94ad2-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="94ad2-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="94ad2-140">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="94ad2-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="94ad2-141">virtual</span><span class="sxs-lookup"><span data-stu-id="94ad2-141">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="94ad2-142">override</span><span class="sxs-lookup"><span data-stu-id="94ad2-142">override</span></span>](./override.md)
- [<span data-ttu-id="94ad2-143">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="94ad2-143">C# Keywords</span></span>](./index.md)
