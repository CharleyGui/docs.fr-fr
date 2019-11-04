---
title: Modificateurs d’accès - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 7dfbc103b3fd0ebf8c349bd36dc54915782eb807
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422938"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="eba08-102">Modificateurs d’accès (référence C#)</span><span class="sxs-lookup"><span data-stu-id="eba08-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="eba08-103">Les modificateurs d’accès sont des mots clés utilisés pour spécifier l’accessibilité déclarée d’un membre ou d’un type.</span><span class="sxs-lookup"><span data-stu-id="eba08-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="eba08-104">Cette section présente les quatre modificateurs d’accès :</span><span class="sxs-lookup"><span data-stu-id="eba08-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="eba08-105">Les modificateurs d’accès permettent de spécifier les six niveaux d’accessibilité suivants :</span><span class="sxs-lookup"><span data-stu-id="eba08-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="eba08-106">[`public`](public.md) : l’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="eba08-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="eba08-107">[`protected`](protected.md) : l’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="eba08-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="eba08-108">[`internal`](internal.md) : l’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="eba08-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="eba08-109">[`protected internal`](protected-internal.md) : l’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="eba08-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="eba08-110">[`private`](private.md) : l’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="eba08-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="eba08-111">[`private protected`](private-protected.md) : l’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="eba08-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="eba08-112">Cette section introduit également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="eba08-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="eba08-113">[Niveaux d’accessibilité](./accessibility-levels.md) : utilisation des quatre modificateurs d’accès pour déclarer six niveaux d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="eba08-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="eba08-114">[Domaine d’accessibilité](./accessibility-domain.md) : spécifie où, dans les sections du programme, un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="eba08-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="eba08-115">[Limitations sur l’utilisation des niveaux d’accessibilité](./restrictions-on-using-accessibility-levels.md) : résumé des restrictions sur l’utilisation des niveaux d’accessibilité déclarés.</span><span class="sxs-lookup"><span data-stu-id="eba08-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba08-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eba08-116">See also</span></span>

- [<span data-ttu-id="eba08-117">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="eba08-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eba08-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="eba08-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eba08-119">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="eba08-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="eba08-120">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="eba08-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="eba08-121">Mots clés d’accès</span><span class="sxs-lookup"><span data-stu-id="eba08-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="eba08-122">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="eba08-122">Modifiers</span></span>](index.md)
