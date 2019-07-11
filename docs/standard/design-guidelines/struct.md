---
title: Conception de structures
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: e787c5b34848a561b43c3457341673f11cc2bd00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775547"
---
# <a name="struct-design"></a><span data-ttu-id="8f5ee-102">Conception de structures</span><span class="sxs-lookup"><span data-stu-id="8f5ee-102">Struct Design</span></span>
<span data-ttu-id="8f5ee-103">Le type de valeur à usage général est souvent appelé un struct, son mot-clé c#.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="8f5ee-104">Cette section fournit des instructions pour la conception de la structure générale.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="8f5ee-105">**X ne sont pas** fournir un constructeur sans paramètre pour un struct.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-105">**X DO NOT** provide a parameterless constructor for a struct.</span></span>  
  
 <span data-ttu-id="8f5ee-106">Suivant cette recommandation permet de tableaux de structs peuvent être créés sans avoir à exécuter le constructeur sur chaque élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="8f5ee-107">Notez que C# n’autorise pas les structs peuvent avoir des constructeurs sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>  
  
 <span data-ttu-id="8f5ee-108">**X DO NOT** définissent les types de valeur mutable.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="8f5ee-109">Types de valeur mutable ont plusieurs problèmes.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-109">Mutable value types have several problems.</span></span> <span data-ttu-id="8f5ee-110">Par exemple, lorsqu’un accesseur Get de propriété retourne un type valeur, l’appelant reçoit une copie.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="8f5ee-111">Étant donné que la copie est créée implicitement, les développeurs connaissez peut-être pas qu’ils sont de mutation la copie et non la valeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="8f5ee-112">En outre, certains langages (langages dynamiques, en particulier) ont des problèmes à l’aide de types valeur mutable, car même les variables locales, lorsqu’il est déréférencé, provoquer une copie qu’il veut.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="8f5ee-113">**✓ DO** s’assurer qu’un état où toutes les données de l’instance est défini sur zéro, false ou null (le cas échéant) est valide.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="8f5ee-114">Cela empêche la création accidentelle d’instances non valides lors de la création d’un tableau des structs.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="8f5ee-115">**✓ DO** implémenter <xref:System.IEquatable%601> sur les types valeur.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="8f5ee-116">Le <xref:System.Object.Equals%2A?displayProperty=nameWithType> (méthode) sur les types valeur entraîne la conversion boxing et son implémentation par défaut n’est pas très efficace, car il utilise la réflexion.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="8f5ee-117"><xref:System.IEquatable%601.Equals%2A> peut avoir de meilleures performances et peut être implémentée afin qu’elle n’entraîne pas de boxing.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="8f5ee-118">**X DO NOT** prolonger explicitement <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="8f5ee-119">En fait, la plupart des langages éviter ce problème.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="8f5ee-120">En général, les structs peuvent être très utiles mais ne doit être utilisées que pour les valeurs de petite, unique et immuables qui ne seront pas boxed fréquemment.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="8f5ee-121">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="8f5ee-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8f5ee-122">*Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8f5ee-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5ee-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f5ee-123">See also</span></span>

- [<span data-ttu-id="8f5ee-124">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="8f5ee-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="8f5ee-125">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f5ee-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8f5ee-126">Choix entre classe et structure</span><span class="sxs-lookup"><span data-stu-id="8f5ee-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
