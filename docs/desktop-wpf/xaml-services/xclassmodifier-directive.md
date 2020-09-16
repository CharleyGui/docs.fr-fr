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
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544815"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="8c347-102">x:ClassModifier, directive</span><span class="sxs-lookup"><span data-stu-id="8c347-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="8c347-103">Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni.</span><span class="sxs-lookup"><span data-stu-id="8c347-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="8c347-104">Plus précisément, au lieu de créer un partiel `class` ayant un `Public` niveau d’accès (valeur par défaut), le fourni `x:Class` est créé avec un `NotPublic` niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="8c347-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="8c347-105">Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="8c347-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="8c347-106">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="8c347-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="8c347-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="8c347-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="8c347-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="8c347-108">*NotPublic*</span></span>|<span data-ttu-id="8c347-109">La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8c347-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="8c347-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="8c347-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="8c347-111">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="8c347-111">Dependencies</span></span>

<span data-ttu-id="8c347-112">[x :Class](xclass-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page.</span><span class="sxs-lookup"><span data-stu-id="8c347-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="8c347-113">Pour plus d’informations, consultez la [ \[ section MS-XAML \] 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8c347-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="8c347-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8c347-114">Remarks</span></span>

<span data-ttu-id="8c347-115">La valeur de `x:ClassModifier` dans l’utilisation des services XAML .net varie en fonction du langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="8c347-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="8c347-116">La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , et si cette langue respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c347-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="8c347-117">Pour C#, la chaîne à passer à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal` .</span><span class="sxs-lookup"><span data-stu-id="8c347-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="8c347-118">Pour Microsoft Visual Basic .NET, la chaîne à transmettre à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend` .</span><span class="sxs-lookup"><span data-stu-id="8c347-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="8c347-119">Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML ; par conséquent, la valeur à passer n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c347-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="8c347-120">Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` en C#, `Public` dans Visual Basic); Toutefois, la spécification de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement effectuée, car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="8c347-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="8c347-121">D’autres valeurs avec des restrictions de niveau d’accès de code utilisateur équivalentes, comme `private` en C#, ne sont pas pertinentes pour, `x:ClassModifier` car les références de classe imbriquée ne sont pas prises en charge en XAML, et par conséquent, le <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificateur a le même effet.</span><span class="sxs-lookup"><span data-stu-id="8c347-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="8c347-122">Remarques relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="8c347-122">Security Notes</span></span>

<span data-ttu-id="8c347-123">Le niveau d’accès tel qu’il est déclaré dans `x:ClassModifier` est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8c347-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="8c347-124">WPF offre des fonctionnalités permettant de charger et d’instancier des types où `x:ClassModifier` est `internal` , si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="8c347-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="8c347-125">À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, ne comptez pas exclusivement sur `x:ClassModifier` pour bloquer toutes les tentatives d’instanciation possibles.</span><span class="sxs-lookup"><span data-stu-id="8c347-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c347-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c347-126">See also</span></span>

- [<span data-ttu-id="8c347-127">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="8c347-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="8c347-128">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="8c347-128">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="8c347-129">x:FieldModifier, directive</span><span class="sxs-lookup"><span data-stu-id="8c347-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="8c347-130">Sécurité (WPF)</span><span class="sxs-lookup"><span data-stu-id="8c347-130">Security (WPF)</span></span>](/dotnet/desktop/wpf/security-wpf)
- [<span data-ttu-id="8c347-131">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="8c347-131">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
