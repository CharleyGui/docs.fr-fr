---
title: Classes abstract et sealed et membres de classe - Guide de programmation C#
description: Le mot clé abstract en C# crée des classes et des membres de classe incomplets. Le mot clé sealed empêche l’héritage des classes ou membres de classe virtuels précédemment.
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: ccbc6734d4e9bafe059dd45bfdf82af7c84438a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204032"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="200fa-104">Classes abstract et sealed et membres de classe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="200fa-104">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="200fa-105">Le mot clé [abstract](../../language-reference/keywords/abstract.md) vous permet de créer des classes et des membres de [class](../../language-reference/keywords/class.md) qui sont incomplets et doivent être implémentés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="200fa-105">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="200fa-106">Le mot clé [sealed](../../language-reference/keywords/sealed.md) vous permet d’empêcher l’héritage d’une classe ou de certains membres de classe qui étaient précédemment marqués comme [virtual](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="200fa-106">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="200fa-107">Classes abstraites et membres de classe</span><span class="sxs-lookup"><span data-stu-id="200fa-107">Abstract Classes and Class Members</span></span>  

 <span data-ttu-id="200fa-108">Les classes peuvent être déclarées comme abstraites en plaçant le mot clé `abstract` avant la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="200fa-108">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="200fa-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="200fa-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="200fa-110">Une classe abstraite ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="200fa-110">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="200fa-111">Le but d'une classe abstraite est de fournir une définition commune d'une classe de base pouvant être partagée par plusieurs classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="200fa-111">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="200fa-112">Par exemple, une bibliothèque de classes peut définir une classe abstraite qui est utilisée comme un paramètre pour beaucoup de ses fonctions, et exiger des programmeurs qui l'utilisent de fournir leur propre implémentation de la classe en créant une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="200fa-112">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="200fa-113">Les classes abstraites peuvent également définir des méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="200fa-113">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="200fa-114">Pour ce faire, ajoutez le mot clé `abstract` avant le type de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="200fa-114">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="200fa-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="200fa-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="200fa-116">Les méthodes abstraites n'ont pas d'implémentation. Ainsi, la définition de la méthode est suivie d'un point-virgule au lieu d'un bloc de méthode normal.</span><span class="sxs-lookup"><span data-stu-id="200fa-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="200fa-117">Les classes dérivées de la classe abstraite doivent implémenter toutes les méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="200fa-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="200fa-118">Lorsqu'une classe abstraite hérite d'une méthode virtuelle d'une classe de base, la classe abstraite peut substituer la méthode virtuelle par une méthode abstraite.</span><span class="sxs-lookup"><span data-stu-id="200fa-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="200fa-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="200fa-119">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="200fa-120">Si une méthode `virtual` est déclarée `abstract`, elle demeure virtuelle pour toutes les classes qui héritent de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="200fa-120">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="200fa-121">Une classe qui hérite d’une méthode abstraite ne peut pas accéder à l’implémentation d’origine de la méthode. Dans l’exemple précédent, `DoWork` sur la classe F ne peut pas appeler `DoWork` sur la classe D. De cette manière, une classe abstraite peut forcer les classes dérivées à fournir de nouvelles implémentations de méthode pour les méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="200fa-121">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="200fa-122">Classes sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="200fa-122">Sealed Classes and Class Members</span></span>  

 <span data-ttu-id="200fa-123">Les classes peuvent être déclarées comme [sealed](../../language-reference/keywords/sealed.md) en plaçant le mot clé `sealed` avant la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="200fa-123">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="200fa-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="200fa-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="200fa-125">Une classe sealed ne peut pas être utilisée comme une classe de base.</span><span class="sxs-lookup"><span data-stu-id="200fa-125">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="200fa-126">Pour cette raison, elle ne peut pas également être une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="200fa-126">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="200fa-127">Les classes sealed empêchent la dérivation.</span><span class="sxs-lookup"><span data-stu-id="200fa-127">Sealed classes prevent derivation.</span></span> <span data-ttu-id="200fa-128">Étant donné qu'elles ne peuvent pas être utilisées comme une classe de base, quelques optimisations au moment de l'exécution permettent d'accélérer un peu les appels aux membres des classes sealed.</span><span class="sxs-lookup"><span data-stu-id="200fa-128">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="200fa-129">Une méthode, un indexeur, une propriété ou un événement sur une classe dérivée qui substitue un membre virtuel de la classe de base peut déclarer ce membre comme sealed.</span><span class="sxs-lookup"><span data-stu-id="200fa-129">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="200fa-130">Cela nie l'aspect virtuel du membre pour toute classe dérivée ultérieure.</span><span class="sxs-lookup"><span data-stu-id="200fa-130">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="200fa-131">Pour ce faire, mettez le mot clé `sealed` avant le mot clé [override](../../language-reference/keywords/override.md) dans la déclaration de membre de classe.</span><span class="sxs-lookup"><span data-stu-id="200fa-131">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="200fa-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="200fa-132">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="200fa-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="200fa-133">See also</span></span>

- [<span data-ttu-id="200fa-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="200fa-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="200fa-135">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="200fa-135">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="200fa-136">Héritage</span><span class="sxs-lookup"><span data-stu-id="200fa-136">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="200fa-137">Méthodes</span><span class="sxs-lookup"><span data-stu-id="200fa-137">Methods</span></span>](./methods.md)
- [<span data-ttu-id="200fa-138">Fields</span><span class="sxs-lookup"><span data-stu-id="200fa-138">Fields</span></span>](./fields.md)
- [<span data-ttu-id="200fa-139">Comment : définir des propriétés abstraites</span><span class="sxs-lookup"><span data-stu-id="200fa-139">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
