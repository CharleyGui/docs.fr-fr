---
title: Constructeurs privés - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705442"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="f017e-102">Constructeurs privés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f017e-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="f017e-103">Un constructeur privé est un constructeur d’instance spécial.</span><span class="sxs-lookup"><span data-stu-id="f017e-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="f017e-104">Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="f017e-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="f017e-105">Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe.</span><span class="sxs-lookup"><span data-stu-id="f017e-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="f017e-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f017e-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="f017e-107">La déclaration du constructeur vide empêche la génération automatique d’un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="f017e-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="f017e-108">Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut.</span><span class="sxs-lookup"><span data-stu-id="f017e-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="f017e-109">En règle générale, le modificateur [private](../../language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="f017e-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="f017e-110">Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="f017e-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="f017e-111">Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique.</span><span class="sxs-lookup"><span data-stu-id="f017e-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="f017e-112">Pour plus d’informations, consultez [les classes statiques et les membres de la classe statique](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f017e-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f017e-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f017e-113">Example</span></span>  
 <span data-ttu-id="f017e-114">L’exemple suivant montre une classe qui utilise un constructeur privé.</span><span class="sxs-lookup"><span data-stu-id="f017e-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="f017e-115">Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :</span><span class="sxs-lookup"><span data-stu-id="f017e-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f017e-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f017e-116">C# Language Specification</span></span>  

<span data-ttu-id="f017e-117">Pour plus d’informations, consultez [Constructeurs privés](~/_csharplang/spec/classes.md#private-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f017e-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f017e-118">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="f017e-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f017e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f017e-119">See also</span></span>

- [<span data-ttu-id="f017e-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f017e-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f017e-121">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="f017e-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f017e-122">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="f017e-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="f017e-123">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="f017e-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="f017e-124">Privé</span><span class="sxs-lookup"><span data-stu-id="f017e-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="f017e-125">public</span><span class="sxs-lookup"><span data-stu-id="f017e-125">public</span></span>](../../language-reference/keywords/public.md)
