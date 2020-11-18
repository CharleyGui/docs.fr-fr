---
title: Conception de classes statiques
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: efa5ca6e7b5e7b7d03cbe1d55471a388f3faab37
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828658"
---
# <a name="static-class-design"></a><span data-ttu-id="2398c-102">Conception de classes statiques</span><span class="sxs-lookup"><span data-stu-id="2398c-102">Static Class Design</span></span>
<span data-ttu-id="2398c-103">Une classe statique est définie en tant que classe qui contient uniquement des membres statiques (bien entendu, outre les membres d’instance hérités de <xref:System.Object?displayProperty=nameWithType> et éventuellement un constructeur privé).</span><span class="sxs-lookup"><span data-stu-id="2398c-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="2398c-104">Certains langages fournissent une prise en charge intégrée des classes statiques.</span><span class="sxs-lookup"><span data-stu-id="2398c-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="2398c-105">En C# 2,0 et versions ultérieures, lorsqu’une classe est déclarée comme étant statique, elle est sealed, abstract, et aucun membre d’instance ne peut être substitué ou déclaré.</span><span class="sxs-lookup"><span data-stu-id="2398c-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="2398c-106">Les classes statiques sont un compromis entre une conception pure orientée objet et une simplicité.</span><span class="sxs-lookup"><span data-stu-id="2398c-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="2398c-107">Elles sont généralement utilisées pour fournir des raccourcis vers d’autres opérations (telles que <xref:System.IO.File?displayProperty=nameWithType> ), des détenteurs de méthodes d’extension ou des fonctionnalités pour lesquelles un wrapper orienté objet complet n’est pas justifié (comme <xref:System.Environment?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="2398c-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="2398c-108">✔️ utiliser des classes statiques avec modération.</span><span class="sxs-lookup"><span data-stu-id="2398c-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="2398c-109">Les classes statiques doivent être utilisées uniquement comme classes de prise en charge pour le noyau orienté objet de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="2398c-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="2398c-110">❌ NE traitez pas les classes statiques comme un compartiment divers.</span><span class="sxs-lookup"><span data-stu-id="2398c-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="2398c-111">❌ NE déclarez pas ou ne substituez pas de membres d’instance dans des classes statiques.</span><span class="sxs-lookup"><span data-stu-id="2398c-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="2398c-112">✔️ déclarez des classes statiques comme sealed, abstract et ajoutez un constructeur d’instance privé si votre langage de programmation n’a pas de prise en charge intégrée des classes statiques.</span><span class="sxs-lookup"><span data-stu-id="2398c-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="2398c-113">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="2398c-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2398c-114">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2398c-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2398c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2398c-115">See also</span></span>

- [<span data-ttu-id="2398c-116">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="2398c-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="2398c-117">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="2398c-117">Framework Design Guidelines</span></span>](index.md)
