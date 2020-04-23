---
title: x:Référence, extension de balisage
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071380"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="15bbb-102">x:Référence, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="15bbb-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="15bbb-103">Références d’un cas qui est déclaré ailleurs dans le balisage XAML.</span><span class="sxs-lookup"><span data-stu-id="15bbb-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="15bbb-104">La référence se réfère à `x:Name`un élément .</span><span class="sxs-lookup"><span data-stu-id="15bbb-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="15bbb-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="15bbb-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="15bbb-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="15bbb-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="15bbb-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="15bbb-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="15bbb-108">La `x:Name` valeur (ou <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>la valeur de la propriété identifiée) de l’instance référencée.</span><span class="sxs-lookup"><span data-stu-id="15bbb-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="15bbb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="15bbb-109">Remarks</span></span>

<span data-ttu-id="15bbb-110">`x:Reference`fournit un soutien au niveau de la langue XAML pour un concept de référence d’élément qui a été autrement mis en œuvre dans des cadres spécifiques tels que WPF.</span><span class="sxs-lookup"><span data-stu-id="15bbb-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="15bbb-111">x:Référence et WPF</span><span class="sxs-lookup"><span data-stu-id="15bbb-111">x:Reference and WPF</span></span>

<span data-ttu-id="15bbb-112">Dans WPF et XAML 2006, les références d’éléments sont abordées par la caractéristique de niveau-cadre de la <xref:System.Windows.Data.Binding.ElementName%2A> liaison.</span><span class="sxs-lookup"><span data-stu-id="15bbb-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="15bbb-113">Pour la plupart des applications <xref:System.Windows.Data.Binding.ElementName%2A> et scénarios WPF, la liaison doit encore être utilisée.</span><span class="sxs-lookup"><span data-stu-id="15bbb-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="15bbb-114">Les exceptions à ces directives générales peuvent inclure les cas où il y a un contexte de données ou d’autres considérations de portée qui rendent la compilation des données impraticable et où la compilation de balisage n’est pas impliquée.</span><span class="sxs-lookup"><span data-stu-id="15bbb-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="15bbb-115">`x:Reference`est une construction définie dans XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="15bbb-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="15bbb-116">Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage WPF.</span><span class="sxs-lookup"><span data-stu-id="15bbb-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="15bbb-117">Le code XAML compilé par balisage et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés de langage et fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="15bbb-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
