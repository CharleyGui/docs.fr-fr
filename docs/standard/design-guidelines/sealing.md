---
title: Sceller
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: f25573c0fef29ef54dc04c5287757903429d89d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615198"
---
# <a name="sealing"></a><span data-ttu-id="39574-102">Sceller</span><span class="sxs-lookup"><span data-stu-id="39574-102">Sealing</span></span>
<span data-ttu-id="39574-103">L’une des fonctionnalités d’infrastructures et orienté objet est que les développeurs peuvent étendre et personnaliser les manières imprévus par les concepteurs de framework.</span><span class="sxs-lookup"><span data-stu-id="39574-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="39574-104">Il s’agit la puissance et le risque de conception extensible.</span><span class="sxs-lookup"><span data-stu-id="39574-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="39574-105">Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement pour l’extensibilité lorsqu’il est nécessaire et pour limiter l’extensibilité lorsqu’il est dangereux.</span><span class="sxs-lookup"><span data-stu-id="39574-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="39574-106">Scellement d’un mécanisme puissant qui empêche d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="39574-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="39574-107">Vous pouvez sceller la classe ou des membres individuels.</span><span class="sxs-lookup"><span data-stu-id="39574-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="39574-108">Sceller une classe empêche les utilisateurs d’en hériter de la classe.</span><span class="sxs-lookup"><span data-stu-id="39574-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="39574-109">Le fait de sceller un membre empêche les utilisateurs de remplacer un membre particulier.</span><span class="sxs-lookup"><span data-stu-id="39574-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="39574-110">**X DO NOT** sceller des classes sans avoir une bonne raison de le faire.</span><span class="sxs-lookup"><span data-stu-id="39574-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="39574-111">Le fait de sceller une classe, car vous ne pouvez pas considérer un scénario d’extensibilité n’est pas une bonne raison.</span><span class="sxs-lookup"><span data-stu-id="39574-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="39574-112">Framework d’utilisateurs apprécient de hériter de classes pour diverses raisons identifiable, comme l’ajout de membres de commodité.</span><span class="sxs-lookup"><span data-stu-id="39574-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="39574-113">Consultez [Classes Unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md) pour obtenir des exemples de raisons identifiable les utilisateurs souhaitent hériter d’un type.</span><span class="sxs-lookup"><span data-stu-id="39574-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="39574-114">Bonnes raisons pour sceller une classe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="39574-114">Good reasons for sealing a class include the following:</span></span>  
  
- <span data-ttu-id="39574-115">La classe est une classe statique.</span><span class="sxs-lookup"><span data-stu-id="39574-115">The class is a static class.</span></span> <span data-ttu-id="39574-116">Consultez [conception de classes statiques](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="39574-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
- <span data-ttu-id="39574-117">La classe stocke les clés secrètes sensibles à la sécurité dans les membres protégés hérités.</span><span class="sxs-lookup"><span data-stu-id="39574-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
- <span data-ttu-id="39574-118">La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement serait dépassent les avantages de la classe non scellés.</span><span class="sxs-lookup"><span data-stu-id="39574-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
- <span data-ttu-id="39574-119">La classe est un attribut qui nécessite la recherche d’exécution très rapide.</span><span class="sxs-lookup"><span data-stu-id="39574-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="39574-120">Attributs sealed ont des niveaux de performances légèrement plus élevés que ceux non scellé.</span><span class="sxs-lookup"><span data-stu-id="39574-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="39574-121">consultez [attributs](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="39574-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="39574-122">**X DO NOT** déclarer les membres virtuels ou protégés sur les types sealed.</span><span class="sxs-lookup"><span data-stu-id="39574-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="39574-123">Par définition, les types sealed ne peut pas être héritées.</span><span class="sxs-lookup"><span data-stu-id="39574-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="39574-124">Cela signifie que les membres protégés sur les types sealed ne peut pas être appelées, et les méthodes virtuelles sur les types sealed ne peut pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="39574-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="39574-125">**✓ CONSIDER** sceller les membres que vous substituez.</span><span class="sxs-lookup"><span data-stu-id="39574-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="39574-126">Les problèmes qui peuvent résulter de présentation de membres virtuels (abordées dans [membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)) s’appliquent aux remplacements de même, bien qu’à un degré légèrement moindre.</span><span class="sxs-lookup"><span data-stu-id="39574-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="39574-127">Le fait de sceller un remplacement vous protège ces problèmes à partir de ce point dans la hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="39574-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="39574-128">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="39574-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="39574-129">*Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="39574-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39574-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39574-130">See also</span></span>

- [<span data-ttu-id="39574-131">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39574-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="39574-132">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="39574-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="39574-133">Classes unsealed</span><span class="sxs-lookup"><span data-stu-id="39574-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
