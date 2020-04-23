---
title: x:Null, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071429"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="261d8-102">x:Null, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="261d8-102">x:Null Markup Extension</span></span>

<span data-ttu-id="261d8-103">Spécifie `null` comme valeur pour un membre XAML.</span><span class="sxs-lookup"><span data-stu-id="261d8-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="261d8-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="261d8-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="261d8-105">Notes</span><span class="sxs-lookup"><span data-stu-id="261d8-105">Remarks</span></span>

<span data-ttu-id="261d8-106">Le mot clé pour une référence nulle dans C et CM est nul.</span><span class="sxs-lookup"><span data-stu-id="261d8-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="261d8-107">Le mot clé Microsoft Visual `Nothing`Basic pour une `{x:Null}` référence nulle est, mais vous utilisez toujours comme l’utilisation XAML indépendamment de la langue codé-derrière vous associer avec le XAML.</span><span class="sxs-lookup"><span data-stu-id="261d8-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="261d8-108">L’extension `x:Null` de balisage n’a pas de propriétés fixes.</span><span class="sxs-lookup"><span data-stu-id="261d8-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="261d8-109">Une utilisation nulle est souvent associée à l’exposition <xref:System.Nullable%601> des membres XAML d’une valeur CLR.</span><span class="sxs-lookup"><span data-stu-id="261d8-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="261d8-110">L’extension `x:Null` de balisage, comme toutes les extensions`{,}`de balisage XAML, utilise les accolades ( ) pour échapper à la manipulation des valeurs d’attribut pour être autre que les littérals ou les références event-handler.</span><span class="sxs-lookup"><span data-stu-id="261d8-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="261d8-111">La syntaxe d’attribut est la syntaxe la plus fréquemment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="261d8-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="261d8-112">Une syntaxe `<x:Null />` d’élément objet est techniquement `x:Null` possible, mais est rarement utilisée parce que l’extension de balisage n’a pas de paramètres de position ou d’arguments de construction.</span><span class="sxs-lookup"><span data-stu-id="261d8-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="261d8-113">Pour plus d’informations sur les extensions de balisage, voir [Extensions Markup et WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="261d8-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="261d8-114">Dans .NET XAML Services, la manipulation de cette <xref:System.Windows.Markup.NullExtension> extension de balisage est définie par la classe.</span><span class="sxs-lookup"><span data-stu-id="261d8-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="261d8-115">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="261d8-115">WPF Usage Notes</span></span>

<span data-ttu-id="261d8-116">Notez `null` que ce n’est pas nécessairement la valeur initiale non assaillie d’une propriété de dépendance de type de référence.</span><span class="sxs-lookup"><span data-stu-id="261d8-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="261d8-117">La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété.</span><span class="sxs-lookup"><span data-stu-id="261d8-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="261d8-118">De nombreuses propriétés `null` de dépendance n’acceptent pas comme valeur, que ce soit par balisage ou par code en raison de leurs implémentations de rappel de validation.</span><span class="sxs-lookup"><span data-stu-id="261d8-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="261d8-119">Pour plus d’informations sur les propriétés de dépendance, voir [Dependency Properties Aperçu](../../framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="261d8-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="261d8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="261d8-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="261d8-121">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="261d8-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="261d8-122">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="261d8-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
