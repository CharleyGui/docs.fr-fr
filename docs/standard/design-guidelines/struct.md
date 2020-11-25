---
title: Conception de structures
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: 7bb7e63004df2eb7541ba8d4f1118ea2272db126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730901"
---
# <a name="struct-design"></a><span data-ttu-id="b1831-102">Conception de structures</span><span class="sxs-lookup"><span data-stu-id="b1831-102">Struct Design</span></span>

<span data-ttu-id="b1831-103">Le type de valeur à usage général est le plus souvent appelé struct, son mot clé C#.</span><span class="sxs-lookup"><span data-stu-id="b1831-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="b1831-104">Cette section fournit des instructions pour la conception générale des structs.</span><span class="sxs-lookup"><span data-stu-id="b1831-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="b1831-105">❌ NE fournissez pas de constructeur sans paramètre pour un struct.</span><span class="sxs-lookup"><span data-stu-id="b1831-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="b1831-106">Le respect de cette règle permet de créer des tableaux de structs sans avoir à exécuter le constructeur sur chaque élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="b1831-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="b1831-107">Notez que C# n’autorise pas les structs à avoir des constructeurs sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="b1831-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="b1831-108">❌ NE définissez pas de types valeur mutable.</span><span class="sxs-lookup"><span data-stu-id="b1831-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="b1831-109">Les types valeur mutable présentent plusieurs problèmes.</span><span class="sxs-lookup"><span data-stu-id="b1831-109">Mutable value types have several problems.</span></span> <span data-ttu-id="b1831-110">Par exemple, lorsqu’un accesseur Get de propriété retourne un type valeur, l’appelant reçoit une copie.</span><span class="sxs-lookup"><span data-stu-id="b1831-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="b1831-111">Étant donné que la copie est créée implicitement, les développeurs peuvent ne pas savoir qu’ils font muter la copie, et non la valeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="b1831-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="b1831-112">En outre, certains langages (Dynamic Languages, en particulier) rencontrent des problèmes lors de l’utilisation des types valeur mutables, car même les variables locales, lorsqu’elles sont déréférencées, provoquent une copie.</span><span class="sxs-lookup"><span data-stu-id="b1831-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="b1831-113">✔️ Assurez-vous qu’un État dans lequel toutes les données d’instance est définie sur zéro, false ou null (selon le cas) est valide.</span><span class="sxs-lookup"><span data-stu-id="b1831-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="b1831-114">Cela empêche la création accidentelle d’instances non valides lorsqu’un tableau de structs est créé.</span><span class="sxs-lookup"><span data-stu-id="b1831-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="b1831-115">✔️ implémenter <xref:System.IEquatable%601> sur des types valeur.</span><span class="sxs-lookup"><span data-stu-id="b1831-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="b1831-116">La <xref:System.Object.Equals%2A?displayProperty=nameWithType> méthode sur les types valeur provoque un boxing, et son implémentation par défaut n’est pas très efficace, car elle utilise la réflexion.</span><span class="sxs-lookup"><span data-stu-id="b1831-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="b1831-117"><xref:System.IEquatable%601.Equals%2A> peut offrir de meilleures performances et peut être implémentée pour ne pas provoquer de conversion boxing.</span><span class="sxs-lookup"><span data-stu-id="b1831-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="b1831-118">❌ N’étendez pas explicitement <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="b1831-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="b1831-119">En fait, la plupart des langues l’empêchent.</span><span class="sxs-lookup"><span data-stu-id="b1831-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="b1831-120">En général, les structs peuvent être très utiles, mais ne doivent être utilisés que pour des valeurs petites, uniques et immuables qui ne seront pas converties fréquemment.</span><span class="sxs-lookup"><span data-stu-id="b1831-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="b1831-121">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="b1831-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b1831-122">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b1831-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b1831-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1831-123">See also</span></span>

- [<span data-ttu-id="b1831-124">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="b1831-124">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="b1831-125">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="b1831-125">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="b1831-126">Choix entre classe et structure</span><span class="sxs-lookup"><span data-stu-id="b1831-126">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)
