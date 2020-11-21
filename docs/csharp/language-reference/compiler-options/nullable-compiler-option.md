---
description: -Nullable (options du compilateur C#)
title: -Nullable (options du compilateur C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099222"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="7680e-103">-Nullable (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="7680e-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="7680e-104">L’option **-Nullable** vous permet de spécifier le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-104">The **-nullable** option lets you specify the nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="7680e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7680e-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="7680e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7680e-106">Arguments</span></span>

<span data-ttu-id="7680e-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7680e-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="7680e-108">Si `+` vous spécifiez, ou **-Nullable**, le compilateur active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-108">Specifying `+`, or **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="7680e-109">`-`Si vous spécifiez, qui est en vigueur si vous ne spécifiez pas **-Nullable**, désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-109">Specifying `-`, which is in effect if you don't specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="7680e-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="7680e-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="7680e-111">Spécifie l’option de contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-111">Specifies the nullable context option.</span></span> <span data-ttu-id="7680e-112">Semblable à `+` ou `-` , pour activer et désactiver, mais permet une plus grande granularité de la spécificité du contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="7680e-113">L' `enable` argument, qui est en effet le même que si vous spécifiez **-Nullable**, active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="7680e-114">La spécification de `disable` désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="7680e-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="7680e-115">Lorsque vous fournissez l' `warnings` argument, **-Nullable : Warnings**, le contexte d’avertissement Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="7680e-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="7680e-116">Lors de la spécification de l' `annotations` argument, **-Nullable : annotations**, le contexte d’annotation Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="7680e-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="7680e-117">Notes</span><span class="sxs-lookup"><span data-stu-id="7680e-117">Remarks</span></span>

<span data-ttu-id="7680e-118">L’analyse de Flow permet de déduire la possibilité de valeur null des variables au sein du code exécutable.</span><span class="sxs-lookup"><span data-stu-id="7680e-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="7680e-119">La possibilité de valeur null déduite d’une variable est indépendante de la possibilité de valeur null déclarée de la variable.</span><span class="sxs-lookup"><span data-stu-id="7680e-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="7680e-120">Les appels de méthode sont analysés même lorsqu’ils sont omis de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="7680e-120">Method calls are analyzed even when they're conditionally omitted.</span></span> <span data-ttu-id="7680e-121">Par exemple, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en mode release.</span><span class="sxs-lookup"><span data-stu-id="7680e-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="7680e-122">L’appel de méthodes annotées avec les attributs suivants affecte également l’analyse du workflow :</span><span class="sxs-lookup"><span data-stu-id="7680e-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="7680e-123">Conditions préalables simples : <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="7680e-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="7680e-124">Conditions postérieures simples : <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="7680e-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="7680e-125">Conditions de publication conditionnelles : <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="7680e-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="7680e-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (par exemple, `DoesNotReturnIf(false)` pour <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) et <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="7680e-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="7680e-127">Conditions de publication des membres : <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> et <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="7680e-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

> [!IMPORTANT]
> <span data-ttu-id="7680e-128">Le contexte Nullable global ne s’applique pas aux fichiers de code générés.</span><span class="sxs-lookup"><span data-stu-id="7680e-128">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="7680e-129">Indépendamment de ce paramètre, le contexte Nullable est *désactivé* pour tout fichier source marqué comme généré.</span><span class="sxs-lookup"><span data-stu-id="7680e-129">Regardless of this setting, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="7680e-130">Un fichier est marqué comme généré de quatre façons :</span><span class="sxs-lookup"><span data-stu-id="7680e-130">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="7680e-131">Dans le fichier. editorconfig, spécifiez `generated_code = true` dans une section qui s’applique à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="7680e-131">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="7680e-132">Placez `<auto-generated>` ou `<auto-generated/>` dans un commentaire en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="7680e-132">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="7680e-133">Il peut se trouver sur n’importe quelle ligne de ce commentaire, mais le bloc de commentaires doit être le premier élément du fichier.</span><span class="sxs-lookup"><span data-stu-id="7680e-133">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="7680e-134">Démarrer le nom de fichier avec *TemporaryGeneratedFile_*</span><span class="sxs-lookup"><span data-stu-id="7680e-134">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="7680e-135">Terminez le nom de fichier avec *. Designer.cs*, *. generated.cs*, *. g.cs* ou *. g.i.cs*.</span><span class="sxs-lookup"><span data-stu-id="7680e-135">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="7680e-136">Les générateurs peuvent s’abonner à l’aide de la [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="7680e-136">Generators can opt-in using the [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="7680e-137">Pour définir cette option du compilateur dans un projet</span><span class="sxs-lookup"><span data-stu-id="7680e-137">To set this compiler option in a project</span></span>

<span data-ttu-id="7680e-138">Modifiez le fichier *. csproj* pour ajouter la `<Nullable>` balise dans une `Project/PropertyGroup` hiérarchie :</span><span class="sxs-lookup"><span data-stu-id="7680e-138">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="7680e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7680e-139">See also</span></span>

- [<span data-ttu-id="7680e-140">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="7680e-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7680e-141">`#nullable` directive de préprocesseur</span><span class="sxs-lookup"><span data-stu-id="7680e-141">`#nullable` preprocessor directive</span></span>](../preprocessor-directives/preprocessor-nullable.md)
- [<span data-ttu-id="7680e-142">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="7680e-142">Nullable reference types</span></span>](../../nullable-references.md)
