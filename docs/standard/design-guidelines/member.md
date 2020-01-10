---
title: Instructions de conception des membres
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: cf4f1d2fee73e3e65dc4d92ea97a62f4a7e4c4e5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709268"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="5bdf0-102">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="5bdf0-102">Member Design Guidelines</span></span>
<span data-ttu-id="5bdf0-103">Les méthodes, propriétés, événements, constructeurs et champs sont collectivement appelés membres.</span><span class="sxs-lookup"><span data-stu-id="5bdf0-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="5bdf0-104">Les membres sont finalement les moyens par lesquels les fonctionnalités de l’infrastructure sont exposées aux utilisateurs finaux d’une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="5bdf0-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="5bdf0-105">Les membres peuvent être virtuels ou non virtuels, concrets ou abstraits, statiques ou d’instance et peuvent avoir plusieurs étendues d’accessibilité différentes.</span><span class="sxs-lookup"><span data-stu-id="5bdf0-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="5bdf0-106">Toute cette variété offre une expressivité incroyable, mais dans le même temps, vous devez faire attention à la partie du concepteur de Framework.</span><span class="sxs-lookup"><span data-stu-id="5bdf0-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="5bdf0-107">Ce chapitre propose des instructions de base qui doivent être suivies lors de la conception de membres de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="5bdf0-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5bdf0-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5bdf0-108">In This Section</span></span>  
 [<span data-ttu-id="5bdf0-109">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="5bdf0-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="5bdf0-110">Conception des propriétés</span><span class="sxs-lookup"><span data-stu-id="5bdf0-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="5bdf0-111">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="5bdf0-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="5bdf0-112">Conception d’événements</span><span class="sxs-lookup"><span data-stu-id="5bdf0-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="5bdf0-113">Conception de champs</span><span class="sxs-lookup"><span data-stu-id="5bdf0-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="5bdf0-114">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="5bdf0-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="5bdf0-115">Surcharges d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="5bdf0-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="5bdf0-116">Conception de paramètres</span><span class="sxs-lookup"><span data-stu-id="5bdf0-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="5bdf0-117">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="5bdf0-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5bdf0-118">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5bdf0-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdf0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bdf0-119">See also</span></span>

- [<span data-ttu-id="5bdf0-120">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5bdf0-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
