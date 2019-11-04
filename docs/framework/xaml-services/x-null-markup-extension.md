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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459945"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="8ad24-102">x:Null, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="8ad24-102">x:Null Markup Extension</span></span>
<span data-ttu-id="8ad24-103">Spécifie `null` en tant que valeur d’un membre XAML.</span><span class="sxs-lookup"><span data-stu-id="8ad24-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8ad24-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="8ad24-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="8ad24-105">Notes</span><span class="sxs-lookup"><span data-stu-id="8ad24-105">Remarks</span></span>  
 <span data-ttu-id="8ad24-106">Le mot clé pour une référence null C# dans C++ et est null.</span><span class="sxs-lookup"><span data-stu-id="8ad24-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="8ad24-107">Le mot clé Microsoft Visual Basic pour une référence null est `Nothing`, mais vous utilisez toujours `{x:Null}` comme utilisation XAML, quel que soit le langage code-behind que vous associez au XAML.</span><span class="sxs-lookup"><span data-stu-id="8ad24-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="8ad24-108">L’extension de balisage `x:Null` n’a pas de propriétés définissables.</span><span class="sxs-lookup"><span data-stu-id="8ad24-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="8ad24-109">Une utilisation null est souvent associée à l’exposition du membre XAML d’une valeur de <xref:System.Nullable%601> CLR.</span><span class="sxs-lookup"><span data-stu-id="8ad24-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="8ad24-110">L’extension de balisage `x:Null`, comme toutes les extensions de balisage XAML, utilise les accolades (`{,}`) pour placer dans une séquence d’échappement la gestion des valeurs d’attribut pour être autres que des littéraux ou des références de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="8ad24-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="8ad24-111">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="8ad24-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="8ad24-112">Une syntaxe d’élément objet `<x:Null />` est techniquement possible, mais est rarement utilisée, car l’extension de balisage `x:Null` n’a pas de paramètres positionnels ou d’arguments de construction.</span><span class="sxs-lookup"><span data-stu-id="8ad24-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="8ad24-113">Pour plus d’informations sur les extensions de balisage, consultez [extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="8ad24-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="8ad24-114">Dans .NET Framework services XAML, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.NullExtension>.</span><span class="sxs-lookup"><span data-stu-id="8ad24-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="8ad24-115">Remarques sur l’utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="8ad24-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="8ad24-116">Notez que `null` n’est pas nécessairement la valeur non définie initiale pour une propriété de dépendance de type référence.</span><span class="sxs-lookup"><span data-stu-id="8ad24-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="8ad24-117">La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8ad24-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="8ad24-118">De nombreuses propriétés de dépendance n’acceptent pas `null` comme valeur, par le biais du balisage ou du code en raison de leurs implémentations de rappel de validation.</span><span class="sxs-lookup"><span data-stu-id="8ad24-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="8ad24-119">Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ad24-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad24-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad24-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="8ad24-121">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ad24-121">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="8ad24-122">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="8ad24-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
