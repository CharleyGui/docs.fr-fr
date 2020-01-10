---
title: Noms d'espaces de noms
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709229"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="ec449-102">Noms d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="ec449-102">Names of Namespaces</span></span>
<span data-ttu-id="ec449-103">Comme pour les autres instructions d’affectation de noms, l’objectif de l’attribution de noms aux espaces de noms est de créer suffisamment de clarté pour le programmeur qui utilise l’infrastructure pour savoir immédiatement ce que le contenu de l’espace de noms est susceptible d’être.</span><span class="sxs-lookup"><span data-stu-id="ec449-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="ec449-104">Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="ec449-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="ec449-105">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="ec449-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="ec449-106">**✓ DO** faites précéder les noms d’espace de noms avec un nom de société pour empêcher les espaces de noms provenant de différentes sociétés de ne pas avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="ec449-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="ec449-107">**✓ DO** utiliser un nom de produit indépendant de la version stable au deuxième niveau d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ec449-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="ec449-108">**X DO NOT** utiliser des hiérarchies d’organisation comme base pour les noms dans les hiérarchies de l’espace de noms, étant donné que les noms de groupe au sein des entreprises ont tendance à être de courte durée de vie.</span><span class="sxs-lookup"><span data-stu-id="ec449-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="ec449-109">Organiser la hiérarchie des espaces de noms autour des groupes de technologies associées.</span><span class="sxs-lookup"><span data-stu-id="ec449-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="ec449-110">**✓ DO** utilisent la casse Pascal et des composants de l’espace de noms distinct avec des périodes (par exemple, `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="ec449-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="ec449-111">Si votre personnalisation utilise une casse qui n’est pas traditionnelle, vous devez suivre la casse définie par votre personnalisation, même si elle diffère de la casse normale des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="ec449-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="ec449-112">**✓ CONSIDER** à l’aide de noms au pluriel, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ec449-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="ec449-113">Par exemple, utilisez `System.Collections` à la place de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="ec449-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="ec449-114">Toutefois, les noms et les acronymes sont des exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="ec449-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="ec449-115">Par exemple, utilisez `System.IO` à la place de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="ec449-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="ec449-116">**X DO NOT** utiliser le même nom pour un espace de noms et un type dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ec449-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="ec449-117">Par exemple, n’utilisez pas `Debug` comme nom d’espace de noms, puis fournissez également une classe nommée `Debug` dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ec449-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="ec449-118">Plusieurs compilateurs requièrent que ces types soient qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="ec449-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="ec449-119">Conflits d’espaces de noms et de noms de types</span><span class="sxs-lookup"><span data-stu-id="ec449-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="ec449-120">**X DO NOT** présentent des noms de type générique comme `Element`, `Node`, `Log`, et `Message`.</span><span class="sxs-lookup"><span data-stu-id="ec449-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="ec449-121">Il y a une très grande probabilité que cela entraîne des conflits de noms de types dans les scénarios courants.</span><span class="sxs-lookup"><span data-stu-id="ec449-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="ec449-122">Vous devez qualifier les noms de types génériques (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="ec449-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="ec449-123">Il existe des instructions spécifiques pour éviter les conflits de noms de types pour différentes catégories d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="ec449-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="ec449-124">**Espaces de noms du modèle d’application**</span><span class="sxs-lookup"><span data-stu-id="ec449-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="ec449-125">Les espaces de noms appartenant à un modèle d’application unique sont souvent utilisés ensemble, mais ils ne sont jamais utilisés avec des espaces de noms d’autres modèles d’application.</span><span class="sxs-lookup"><span data-stu-id="ec449-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="ec449-126">Par exemple, l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> est très rarement utilisé avec l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ec449-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ec449-127">Voici une liste de groupes d’espaces de noms de modèle d’application connus :</span><span class="sxs-lookup"><span data-stu-id="ec449-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="ec449-128">**X DO NOT** donner le même nom aux types dans les espaces de noms dans un modèle d’application unique.</span><span class="sxs-lookup"><span data-stu-id="ec449-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="ec449-129">Par exemple, n’ajoutez pas de type nommé `Page` à l’espace de noms <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, car l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType> contient déjà un type nommé `Page`.</span><span class="sxs-lookup"><span data-stu-id="ec449-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="ec449-130">**Espaces de noms d’infrastructure**</span><span class="sxs-lookup"><span data-stu-id="ec449-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="ec449-131">Ce groupe contient des espaces de noms rarement importés pendant le développement d’applications courantes.</span><span class="sxs-lookup"><span data-stu-id="ec449-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="ec449-132">Par exemple, les espaces de noms `.Design` sont principalement utilisés lors du développement d’outils de programmation.</span><span class="sxs-lookup"><span data-stu-id="ec449-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="ec449-133">Éviter les conflits avec les types de ces espaces de noms n’est pas critique.</span><span class="sxs-lookup"><span data-stu-id="ec449-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="ec449-134">**Espaces de noms principaux**</span><span class="sxs-lookup"><span data-stu-id="ec449-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="ec449-135">Les espaces de noms principaux incluent tous les espaces de noms `System`, à l’exclusion des espaces de noms des modèles d’application et des espaces de noms d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="ec449-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="ec449-136">Les espaces de noms principaux incluent, entre autres, les `System`, les `System.IO`, les `System.Xml`et les `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="ec449-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="ec449-137">**X DO NOT** permettent de types de noms qui sont en conflit avec un type dans les espaces de noms de base.</span><span class="sxs-lookup"><span data-stu-id="ec449-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="ec449-138">Par exemple, n’utilisez jamais `Stream` comme nom de type.</span><span class="sxs-lookup"><span data-stu-id="ec449-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="ec449-139">Il serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, un type très couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="ec449-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="ec449-140">**Groupes d’espaces de noms technologiques**</span><span class="sxs-lookup"><span data-stu-id="ec449-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="ec449-141">Cette catégorie comprend tous les espaces de noms ayant les mêmes deux premiers nœuds d’espace de noms `(<Company>.<Technology>*`), tels que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="ec449-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="ec449-142">Il est important que les types appartenant à une même technologie n’entrent pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="ec449-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="ec449-143">**X DO NOT** affecter des noms de type qui sont en conflit avec d’autres types au sein d’une seule technologie.</span><span class="sxs-lookup"><span data-stu-id="ec449-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="ec449-144">**X DO NOT** présentent des conflits de nom de type entre les types dans les espaces de noms de technologie et un espace de noms de modèle d’application (à moins que la technologie n’est pas destinée à être utilisée avec le modèle d’application).</span><span class="sxs-lookup"><span data-stu-id="ec449-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="ec449-145">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="ec449-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ec449-146">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ec449-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec449-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec449-147">See also</span></span>

- [<span data-ttu-id="ec449-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec449-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ec449-149">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="ec449-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
