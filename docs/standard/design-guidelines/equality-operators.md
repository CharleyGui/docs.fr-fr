---
title: Opérateurs d'égalité
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741693"
---
# <a name="equality-operators"></a><span data-ttu-id="af6c4-102">Opérateurs d'égalité</span><span class="sxs-lookup"><span data-stu-id="af6c4-102">Equality Operators</span></span>
<span data-ttu-id="af6c4-103">Cette section traite de la surcharge des opérateurs d’égalité et fait référence à `operator==` et `operator!=` en tant qu’opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="af6c4-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="af6c4-104">❌ ne surchargent pas l’un des opérateurs d’égalité et non l’autre.</span><span class="sxs-lookup"><span data-stu-id="af6c4-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="af6c4-105">✔️ Assurez-vous que <xref:System.Object.Equals%2A?displayProperty=nameWithType> et les opérateurs d’égalité ont exactement la même sémantique et les mêmes caractéristiques de performances similaires.</span><span class="sxs-lookup"><span data-stu-id="af6c4-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="af6c4-106">Cela signifie souvent que `Object.Equals` doit être substitué lorsque les opérateurs d’égalité sont surchargés.</span><span class="sxs-lookup"><span data-stu-id="af6c4-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="af6c4-107">❌ éviter de lever des exceptions à partir d’opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="af6c4-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="af6c4-108">Par exemple, retourne false si l’un des arguments a la valeur null au lieu de lever `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="af6c4-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="af6c4-109">Opérateurs d’égalité sur les types valeur</span><span class="sxs-lookup"><span data-stu-id="af6c4-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="af6c4-110">✔️ surchargent les opérateurs d’égalité sur les types valeur, si l’égalité est significative.</span><span class="sxs-lookup"><span data-stu-id="af6c4-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="af6c4-111">Dans la plupart des langages de programmation, il n’y a pas d’implémentation par défaut de `operator==` pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="af6c4-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="af6c4-112">Opérateurs d’égalité sur les types référence</span><span class="sxs-lookup"><span data-stu-id="af6c4-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="af6c4-113">❌ éviter de surcharger les opérateurs d’égalité sur les types référence mutables.</span><span class="sxs-lookup"><span data-stu-id="af6c4-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="af6c4-114">De nombreux langages ont des opérateurs d’égalité intégrés pour les types référence.</span><span class="sxs-lookup"><span data-stu-id="af6c4-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="af6c4-115">Les opérateurs intégrés implémentent généralement l’égalité des références, et de nombreux développeurs sont surpris lorsque le comportement par défaut est remplacé par l’égalité de la valeur.</span><span class="sxs-lookup"><span data-stu-id="af6c4-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="af6c4-116">Ce problème est atténué pour les types référence immuables, car l’immuabilité rend beaucoup plus difficile la différence entre l’égalité des références et l’égalité des valeurs.</span><span class="sxs-lookup"><span data-stu-id="af6c4-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="af6c4-117">❌ éviter de surcharger les opérateurs d’égalité sur les types référence si l’implémentation est beaucoup plus lente que celle de l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="af6c4-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="af6c4-118">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="af6c4-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="af6c4-119">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="af6c4-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="af6c4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af6c4-120">See also</span></span>

- [<span data-ttu-id="af6c4-121">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af6c4-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="af6c4-122">Indications relatives à l’utilisation</span><span class="sxs-lookup"><span data-stu-id="af6c4-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
