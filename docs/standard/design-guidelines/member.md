---
title: Instructions de conception des membres
description: Découvrez les instructions de conception des membres dans .NET. Les membres incluent des méthodes, des propriétés, des événements, des constructeurs et des champs.
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: 5070f45beccd89d6f051f1b1d8345390e915d471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706591"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="4a974-104">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="4a974-104">Member Design Guidelines</span></span>

<span data-ttu-id="4a974-105">Les méthodes, propriétés, événements, constructeurs et champs sont collectivement appelés membres.</span><span class="sxs-lookup"><span data-stu-id="4a974-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="4a974-106">Les membres sont finalement les moyens par lesquels les fonctionnalités de l’infrastructure sont exposées aux utilisateurs finaux d’une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="4a974-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="4a974-107">Les membres peuvent être virtuels ou non virtuels, concrets ou abstraits, statiques ou d’instance et peuvent avoir plusieurs étendues d’accessibilité différentes.</span><span class="sxs-lookup"><span data-stu-id="4a974-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="4a974-108">Toute cette variété offre une expressivité incroyable, mais dans le même temps, vous devez faire attention à la partie du concepteur de Framework.</span><span class="sxs-lookup"><span data-stu-id="4a974-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="4a974-109">Ce chapitre propose des instructions de base qui doivent être suivies lors de la conception de membres de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="4a974-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a974-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4a974-110">In This Section</span></span>  

 [<span data-ttu-id="4a974-111">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="4a974-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="4a974-112">Conception des propriétés</span><span class="sxs-lookup"><span data-stu-id="4a974-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="4a974-113">Conception de constructeur</span><span class="sxs-lookup"><span data-stu-id="4a974-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="4a974-114">Conception des événements</span><span class="sxs-lookup"><span data-stu-id="4a974-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="4a974-115">Conception de champs</span><span class="sxs-lookup"><span data-stu-id="4a974-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="4a974-116">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="4a974-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="4a974-117">Surcharges d’opérateur</span><span class="sxs-lookup"><span data-stu-id="4a974-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="4a974-118">Conception de paramètres</span><span class="sxs-lookup"><span data-stu-id="4a974-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="4a974-119">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="4a974-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4a974-120">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4a974-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a974-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a974-121">See also</span></span>

- [<span data-ttu-id="4a974-122">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="4a974-122">Framework Design Guidelines</span></span>](index.md)
