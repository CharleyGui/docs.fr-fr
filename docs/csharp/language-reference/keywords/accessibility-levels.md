---
title: Niveaux d’accessibilité - Référence C#
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602389"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="50847-102">Niveaux d’accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="50847-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="50847-103">Utilisez les modificateurs d’accès `public`, `protected`, `internal` ou `private` pour spécifier l’un des niveaux d’accessibilité déclarés ci-dessous pour les membres.</span><span class="sxs-lookup"><span data-stu-id="50847-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="50847-104">Accessibilité déclarée</span><span class="sxs-lookup"><span data-stu-id="50847-104">Declared accessibility</span></span>|<span data-ttu-id="50847-105">Signification</span><span class="sxs-lookup"><span data-stu-id="50847-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="50847-106">L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="50847-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="50847-107">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="50847-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="50847-108">L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="50847-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="50847-109">L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="50847-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="50847-110">L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="50847-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="50847-111">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="50847-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="50847-112">Disponible depuis C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="50847-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="50847-113">Vous ne pouvez spécifier qu’un seul modificateur d’accès pour un membre ou un type, sauf si vous utilisez les combinaisons `protected internal` ou `private protected`.</span><span class="sxs-lookup"><span data-stu-id="50847-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="50847-114">Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="50847-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="50847-115">Les espaces de noms ne présentent aucune limitation d’accès.</span><span class="sxs-lookup"><span data-stu-id="50847-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="50847-116">Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="50847-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="50847-117">Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="50847-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="50847-118">Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="50847-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="50847-119">L’accessibilité par défaut de ces types est `internal`.</span><span class="sxs-lookup"><span data-stu-id="50847-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="50847-120">Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="50847-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="50847-121">Membres de</span><span class="sxs-lookup"><span data-stu-id="50847-121">Members of</span></span>|<span data-ttu-id="50847-122">Accessibilité par défaut du membre</span><span class="sxs-lookup"><span data-stu-id="50847-122">Default member accessibility</span></span>|<span data-ttu-id="50847-123">Accessibilité déclarée du membre autorisée</span><span class="sxs-lookup"><span data-stu-id="50847-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="50847-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50847-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="50847-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50847-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="50847-126">L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](./accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="50847-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="50847-127">Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="50847-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="50847-128">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="50847-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50847-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50847-129">See also</span></span>

- [<span data-ttu-id="50847-130">Référence C#</span><span class="sxs-lookup"><span data-stu-id="50847-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50847-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="50847-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50847-132">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="50847-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="50847-133">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="50847-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="50847-134">Domaine d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="50847-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="50847-135">Limitations sur l’utilisation des niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="50847-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="50847-136">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="50847-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="50847-137">public</span><span class="sxs-lookup"><span data-stu-id="50847-137">public</span></span>](./public.md)
- [<span data-ttu-id="50847-138">private</span><span class="sxs-lookup"><span data-stu-id="50847-138">private</span></span>](./private.md)
- [<span data-ttu-id="50847-139">protected</span><span class="sxs-lookup"><span data-stu-id="50847-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="50847-140">internal</span><span class="sxs-lookup"><span data-stu-id="50847-140">internal</span></span>](./internal.md)
