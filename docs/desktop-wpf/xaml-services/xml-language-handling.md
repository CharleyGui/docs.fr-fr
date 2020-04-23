---
title: Gestion de xml:lang en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071443"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="0ef4c-102">Gestion de xml:lang en XAML</span><span class="sxs-lookup"><span data-stu-id="0ef4c-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="0ef4c-103">L’attribut `xml:lang` est un attribut défini par XML qui déclare l’information linguistique et culturelle pour un élément dans XML.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="0ef4c-104">Cette même signification de l’attribut persiste en XAML. Toutefois, certaines considérations supplémentaires s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="0ef4c-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="0ef4c-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="0ef4c-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="0ef4c-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="0ef4c-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="0ef4c-107">*rfc3066lang*</span></span>|<span data-ttu-id="0ef4c-108">Chaîne dérivée de la norme [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) qui identifie une langue ou une langue-région.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="0ef4c-109">Dans le dernier cas, la langue et la région sont séparées par un tiret.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="0ef4c-110">Pour plus d’informations sur les valeurs et le format, consultez <xref:System.Windows.Markup.XmlLanguage> .</span><span class="sxs-lookup"><span data-stu-id="0ef4c-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ef4c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="0ef4c-111">Remarks</span></span>

<span data-ttu-id="0ef4c-112">La définition `xml:lang` de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] l’attribut `xml:lang` est dérivée d’un « attribut spécial » par le World Wide Web Consortium (W3C) pour XML.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="0ef4c-113">Les informations de langue et de culture peuvent être traitées de différentes façons par les éléments, selon leurs implémentations. Toutefois, il n’existe aucun traitement [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] par défaut de l’attribut `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="0ef4c-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="0ef4c-114">La valeur par défaut de l’attribut `xml:lang` est une chaîne vide au niveau de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="0ef4c-115">Les effets et la valeur de l’attribut `xml:lang` sont généralement transmis aux éléments enfants, quand ils sont interprétés par des systèmes qui agissent sur les valeurs `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="0ef4c-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="0ef4c-116">Lorsqu’il est interprété par les auteurs XAML de .NET XAML Services, une `xml:lang` valeur peut créer <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> des objets dans la représentation de l’objet sous-jacent; cependant, ce comportement dépend de `xml:lang` si la valeur spécifiée pour est une construction valide pour ces classes.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="0ef4c-117">Les infrastructures peuvent créer des associations entre les propriétés définies par l’infrastructure et la signification de `xml:lang` dans XML en appliquant <xref:System.Windows.Markup.XmlLangPropertyAttribute> à la propriété.</span><span class="sxs-lookup"><span data-stu-id="0ef4c-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="0ef4c-118">Nœuds d’utilisation WPF</span><span class="sxs-lookup"><span data-stu-id="0ef4c-118">WPF Usage Nodes</span></span>

<span data-ttu-id="0ef4c-119">Pour les éléments qui sont des classes dérivées de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, vous pouvez utiliser la propriété de dépendance <xref:System.Windows.FrameworkElement.Language%2A> équivalente à la place de l’attribut `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="0ef4c-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="0ef4c-120">Par défaut, la propriété <xref:System.Windows.FrameworkElement.Language%2A> utilise « en-US » si elle n’est pas définie autrement via la propriété ou via le traitement de l’attribut `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="0ef4c-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ef4c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ef4c-121">See also</span></span>

- [<span data-ttu-id="0ef4c-122">Globalisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="0ef4c-122">Globalization for WPF</span></span>](../../framework/wpf/advanced/globalization-for-wpf.md)
