---
title: Restriction d’accessibilité de l’accesseur - Guide de programmation C#
description: Les accesseurs d’extraction et de définition d’une propriété en C# ont le même niveau de visibilité ou d’accès par défaut que la propriété à laquelle ils appartiennent. Vous pouvez restreindre l’accès.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: be7be4fc67a9a6f62a71f8473d6daa1fac49e842
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199027"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="c294c-104">Restriction d’accessibilité de l’accesseur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c294c-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>

<span data-ttu-id="c294c-105">Les parties [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) d’une propriété ou d’un indexeur sont appelées *accesseurs*.</span><span class="sxs-lookup"><span data-stu-id="c294c-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="c294c-106">Par défaut, ces accesseurs ont la visibilité ou le niveau d’accès de la propriété ou de l’indexeur auquel ils appartiennent.</span><span class="sxs-lookup"><span data-stu-id="c294c-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="c294c-107">Pour plus d’informations, consultez [Niveaux d’accessibilité](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c294c-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="c294c-108">Toutefois, il peut parfois s’avérer utile de restreindre l’accès à l’un de ces accesseurs.</span><span class="sxs-lookup"><span data-stu-id="c294c-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="c294c-109">En général, cela implique de restreindre l’accessibilité de l’accesseur `set`, tout en gardant l’accesseur `get` publiquement accessible.</span><span class="sxs-lookup"><span data-stu-id="c294c-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="c294c-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c294c-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="c294c-111">Dans cet exemple, une propriété appelée `Name` définit un accesseur `get` et `set`.</span><span class="sxs-lookup"><span data-stu-id="c294c-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="c294c-112">L’accesseur `get` reçoit le niveau d’accessibilité de la propriété elle-même, `public` dans le cas présent, alors que l’accesseur `set` est restreint explicitement par l’application du modificateur d’accès [protected](../../language-reference/keywords/protected.md) à l’accesseur lui-même.</span><span class="sxs-lookup"><span data-stu-id="c294c-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="c294c-113">Restrictions sur les modificateurs d’accès sur les accesseurs</span><span class="sxs-lookup"><span data-stu-id="c294c-113">Restrictions on Access Modifiers on Accessors</span></span>  

 <span data-ttu-id="c294c-114">L’utilisation de modificateurs d’accesseurs sur les propriétés ou les indexeurs est soumise aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c294c-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="c294c-115">Vous ne pouvez pas utiliser de modificateurs d’accesseur sur une interface ou sur une implémentation de membre d’[interface](../../language-reference/keywords/interface.md) explicite.</span><span class="sxs-lookup"><span data-stu-id="c294c-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="c294c-116">Vous pouvez utiliser les modificateurs d’accesseur uniquement si la propriété ou l’indexeur dispose à la fois d’accesseurs `set` et `get`.</span><span class="sxs-lookup"><span data-stu-id="c294c-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="c294c-117">Dans ce cas, le modificateur est autorisé uniquement sur l’un des deux accesseurs.</span><span class="sxs-lookup"><span data-stu-id="c294c-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="c294c-118">Si la propriété ou l’indexeur possède un modificateur [override](../../language-reference/keywords/override.md), le modificateur d’accesseur doit correspondre à l’accesseur de l’accesseur substitué, le cas échant.</span><span class="sxs-lookup"><span data-stu-id="c294c-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="c294c-119">Le niveau d’accessibilité sur l’accesseur doit être plus restrictif que le niveau d’accessibilité sur la propriété ou l’indexeur eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="c294c-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="c294c-120">Modificateurs d’accès sur les accesseurs de substitution</span><span class="sxs-lookup"><span data-stu-id="c294c-120">Access Modifiers on Overriding Accessors</span></span>  

 <span data-ttu-id="c294c-121">Quand vous substituez une propriété ou un indexeur, les accesseurs remplacés doivent être accessibles au code de substitution.</span><span class="sxs-lookup"><span data-stu-id="c294c-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="c294c-122">Par ailleurs, l’accessibilité de la propriété/l’indexeur et de ses accesseurs doivent correspondre à la propriété/l’indexeur et à ses accesseurs substitués.</span><span class="sxs-lookup"><span data-stu-id="c294c-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="c294c-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c294c-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="c294c-124">Implémentation des interfaces</span><span class="sxs-lookup"><span data-stu-id="c294c-124">Implementing Interfaces</span></span>  

 <span data-ttu-id="c294c-125">Quand vous utilisez un accesseur pour implémenter une interface, l’accesseur peut ne pas avoir de modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="c294c-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="c294c-126">Toutefois, si vous implémentez l’interface à l’aide d’un accesseur, tel que `get`, l’autre accesseur peut avoir un modificateur d’accès, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c294c-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="c294c-127">Domaine d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="c294c-127">Accessor Accessibility Domain</span></span>  

 <span data-ttu-id="c294c-128">Si vous utilisez un modificateur d’accès sur l’accesseur, le [domaine d’accessibilité](../../language-reference/keywords/accessibility-domain.md) de l’accesseur est déterminé par ce modificateur.</span><span class="sxs-lookup"><span data-stu-id="c294c-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="c294c-129">Si vous n’avez pas utilisé un modificateur d’accès sur l’accesseur, le domaine d’accessibilité de l’accesseur est déterminé par le niveau d’accessibilité de la propriété ou de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="c294c-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c294c-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="c294c-130">Example</span></span>  

 <span data-ttu-id="c294c-131">L’exemple suivant contient trois classes, `BaseClass`, `DerivedClass` et `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="c294c-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="c294c-132">Il y a deux propriétés sur `BaseClass`, `Name` et `Id` sur les deux classes.</span><span class="sxs-lookup"><span data-stu-id="c294c-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="c294c-133">L’exemple montre comment la propriété `Id` sur `DerivedClass` peut être masquée par la propriété `Id` sur `BaseClass` quand vous utilisez un modificateur d’accès restrictif tel que [protected](../../language-reference/keywords/protected.md) ou [private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="c294c-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="c294c-134">Par conséquent, quand vous affectez des valeurs à cette propriété, la propriété sur la classe `BaseClass` est appelée à la place.</span><span class="sxs-lookup"><span data-stu-id="c294c-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="c294c-135">Le remplacement du modificateur d’accès par [public](../../language-reference/keywords/public.md) rend la propriété accessible.</span><span class="sxs-lookup"><span data-stu-id="c294c-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="c294c-136">L’exemple montre également qu’un modificateur d’accès restrictif, tel que `private` ou `protected`, sur l’accesseur `set` de la propriété `Name` dans `DerivedClass` empêche l’accès à l’accesseur et génère une erreur quand vous lui affectez une valeur.</span><span class="sxs-lookup"><span data-stu-id="c294c-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="c294c-137">Commentaires</span><span class="sxs-lookup"><span data-stu-id="c294c-137">Comments</span></span>  

 <span data-ttu-id="c294c-138">Notez que si vous remplacez la déclaration `new private string Id` par `new public string Id`, vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c294c-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="c294c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c294c-139">See also</span></span>

- [<span data-ttu-id="c294c-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c294c-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c294c-141">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c294c-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="c294c-142">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="c294c-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="c294c-143">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="c294c-143">Access Modifiers</span></span>](./access-modifiers.md)
