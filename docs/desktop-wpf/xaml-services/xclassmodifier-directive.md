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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072031"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="e5400-102">x:ClassModifier, directive</span><span class="sxs-lookup"><span data-stu-id="e5400-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="e5400-103">Modifie le comportement de `x:Class` compilation XAML lorsqu’il est également fourni.</span><span class="sxs-lookup"><span data-stu-id="e5400-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="e5400-104">Plus précisément, au `class` lieu de `Public` créer une partie qui `x:Class` a un `NotPublic` niveau d’accès (la valeur par défaut), le fourni est créé avec un niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="e5400-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="e5400-105">Ce comportement affecte le niveau d’accès pour la classe dans les assemblages générés.</span><span class="sxs-lookup"><span data-stu-id="e5400-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="e5400-106">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="e5400-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="e5400-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="e5400-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="e5400-108">*NonPublic*</span><span class="sxs-lookup"><span data-stu-id="e5400-108">*NotPublic*</span></span>|<span data-ttu-id="e5400-109">La chaîne exacte à <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passer <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> pour spécifier par rapport varie, selon le langage de programmation codé-derrière que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e5400-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="e5400-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="e5400-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="e5400-111">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="e5400-111">Dependencies</span></span>

<span data-ttu-id="e5400-112">[x : La classe](xclass-directive.md) doit également être fournie sur le même élément, et cet élément doit être l’élément racine d’une page.</span><span class="sxs-lookup"><span data-stu-id="e5400-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="e5400-113">Pour plus d’informations, voir [ \[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e5400-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="e5400-114">Notes</span><span class="sxs-lookup"><span data-stu-id="e5400-114">Remarks</span></span>

<span data-ttu-id="e5400-115">La valeur `x:ClassModifier` de l’utilisation de services .NET XAML varie selon le langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="e5400-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="e5400-116">La chaîne à utiliser dépend de <xref:System.CodeDom.Compiler.CodeDomProvider> la façon dont chaque langue implémente <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>son et le type de convertisseurs qu’elle retourne pour définir les significations et, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et si cette langue est sensible aux cas.</span><span class="sxs-lookup"><span data-stu-id="e5400-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="e5400-117">Pour C, la corde à <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> passer `internal`pour désigner est .</span><span class="sxs-lookup"><span data-stu-id="e5400-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="e5400-118">Pour Microsoft Visual Basic .NET, la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> chaîne `Friend`à passer pour désigner est .</span><span class="sxs-lookup"><span data-stu-id="e5400-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="e5400-119">Pour le CMD/CLI, il n’existe aucune cible qui appuie la compilation de XAML; par conséquent, la valeur de passage n’est pas précisée.</span><span class="sxs-lookup"><span data-stu-id="e5400-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="e5400-120">Vous pouvez <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> également`public` spécifier (en C, `Public` dans Visual Basic); cependant, la <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> spécifier est <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> rarement fait parce que c’est déjà le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="e5400-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="e5400-121">D’autres valeurs assorties de restrictions `private` équivalentes au niveau du `x:ClassModifier` code utilisateur, comme dans le C, ne <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> sont pas pertinentes parce que les références de classe imbriquées ne sont pas prises en charge dans XAML, et par conséquent, le modificateur a le même effet.</span><span class="sxs-lookup"><span data-stu-id="e5400-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="e5400-122">Remarques relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="e5400-122">Security Notes</span></span>

<span data-ttu-id="e5400-123">Le niveau d’accès tel qu’il est déclaré est `x:ClassModifier` toujours soumis à l’interprétation par des cadres particuliers et leurs capacités.</span><span class="sxs-lookup"><span data-stu-id="e5400-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="e5400-124">WPF inclut les capacités de chargement et d’instantanéis types où `x:ClassModifier` est, `internal`si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI pack.</span><span class="sxs-lookup"><span data-stu-id="e5400-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="e5400-125">En conséquence de cette affaire et potentiellement d’autres comme elle `x:ClassModifier` mise en œuvre par d’autres cadres, ne comptent pas exclusivement sur pour bloquer toutes les tentatives d’instantanéisation possibles.</span><span class="sxs-lookup"><span data-stu-id="e5400-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5400-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5400-126">See also</span></span>

- [<span data-ttu-id="e5400-127">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="e5400-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="e5400-128">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="e5400-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="e5400-129">x:FieldModifier, directive</span><span class="sxs-lookup"><span data-stu-id="e5400-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="e5400-130">Sécurité (WPF)</span><span class="sxs-lookup"><span data-stu-id="e5400-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="e5400-131">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="e5400-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
