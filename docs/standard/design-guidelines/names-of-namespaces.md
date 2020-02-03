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
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744139"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="aed93-102">Noms d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="aed93-102">Names of Namespaces</span></span>
<span data-ttu-id="aed93-103">Comme pour les autres instructions d’affectation de noms, l’objectif de l’attribution de noms aux espaces de noms est de créer suffisamment de clarté pour le programmeur qui utilise l’infrastructure pour savoir immédiatement ce que le contenu de l’espace de noms est susceptible d’être.</span><span class="sxs-lookup"><span data-stu-id="aed93-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="aed93-104">Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="aed93-104">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="aed93-105">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="aed93-105">The following are examples:</span></span>

 <span data-ttu-id="aed93-106">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="aed93-106">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="aed93-107">✔️ FAITES précéder les noms d’espaces de noms d’un nom de société pour empêcher les espaces de noms de sociétés différentes d’avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="aed93-107">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="aed93-108">✔️ Utilisez un nom de produit stable et indépendant de la version au deuxième niveau d’un nom d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="aed93-108">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="aed93-109">❌ n’utilisez pas de hiérarchies organisationnelles comme base pour les noms dans les hiérarchies d’espaces de noms, car les noms de groupe dans les sociétés ont tendance à être éphémères.</span><span class="sxs-lookup"><span data-stu-id="aed93-109">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="aed93-110">Organiser la hiérarchie des espaces de noms autour des groupes de technologies associées.</span><span class="sxs-lookup"><span data-stu-id="aed93-110">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="aed93-111">✔️ Utilisez PascalCasing et séparez les composants d’espace de noms par des points (par exemple, `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="aed93-111">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="aed93-112">Si votre personnalisation utilise une casse qui n’est pas traditionnelle, vous devez suivre la casse définie par votre personnalisation, même si elle diffère de la casse normale des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="aed93-112">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="aed93-113">✔️ envisagez d’utiliser des noms d’espaces de noms pluriels lorsque cela est approprié.</span><span class="sxs-lookup"><span data-stu-id="aed93-113">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="aed93-114">Par exemple, utilisez `System.Collections` au lieu de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="aed93-114">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="aed93-115">Toutefois, les noms et les acronymes sont des exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="aed93-115">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="aed93-116">Par exemple, utilisez `System.IO` au lieu de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="aed93-116">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="aed93-117">❌ n’utilisez pas le même nom pour un espace de noms et un type dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="aed93-117">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="aed93-118">Par exemple, n’utilisez pas `Debug` comme nom d’espace de noms, puis fournissez également une classe nommée `Debug` dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="aed93-118">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="aed93-119">Plusieurs compilateurs requièrent que ces types soient qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="aed93-119">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="aed93-120">Conflits d’espaces de noms et de noms de types</span><span class="sxs-lookup"><span data-stu-id="aed93-120">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="aed93-121">❌ n’introduisez pas de noms de types génériques tels que `Element`, `Node`, `Log`et `Message`.</span><span class="sxs-lookup"><span data-stu-id="aed93-121">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="aed93-122">Il y a une très grande probabilité que cela entraîne des conflits de noms de types dans les scénarios courants.</span><span class="sxs-lookup"><span data-stu-id="aed93-122">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="aed93-123">Vous devez qualifier les noms de types génériques (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="aed93-123">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="aed93-124">Il existe des instructions spécifiques pour éviter les conflits de noms de types pour différentes catégories d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="aed93-124">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="aed93-125">**Espaces de noms du modèle d’application**</span><span class="sxs-lookup"><span data-stu-id="aed93-125">**Application model namespaces**</span></span>

     <span data-ttu-id="aed93-126">Les espaces de noms appartenant à un modèle d’application unique sont souvent utilisés ensemble, mais ils ne sont jamais utilisés avec des espaces de noms d’autres modèles d’application.</span><span class="sxs-lookup"><span data-stu-id="aed93-126">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="aed93-127">Par exemple, l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> est très rarement utilisé avec l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aed93-127">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="aed93-128">Voici une liste de groupes d’espaces de noms de modèle d’application connus :</span><span class="sxs-lookup"><span data-stu-id="aed93-128">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="aed93-129">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="aed93-129">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="aed93-130">❌ n’attribuez pas le même nom aux types dans des espaces de noms dans un modèle d’application unique.</span><span class="sxs-lookup"><span data-stu-id="aed93-130">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="aed93-131">Par exemple, n’ajoutez pas de type nommé `Page` à l’espace de noms <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, car l’espace de noms <xref:System.Web.UI?displayProperty=nameWithType> contient déjà un type nommé `Page`.</span><span class="sxs-lookup"><span data-stu-id="aed93-131">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="aed93-132">**Espaces de noms d’infrastructure**</span><span class="sxs-lookup"><span data-stu-id="aed93-132">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="aed93-133">Ce groupe contient des espaces de noms rarement importés pendant le développement d’applications courantes.</span><span class="sxs-lookup"><span data-stu-id="aed93-133">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="aed93-134">Par exemple, les espaces de noms `.Design` sont principalement utilisés lors du développement d’outils de programmation.</span><span class="sxs-lookup"><span data-stu-id="aed93-134">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="aed93-135">Éviter les conflits avec les types de ces espaces de noms n’est pas critique.</span><span class="sxs-lookup"><span data-stu-id="aed93-135">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="aed93-136">**Espaces de noms principaux**</span><span class="sxs-lookup"><span data-stu-id="aed93-136">**Core namespaces**</span></span>

     <span data-ttu-id="aed93-137">Les espaces de noms principaux incluent tous les espaces de noms `System`, à l’exclusion des espaces de noms des modèles d’application et des espaces de noms d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="aed93-137">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="aed93-138">Les espaces de noms principaux incluent, entre autres, les `System`, les `System.IO`, les `System.Xml`et les `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="aed93-138">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="aed93-139">❌ n’attribuez pas de noms de types qui seraient en conflit avec n’importe quel type dans les espaces de noms de base.</span><span class="sxs-lookup"><span data-stu-id="aed93-139">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="aed93-140">Par exemple, n’utilisez jamais `Stream` comme nom de type.</span><span class="sxs-lookup"><span data-stu-id="aed93-140">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="aed93-141">Il serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, un type très couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="aed93-141">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="aed93-142">**Groupes d’espaces de noms technologiques**</span><span class="sxs-lookup"><span data-stu-id="aed93-142">**Technology namespace groups**</span></span>

     <span data-ttu-id="aed93-143">Cette catégorie comprend tous les espaces de noms ayant les mêmes deux premiers nœuds d’espace de noms `(<Company>.<Technology>*`), tels que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="aed93-143">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="aed93-144">Il est important que les types appartenant à une même technologie n’entrent pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="aed93-144">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="aed93-145">❌ n’attribuez pas de noms de types qui seraient en conflit avec d’autres types au sein d’une même technologie.</span><span class="sxs-lookup"><span data-stu-id="aed93-145">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="aed93-146">❌ n’introduisent pas de conflits de nom de type entre les types dans les espaces de noms technologiques et un espace de noms de modèle d’application (sauf si la technologie n’est pas destinée à être utilisée avec le modèle d’application).</span><span class="sxs-lookup"><span data-stu-id="aed93-146">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="aed93-147">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="aed93-147">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="aed93-148">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="aed93-148">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="aed93-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aed93-149">See also</span></span>

- [<span data-ttu-id="aed93-150">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aed93-150">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="aed93-151">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="aed93-151">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
