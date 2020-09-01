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
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125044"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="4349b-103">-Nullable (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="4349b-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="4349b-104">L’option **-Nullable** vous permet de spécifier le contexte Nullable souhaité.</span><span class="sxs-lookup"><span data-stu-id="4349b-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="4349b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4349b-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="4349b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4349b-106">Arguments</span></span>

<span data-ttu-id="4349b-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4349b-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="4349b-108">Si `+` vous spécifiez, ou uniquement **null**,, le compilateur active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="4349b-109">`-`Si vous spécifiez, qui est en vigueur si vous ne spécifiez pas **-Nullable**, désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="4349b-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="4349b-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="4349b-111">Spécifie l’option de contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-111">Specifies the nullable context option.</span></span> <span data-ttu-id="4349b-112">Semblable à `+` ou `-` , pour activer et désactiver, mais permet une plus grande granularité de la spécificité du contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="4349b-113">L' `enable` argument, qui est en effet le même que si vous spécifiez **-Nullable**, active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="4349b-114">La spécification de `disable` désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="4349b-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="4349b-115">Lorsque vous fournissez l' `warnings` argument, **-Nullable : Warnings**, le contexte d’avertissement Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="4349b-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="4349b-116">Lors de la spécification de l' `annotations` argument, **-Nullable : annotations**, le contexte d’annotation Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="4349b-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="4349b-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="4349b-117">Remarks</span></span>

<span data-ttu-id="4349b-118">L’analyse de Flow permet de déduire la possibilité de valeur null des variables au sein du code exécutable.</span><span class="sxs-lookup"><span data-stu-id="4349b-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="4349b-119">La possibilité de valeur null déduite d’une variable est indépendante de la possibilité de valeur null déclarée de la variable.</span><span class="sxs-lookup"><span data-stu-id="4349b-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="4349b-120">Les appels de méthode sont analysés même s’ils sont omis conditionnellement.</span><span class="sxs-lookup"><span data-stu-id="4349b-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="4349b-121">Par exemple, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en mode release.</span><span class="sxs-lookup"><span data-stu-id="4349b-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="4349b-122">L’appel de méthodes annotées avec les attributs suivants affecte également l’analyse du workflow :</span><span class="sxs-lookup"><span data-stu-id="4349b-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="4349b-123">Conditions préalables simples : <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="4349b-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="4349b-124">Conditions postérieures simples : <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="4349b-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="4349b-125">Conditions de publication conditionnelles : <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="4349b-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="4349b-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (par exemple, `DoesNotReturnIf(false)` pour <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) et <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="4349b-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="4349b-127">Conditions de publication des membres : <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> et <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="4349b-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="4349b-128">Pour définir cette option du compilateur dans un projet</span><span class="sxs-lookup"><span data-stu-id="4349b-128">To set this compiler option in a project</span></span>

<span data-ttu-id="4349b-129">Modifiez le fichier *. csproj* pour ajouter la `<Nullable>` balise dans une `Project/PropertyGroup` hiérarchie :</span><span class="sxs-lookup"><span data-stu-id="4349b-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="4349b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4349b-130">See also</span></span>

- [<span data-ttu-id="4349b-131">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="4349b-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4349b-132">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="4349b-132">Nullable reference types</span></span>](../../nullable-references.md)
