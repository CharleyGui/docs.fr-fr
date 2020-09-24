---
description: Modificateurs d’accès - Référence C#
title: Modificateurs d’accès - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: e941fc673c508f10863ee49b6544d6886bd594a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168814"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="2cdfd-103">Modificateurs d’accès (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2cdfd-103">Access Modifiers (C# Reference)</span></span>

<span data-ttu-id="2cdfd-104">Les modificateurs d’accès sont des mots clés utilisés pour spécifier l’accessibilité déclarée d’un membre ou d’un type.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="2cdfd-105">Cette section présente les quatre modificateurs d’accès :</span><span class="sxs-lookup"><span data-stu-id="2cdfd-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="2cdfd-106">Les modificateurs d’accès permettent de spécifier les six niveaux d’accessibilité suivants :</span><span class="sxs-lookup"><span data-stu-id="2cdfd-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="2cdfd-107">[`public`](public.md): L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="2cdfd-108">[`protected`](protected.md): L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="2cdfd-109">[`internal`](internal.md): L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="2cdfd-110">[`protected internal`](protected-internal.md): L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="2cdfd-111">[`private`](private.md): L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="2cdfd-112">[`private protected`](private-protected.md): L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="2cdfd-113">Cette section introduit également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2cdfd-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="2cdfd-114">[Niveaux d’accessibilité](./accessibility-levels.md) : utilisation des quatre modificateurs d’accès pour déclarer six niveaux d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="2cdfd-115">[Domaine d’accessibilité](./accessibility-domain.md) : spécifie où, dans les sections du programme, un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="2cdfd-116">[Limitations sur l’utilisation des niveaux d’accessibilité](./restrictions-on-using-accessibility-levels.md) : résumé des restrictions sur l’utilisation des niveaux d’accessibilité déclarés.</span><span class="sxs-lookup"><span data-stu-id="2cdfd-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cdfd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cdfd-117">See also</span></span>

- [<span data-ttu-id="2cdfd-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="2cdfd-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2cdfd-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2cdfd-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2cdfd-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="2cdfd-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2cdfd-121">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="2cdfd-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="2cdfd-122">Mots clés d'accès</span><span class="sxs-lookup"><span data-stu-id="2cdfd-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="2cdfd-123">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="2cdfd-123">Modifiers</span></span>](index.md)
