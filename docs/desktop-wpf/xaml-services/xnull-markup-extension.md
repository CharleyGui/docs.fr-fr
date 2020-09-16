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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549442"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="9da0c-102">x:Null, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="9da0c-102">x:Null Markup Extension</span></span>

<span data-ttu-id="9da0c-103">Spécifie `null` comme valeur pour un membre XAML.</span><span class="sxs-lookup"><span data-stu-id="9da0c-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="9da0c-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="9da0c-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="9da0c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="9da0c-105">Remarks</span></span>

<span data-ttu-id="9da0c-106">Le mot clé pour une référence null en C# et C++ a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="9da0c-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="9da0c-107">Le mot clé Microsoft Visual Basic pour une référence null est `Nothing` , mais vous utilisez toujours `{x:Null}` comme utilisation XAML quel que soit le langage code-behind que vous associez au XAML.</span><span class="sxs-lookup"><span data-stu-id="9da0c-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="9da0c-108">L' `x:Null` extension de balisage n’a pas de propriétés définissables.</span><span class="sxs-lookup"><span data-stu-id="9da0c-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="9da0c-109">Une utilisation null est souvent associée à l’exposition du membre XAML d’une <xref:System.Nullable%601> valeur CLR.</span><span class="sxs-lookup"><span data-stu-id="9da0c-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="9da0c-110">L' `x:Null` extension de balisage, comme toutes les extensions de balisage XAML, utilise les accolades ( `{,}` ) pour échapper la gestion des valeurs d’attribut à d’autres littéraux ou références de gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="9da0c-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="9da0c-111">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="9da0c-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="9da0c-112">Une syntaxe d’élément objet `<x:Null />` est techniquement possible, mais est rarement utilisée, car l' `x:Null` extension de balisage n’a pas de paramètres positionnels ou d’arguments de construction.</span><span class="sxs-lookup"><span data-stu-id="9da0c-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="9da0c-113">Pour plus d’informations sur les extensions de balisage, consultez [extensions de balisage et XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="9da0c-113">For information about markup extensions, see [Markup Extensions and WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span></span>

<span data-ttu-id="9da0c-114">Dans les services XAML .NET, la gestion de cette extension de balisage est définie par la <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="9da0c-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="9da0c-115">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="9da0c-115">WPF Usage Notes</span></span>

<span data-ttu-id="9da0c-116">Notez qu' `null` il ne s’agit pas nécessairement de la valeur initiale non définie pour une propriété de dépendance de type référence.</span><span class="sxs-lookup"><span data-stu-id="9da0c-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="9da0c-117">La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9da0c-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="9da0c-118">De nombreuses propriétés de dépendance n’acceptent pas `null` comme valeur, par le biais du balisage ou du code en raison de leurs implémentations de rappel de validation.</span><span class="sxs-lookup"><span data-stu-id="9da0c-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="9da0c-119">Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span><span class="sxs-lookup"><span data-stu-id="9da0c-119">For more information about dependency properties, see [Dependency Properties Overview](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span></span>

## <a name="see-also"></a><span data-ttu-id="9da0c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9da0c-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="9da0c-121">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9da0c-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="9da0c-122">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="9da0c-122">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
