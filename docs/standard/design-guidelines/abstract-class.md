---
title: Conception de classes abstraites
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709593"
---
# <a name="abstract-class-design"></a><span data-ttu-id="3c84b-102">Conception de classes abstraites</span><span class="sxs-lookup"><span data-stu-id="3c84b-102">Abstract Class Design</span></span>
<span data-ttu-id="3c84b-103">**X DO NOT** définir des constructeurs internes publiques ou protégées dans les types abstraits.</span><span class="sxs-lookup"><span data-stu-id="3c84b-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="3c84b-104">Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type.</span><span class="sxs-lookup"><span data-stu-id="3c84b-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="3c84b-105">Étant donné que vous ne pouvez pas créer d’instances d’un type abstrait, un type abstrait avec un constructeur public n’est pas correctement conçu et trompe les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="3c84b-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="3c84b-106">**✓ DO** définir un document protégé ou un constructeur interne dans les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="3c84b-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="3c84b-107">Un constructeur protégé est plus courant et permet simplement à la classe de base d’effectuer sa propre initialisation lors de la création de sous-types.</span><span class="sxs-lookup"><span data-stu-id="3c84b-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="3c84b-108">Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly qui définit la classe.</span><span class="sxs-lookup"><span data-stu-id="3c84b-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="3c84b-109">**✓ DO** fournir au moins un type concret qui hérite de chaque classe abstraite qui vous sont fournis.</span><span class="sxs-lookup"><span data-stu-id="3c84b-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="3c84b-110">Cela permet de valider la conception de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="3c84b-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="3c84b-111">Par exemple, <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la classe abstraite <xref:System.IO.Stream?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3c84b-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="3c84b-112">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="3c84b-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3c84b-113">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="3c84b-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c84b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c84b-114">See also</span></span>

- [<span data-ttu-id="3c84b-115">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="3c84b-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="3c84b-116">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c84b-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
