---
title: Constructeurs privés - Guide de programmation C#
description: Un constructeur privé est un constructeur d’instance spécial en C# utilisé pour limiter la manière dont un objet peut être créé. Elles peuvent être utilisées avec des méthodes de fabrique ou d’autres idiomes de construction.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: c6048424128b462bfc56d9c7c3cf8f75cca9298d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159343"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="34497-104">Constructeurs privés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="34497-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="34497-105">Un constructeur privé est un constructeur d’instance spécial.</span><span class="sxs-lookup"><span data-stu-id="34497-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="34497-106">Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="34497-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="34497-107">Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe.</span><span class="sxs-lookup"><span data-stu-id="34497-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="34497-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="34497-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="34497-109">La déclaration du constructeur vide empêche la génération automatique d’un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="34497-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="34497-110">Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut.</span><span class="sxs-lookup"><span data-stu-id="34497-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="34497-111">En règle générale, le modificateur [private](../../language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="34497-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="34497-112">Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="34497-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="34497-113">Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique.</span><span class="sxs-lookup"><span data-stu-id="34497-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="34497-114">Pour plus d’informations [, consultez classes statiques et membres de classe statique](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="34497-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34497-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="34497-115">Example</span></span>  

 <span data-ttu-id="34497-116">L’exemple suivant montre une classe qui utilise un constructeur privé.</span><span class="sxs-lookup"><span data-stu-id="34497-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="34497-117">Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :</span><span class="sxs-lookup"><span data-stu-id="34497-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="34497-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="34497-118">C# Language Specification</span></span>  

<span data-ttu-id="34497-119">Pour plus d’informations, consultez [Constructeurs privés](~/_csharplang/spec/classes.md#private-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="34497-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="34497-120">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="34497-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="34497-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34497-121">See also</span></span>

- [<span data-ttu-id="34497-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="34497-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34497-123">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="34497-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="34497-124">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="34497-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="34497-125">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="34497-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="34497-126">priv</span><span class="sxs-lookup"><span data-stu-id="34497-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="34497-127">public</span><span class="sxs-lookup"><span data-stu-id="34497-127">public</span></span>](../../language-reference/keywords/public.md)
