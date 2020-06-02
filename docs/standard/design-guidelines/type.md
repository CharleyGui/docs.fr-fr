---
title: Instructions de conception de types
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 17bd300277a039818a3d563c8f2d5f99eb2fc68d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289562"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="39819-102">Instructions de conception de types</span><span class="sxs-lookup"><span data-stu-id="39819-102">Type Design Guidelines</span></span>
<span data-ttu-id="39819-103">Du point de vue du CLR, il n’existe que deux catégories de types : les types référence et les types valeur, mais pour les besoins d’une discussion sur la conception de l’infrastructure, nous dipartissons les types en groupes plus logiques, chacun avec ses propres règles de conception spécifiques.</span><span class="sxs-lookup"><span data-stu-id="39819-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="39819-104">Les classes sont le cas général de types référence.</span><span class="sxs-lookup"><span data-stu-id="39819-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="39819-105">Ils constituent la majeure partie des types dans la majorité des infrastructures.</span><span class="sxs-lookup"><span data-stu-id="39819-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="39819-106">Les classes ont eu la popularité de l’ensemble complet des fonctionnalités orientées objet qu’elles prennent en charge et de leur applicabilité générale.</span><span class="sxs-lookup"><span data-stu-id="39819-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="39819-107">Les classes de base et les classes abstraites sont des groupes logiques spéciaux liés à l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="39819-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="39819-108">Les interfaces sont des types qui peuvent être implémentés par les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="39819-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="39819-109">Ils peuvent ainsi servir de racines de hiérarchies polymorphes de types référence et de types valeur.</span><span class="sxs-lookup"><span data-stu-id="39819-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="39819-110">En outre, les interfaces peuvent être utilisées pour simuler plusieurs héritages, ce qui n’est pas pris en charge en mode natif par le CLR.</span><span class="sxs-lookup"><span data-stu-id="39819-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="39819-111">Les structs sont le cas général des types valeur et doivent être réservés pour les petits types simples, similaires aux primitives de langage.</span><span class="sxs-lookup"><span data-stu-id="39819-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="39819-112">Les enums sont un cas spécial de types valeur utilisés pour définir des jeux de valeurs courts, tels que les jours de la semaine, les couleurs de la console, etc.</span><span class="sxs-lookup"><span data-stu-id="39819-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="39819-113">Les classes statiques sont des types destinés à être des conteneurs pour des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="39819-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="39819-114">Ils sont généralement utilisés pour fournir des raccourcis vers d’autres opérations.</span><span class="sxs-lookup"><span data-stu-id="39819-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="39819-115">Les délégués, les exceptions, les attributs, les tableaux et les collections sont tous des cas spéciaux de types référence destinés à des utilisations spécifiques, et les recommandations relatives à leur conception et à leur utilisation sont décrites ailleurs dans ce document.</span><span class="sxs-lookup"><span data-stu-id="39819-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="39819-116">✔️ Assurez-vous que chaque type est un ensemble bien défini de membres associés, et pas seulement une collection aléatoire de fonctionnalités non liées.</span><span class="sxs-lookup"><span data-stu-id="39819-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="39819-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="39819-117">In This Section</span></span>
 <span data-ttu-id="39819-118">[Choix entre une classe et une structure](choosing-between-class-and-struct.md) [abstraite conception](abstract-class.md) d’une classe [statique](static-class.md) conception d' [interface](interface.md) conception d’une [structure](struct.md) [enum](enum.md) conception des [types imbriqués](nested-types.md) *parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="39819-118">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="39819-119">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="39819-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="39819-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39819-120">See also</span></span>

- [<span data-ttu-id="39819-121">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="39819-121">Framework Design Guidelines</span></span>](index.md)
