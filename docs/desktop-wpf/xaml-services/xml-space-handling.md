---
title: Gestion de xml:space en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071436"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="84e09-102">Gestion de xml:space en XAML</span><span class="sxs-lookup"><span data-stu-id="84e09-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="84e09-103">L’attribut `xml:space` est un attribut XML défini qui déclare le comportement significatif de traitement de l’espace blanc dans un élément d’objet.</span><span class="sxs-lookup"><span data-stu-id="84e09-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="84e09-104">Ce comportement est pertinent pour tout contenu (texte `xml:space` interne) contenu dans l’élément où est déclaré, et aussi les étendues aux éléments de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="84e09-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="84e09-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="84e09-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="84e09-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="84e09-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="84e09-107">Notes</span><span class="sxs-lookup"><span data-stu-id="84e09-107">Remarks</span></span>

<span data-ttu-id="84e09-108">La définition `xml:space` de l’attribut dans XAML, `xml:space` y compris ses deux valeurs possibles, est dérivée d’un « attribut spécial » par les spécifications W3C pour XML.</span><span class="sxs-lookup"><span data-stu-id="84e09-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="84e09-109">La valeur par `xml:space` défaut de l’attribut est la valeur `"default"`littérale .</span><span class="sxs-lookup"><span data-stu-id="84e09-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="84e09-110">Pour la `"default"`valeur `xml:space` , ou si n’est pas indiqué du tout, le comportement de l’analyse importante de l’espace blanc est la manipulation par défaut, tel que défini dans le sujet [de traitement de l’espace blanc dans XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="84e09-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="84e09-111">Pour préserver l’espace blanc `xml:space="preserve"` dans le contenu de l’élément objet, spécifiez sur cet élément d’objet.</span><span class="sxs-lookup"><span data-stu-id="84e09-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="84e09-112">Selon la plupart `xml:space` des interprétations, les effets d’attribut et la valeur de l’attribut sont étendues aux éléments de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="84e09-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="84e09-113">Pour une discussion complète du traitement de l’espace blanc dans XAML, voir [le traitement de l’espace blanc dans XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="84e09-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84e09-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84e09-114">See also</span></span>

- [<span data-ttu-id="84e09-115">Traitement des espaces blancs en XAML</span><span class="sxs-lookup"><span data-stu-id="84e09-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="84e09-116">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="84e09-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
