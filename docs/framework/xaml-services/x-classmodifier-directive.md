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
ms.openlocfilehash: c3c08f61b49a6367663cf02099dda86d1a692284
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484749"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="727f6-102">x:ClassModifier, directive</span><span class="sxs-lookup"><span data-stu-id="727f6-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="727f6-103">Modifie le comportement de compilation XAML `x:Class` lorsque est également fourni.</span><span class="sxs-lookup"><span data-stu-id="727f6-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="727f6-104">Plus précisément, au lieu de créer `class` un partiel ayant `Public` un niveau d’accès (valeur par défaut) `x:Class` , le fourni est `NotPublic` créé avec un niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="727f6-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="727f6-105">Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="727f6-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="727f6-106">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="727f6-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="727f6-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="727f6-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="727f6-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="727f6-108">*NotPublic*</span></span>|<span data-ttu-id="727f6-109">La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="727f6-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="727f6-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="727f6-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="727f6-111">Dépendances</span><span class="sxs-lookup"><span data-stu-id="727f6-111">Dependencies</span></span>  
 <span data-ttu-id="727f6-112">[x:Class](x-class-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page.</span><span class="sxs-lookup"><span data-stu-id="727f6-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="727f6-113">Pour plus d’informations, consultez [ \[la section\] MS-XAML 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="727f6-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="727f6-114">Notes</span><span class="sxs-lookup"><span data-stu-id="727f6-114">Remarks</span></span>  
 <span data-ttu-id="727f6-115">La valeur de `x:ClassModifier` dans .NET Framework l’utilisation des services XAML varie en fonction du langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="727f6-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="727f6-116">La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="727f6-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="727f6-117">Pour C#, la chaîne à passer à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal`.</span><span class="sxs-lookup"><span data-stu-id="727f6-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="727f6-118">Pour Microsoft Visual Basic .net, la chaîne à transmettre à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend`.</span><span class="sxs-lookup"><span data-stu-id="727f6-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="727f6-119">Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML; par conséquent, la valeur à passer n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="727f6-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="727f6-120">Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` dans C#, `Public` dans Visual Basic); Toutefois, la <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> spécification de est rarement effectuée <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , car est déjà le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="727f6-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="727f6-121">D’autres valeurs avec des restrictions de niveau d’accès du code utilisateur `private` équivalentes, comme dans C#, `x:ClassModifier` ne sont pas pertinentes pour, car les références de classe imbriquée ne sont <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> pas prises en charge en XAML, et par conséquent, le modificateur a le même effet .</span><span class="sxs-lookup"><span data-stu-id="727f6-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="727f6-122">Notes de sécurité</span><span class="sxs-lookup"><span data-stu-id="727f6-122">Security Notes</span></span>  
 <span data-ttu-id="727f6-123">Le niveau d’accès tel qu' `x:ClassModifier` il est déclaré dans est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="727f6-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="727f6-124">WPF offre des fonctionnalités permettant de charger et d' `x:ClassModifier` instancier des types où est `internal`, si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="727f6-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="727f6-125">À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, `x:ClassModifier` ne comptez pas exclusivement sur pour bloquer toutes les tentatives d’instanciation possibles.</span><span class="sxs-lookup"><span data-stu-id="727f6-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="727f6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="727f6-126">See also</span></span>

- [<span data-ttu-id="727f6-127">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="727f6-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="727f6-128">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="727f6-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="727f6-129">x:FieldModifier, directive</span><span class="sxs-lookup"><span data-stu-id="727f6-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="727f6-130">Sécurité (WPF)</span><span class="sxs-lookup"><span data-stu-id="727f6-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="727f6-131">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="727f6-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
