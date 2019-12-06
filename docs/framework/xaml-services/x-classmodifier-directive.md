---
title: x:ClassModifier, directive
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837231"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="ce5ac-102">x:ClassModifier, directive</span><span class="sxs-lookup"><span data-stu-id="ce5ac-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="ce5ac-103">Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="ce5ac-104">Plus précisément, au lieu de créer une `class` partielle ayant un niveau d’accès `Public` (valeur par défaut), la `x:Class` fournie est créée avec un niveau d’accès `NotPublic`.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="ce5ac-105">Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="ce5ac-106">Utilisation des attributs XAML</span><span class="sxs-lookup"><span data-stu-id="ce5ac-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ce5ac-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="ce5ac-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce5ac-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="ce5ac-108">*NotPublic*</span></span>|<span data-ttu-id="ce5ac-109">La chaîne exacte à passer à spécifiez <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> contre <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="ce5ac-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="ce5ac-111">Dépendances</span><span class="sxs-lookup"><span data-stu-id="ce5ac-111">Dependencies</span></span>  
 <span data-ttu-id="ce5ac-112">[x :Class](x-class-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="ce5ac-113">Pour plus d’informations, consultez [\[MS-XAML\] section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ce5ac-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce5ac-114">Notes</span><span class="sxs-lookup"><span data-stu-id="ce5ac-114">Remarks</span></span>  
 <span data-ttu-id="ce5ac-115">La valeur de `x:ClassModifier` dans .NET Framework l’utilisation des services XAML varie en fonction du langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="ce5ac-116">La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et des convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="ce5ac-117">Pour C#, la chaîne à passer à la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> de désignation est `internal`.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="ce5ac-118">Pour Microsoft Visual Basic .NET, la chaîne à transmettre à la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Designate est `Friend`.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="ce5ac-119">Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML ; par conséquent, la valeur à passer n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="ce5ac-120">Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` dans C#, `Public` dans Visual Basic). Toutefois, la spécification de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement effectuée, car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="ce5ac-121">Les autres valeurs avec des restrictions de niveau d’accès de code utilisateur équivalentes C#, telles que `private` dans, ne sont pas pertinentes pour les `x:ClassModifier`, car les références de classe imbriquée ne sont pas prises en charge en XAML, et par conséquent, le modificateur <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> a le même effet.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="ce5ac-122">Remarques relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="ce5ac-122">Security Notes</span></span>  
 <span data-ttu-id="ce5ac-123">Le niveau d’accès tel qu’il est déclaré dans `x:ClassModifier` est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="ce5ac-124">WPF comprend des fonctionnalités permettant de charger et d’instancier des types où `x:ClassModifier` est `internal`, si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="ce5ac-125">À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, ne comptez pas exclusivement sur les `x:ClassModifier` pour bloquer toutes les tentatives d’instanciation possibles.</span><span class="sxs-lookup"><span data-stu-id="ce5ac-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5ac-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce5ac-126">See also</span></span>

- [<span data-ttu-id="ce5ac-127">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="ce5ac-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="ce5ac-128">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="ce5ac-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="ce5ac-129">x:FieldModifier, directive</span><span class="sxs-lookup"><span data-stu-id="ce5ac-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="ce5ac-130">Sécurité (WPF)</span><span class="sxs-lookup"><span data-stu-id="ce5ac-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="ce5ac-131">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="ce5ac-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
