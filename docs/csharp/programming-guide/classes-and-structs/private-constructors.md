---
title: Constructeurs privés - Guide de programmation C#
description: Un constructeur privé est un constructeur d’instance spécial en C# utilisé pour limiter la manière dont un objet peut être créé. Elles peuvent être utilisées avec des méthodes de fabrique ou d’autres idiomes de construction.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899398"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="20f46-104">Constructeurs privés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="20f46-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="20f46-105">Un constructeur privé est un constructeur d’instance spécial.</span><span class="sxs-lookup"><span data-stu-id="20f46-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="20f46-106">Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="20f46-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="20f46-107">Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe.</span><span class="sxs-lookup"><span data-stu-id="20f46-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="20f46-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="20f46-108">For example:</span></span>  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 <span data-ttu-id="20f46-109">La déclaration du constructeur vide empêche la génération automatique d’un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="20f46-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="20f46-110">Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut.</span><span class="sxs-lookup"><span data-stu-id="20f46-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="20f46-111">En règle générale, le modificateur [private](../../language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="20f46-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="20f46-112">Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="20f46-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="20f46-113">Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique.</span><span class="sxs-lookup"><span data-stu-id="20f46-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="20f46-114">Pour plus d’informations [, consultez classes statiques et membres de classe statique](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="20f46-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20f46-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="20f46-115">Example</span></span>  

 <span data-ttu-id="20f46-116">L’exemple suivant montre une classe qui utilise un constructeur privé.</span><span class="sxs-lookup"><span data-stu-id="20f46-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 <span data-ttu-id="20f46-117">Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :</span><span class="sxs-lookup"><span data-stu-id="20f46-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a><span data-ttu-id="20f46-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="20f46-118">C# Language Specification</span></span>  

<span data-ttu-id="20f46-119">Pour plus d’informations, consultez [Constructeurs privés](~/_csharplang/spec/classes.md#private-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="20f46-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="20f46-120">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="20f46-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="20f46-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20f46-121">See also</span></span>

- [<span data-ttu-id="20f46-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="20f46-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="20f46-123">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="20f46-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="20f46-124">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="20f46-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="20f46-125">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="20f46-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="20f46-126">priv</span><span class="sxs-lookup"><span data-stu-id="20f46-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="20f46-127">public</span><span class="sxs-lookup"><span data-stu-id="20f46-127">public</span></span>](../../language-reference/keywords/public.md)
