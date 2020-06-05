---
title: -Nullable (options du compilateur C#)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449812"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="ccddf-102">-Nullable (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ccddf-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="ccddf-103">L’option **-Nullable** vous permet de spécifier le contexte Nullable souhaité.</span><span class="sxs-lookup"><span data-stu-id="ccddf-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="ccddf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccddf-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="ccddf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ccddf-105">Arguments</span></span>

<span data-ttu-id="ccddf-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ccddf-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="ccddf-107">Si `+` vous spécifiez, ou uniquement **null**,, le compilateur active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="ccddf-108">`-`Si vous spécifiez, qui est en vigueur si vous ne spécifiez pas **-Nullable**, désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="ccddf-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="ccddf-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="ccddf-110">Spécifie l’option de contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-110">Specifies the nullable context option.</span></span> <span data-ttu-id="ccddf-111">Semblable à `+` ou `-` , pour activer et désactiver, mais permet une plus grande granularité de la spécificité du contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="ccddf-112">L' `enable` argument, qui est en effet le même que si vous spécifiez **-Nullable**, active le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="ccddf-113">La spécification de `disable` désactive le contexte Nullable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="ccddf-114">Lorsque vous fournissez l' `warnings` argument, **-Nullable : Warnings**, le contexte d’avertissement Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="ccddf-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="ccddf-115">Lors de la spécification de l' `annotations` argument, **-Nullable : annotations**, le contexte d’annotation Nullable est activé.</span><span class="sxs-lookup"><span data-stu-id="ccddf-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccddf-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="ccddf-116">Remarks</span></span>

<span data-ttu-id="ccddf-117">L’analyse de Flow permet de déduire la possibilité de valeur null des variables au sein du code exécutable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="ccddf-118">La possibilité de valeur null déduite d’une variable est indépendante de la possibilité de valeur null déclarée de la variable.</span><span class="sxs-lookup"><span data-stu-id="ccddf-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="ccddf-119">Les appels de méthode sont analysés même s’ils sont omis conditionnellement.</span><span class="sxs-lookup"><span data-stu-id="ccddf-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="ccddf-120">Par exemple, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en mode release.</span><span class="sxs-lookup"><span data-stu-id="ccddf-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="ccddf-121">L’appel de méthodes annotées avec les attributs suivants affecte également l’analyse du workflow :</span><span class="sxs-lookup"><span data-stu-id="ccddf-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="ccddf-122">Conditions préalables simples : <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> et<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ccddf-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="ccddf-123">Conditions postérieures simples : <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> et<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ccddf-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="ccddf-124">Conditions de publication conditionnelles : <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> et<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="ccddf-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="ccddf-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(par exemple, `DoesNotReturnIf(false)` pour <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) et<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="ccddf-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (e.g. `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="ccddf-126">Conditions de publication des membres : <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> et<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="ccddf-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="ccddf-127">Pour définir cette option du compilateur dans un projet</span><span class="sxs-lookup"><span data-stu-id="ccddf-127">To set this compiler option in a project</span></span>

<span data-ttu-id="ccddf-128">Modifiez le *. csproj* pour ajouter la `<Nullable>` balise dans une `Project/PropertyGroup` hiérarchie :</span><span class="sxs-lookup"><span data-stu-id="ccddf-128">Edit the *.csproj* to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="ccddf-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccddf-129">See also</span></span>

- [<span data-ttu-id="ccddf-130">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="ccddf-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ccddf-131">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="ccddf-131">Nullable reference types</span></span>](../../nullable-references.md)
