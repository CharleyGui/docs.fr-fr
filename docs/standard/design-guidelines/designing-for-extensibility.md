---
title: Conception en vue de l'extensibilité
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 9e75ef433f3bd9af34e8dd40331a8267755e59fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821383"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="f703a-102">Conception en vue de l'extensibilité</span><span class="sxs-lookup"><span data-stu-id="f703a-102">Designing for Extensibility</span></span>
<span data-ttu-id="f703a-103">Un aspect important de la conception d’une infrastructure consiste à s’assurer que l’extensibilité de l’infrastructure a été soigneusement étudiée.</span><span class="sxs-lookup"><span data-stu-id="f703a-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="f703a-104">Cela nécessite que vous compreniez les coûts et les avantages associés à différents mécanismes d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f703a-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="f703a-105">Ce chapitre vous aide à choisir les mécanismes d’extensibilité (sous-classe, événements, membres virtuels, rappels, etc.) qui répondent le mieux aux besoins de votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="f703a-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="f703a-106">Il existe de nombreuses façons d’autoriser l’extensibilité dans les infrastructures.</span><span class="sxs-lookup"><span data-stu-id="f703a-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="f703a-107">Ils vont de moins puissants mais moins coûteux à très puissants, mais onéreux.</span><span class="sxs-lookup"><span data-stu-id="f703a-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="f703a-108">Pour toute exigence d’extensibilité donnée, vous devez choisir le mécanisme d’extensibilité le moins coûteux qui répond aux exigences.</span><span class="sxs-lookup"><span data-stu-id="f703a-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="f703a-109">Gardez à l’esprit qu’il est généralement possible d’ajouter plus d’extensibilité ultérieurement, mais vous ne pouvez jamais le retirer sans introduire de modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="f703a-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f703a-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f703a-110">In This Section</span></span>  
 [<span data-ttu-id="f703a-111">Classes non scellées</span><span class="sxs-lookup"><span data-stu-id="f703a-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="f703a-112">Membres protégés</span><span class="sxs-lookup"><span data-stu-id="f703a-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="f703a-113">Événements et rappels</span><span class="sxs-lookup"><span data-stu-id="f703a-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="f703a-114">Membres virtuels</span><span class="sxs-lookup"><span data-stu-id="f703a-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="f703a-115">Abstractions (types et interfaces abstraits)</span><span class="sxs-lookup"><span data-stu-id="f703a-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="f703a-116">Classes de base pour l’implémentation d’abstractions</span><span class="sxs-lookup"><span data-stu-id="f703a-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="f703a-117">Sceller</span><span class="sxs-lookup"><span data-stu-id="f703a-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="f703a-118">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="f703a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f703a-119">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f703a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f703a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f703a-120">See also</span></span>

- [<span data-ttu-id="f703a-121">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="f703a-121">Framework Design Guidelines</span></span>](index.md)
