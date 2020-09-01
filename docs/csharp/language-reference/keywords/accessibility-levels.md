---
description: Niveaux d’accessibilité - Référence C#
title: Niveaux d’accessibilité - Référence C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26b8f78595b1406deb371113cf491b80ad7c1474
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127020"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="d8f0c-103">Niveaux d’accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d8f0c-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="d8f0c-104">Utilisez les modificateurs d’accès `public`, `protected`, `internal` ou `private` pour spécifier l’un des niveaux d’accessibilité déclarés ci-dessous pour les membres.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="d8f0c-105">Accessibilité déclarée</span><span class="sxs-lookup"><span data-stu-id="d8f0c-105">Declared accessibility</span></span>|<span data-ttu-id="d8f0c-106">Signification</span><span class="sxs-lookup"><span data-stu-id="d8f0c-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="d8f0c-107">L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="d8f0c-108">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="d8f0c-109">L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="d8f0c-110">L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="d8f0c-111">L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="d8f0c-112">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="d8f0c-113">Disponible depuis C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="d8f0c-114">Vous ne pouvez spécifier qu’un seul modificateur d’accès pour un membre ou un type, sauf si vous utilisez les combinaisons `protected internal` ou `private protected`.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="d8f0c-115">Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="d8f0c-116">Les espaces de noms ne présentent aucune limitation d’accès.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="d8f0c-117">Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="d8f0c-118">Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="d8f0c-119">Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="d8f0c-120">L’accessibilité par défaut de ces types est `internal`.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="d8f0c-121">Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="d8f0c-122">Membres de</span><span class="sxs-lookup"><span data-stu-id="d8f0c-122">Members of</span></span>|<span data-ttu-id="d8f0c-123">Accessibilité par défaut du membre</span><span class="sxs-lookup"><span data-stu-id="d8f0c-123">Default member accessibility</span></span>|<span data-ttu-id="d8f0c-124">Accessibilité déclarée du membre autorisée</span><span class="sxs-lookup"><span data-stu-id="d8f0c-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="d8f0c-125">None</span><span class="sxs-lookup"><span data-stu-id="d8f0c-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="d8f0c-126">None</span><span class="sxs-lookup"><span data-stu-id="d8f0c-126">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="d8f0c-127">L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](./accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="d8f0c-128">Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="d8f0c-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d8f0c-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d8f0c-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8f0c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f0c-130">See also</span></span>

- [<span data-ttu-id="d8f0c-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d8f0c-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d8f0c-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d8f0c-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d8f0c-133">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="d8f0c-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d8f0c-134">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="d8f0c-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="d8f0c-135">Domaine d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="d8f0c-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="d8f0c-136">Restrictions concernant l’utilisation des niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="d8f0c-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="d8f0c-137">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="d8f0c-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="d8f0c-138">public</span><span class="sxs-lookup"><span data-stu-id="d8f0c-138">public</span></span>](./public.md)
- [<span data-ttu-id="d8f0c-139">priv</span><span class="sxs-lookup"><span data-stu-id="d8f0c-139">private</span></span>](./private.md)
- [<span data-ttu-id="d8f0c-140">protected</span><span class="sxs-lookup"><span data-stu-id="d8f0c-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="d8f0c-141">intérieurs</span><span class="sxs-lookup"><span data-stu-id="d8f0c-141">internal</span></span>](./internal.md)
