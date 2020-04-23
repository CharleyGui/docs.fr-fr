---
title: '{}Séquence d’évasion - Extension de Markup'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071744"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="98851-102">{}Séquence d’évasion / extension de balisage</span><span class="sxs-lookup"><span data-stu-id="98851-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="98851-103">Fournit la séquence d’évacuation XAML pour les valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="98851-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="98851-104">La séquence d’évacuation permet d’interpréter les valeurs ultérieures de l’attribut comme littérales.</span><span class="sxs-lookup"><span data-stu-id="98851-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="98851-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="98851-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="98851-106">Utilisation des éléments de propriété XAML</span><span class="sxs-lookup"><span data-stu-id="98851-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="98851-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="98851-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="98851-108">*littéralValue*</span><span class="sxs-lookup"><span data-stu-id="98851-108">*literalValue*</span></span>|<span data-ttu-id="98851-109">La chaîne littérale qui suit la séquence d’évasion.</span><span class="sxs-lookup"><span data-stu-id="98851-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="98851-110">Typiquement, cette chaîne contient une accolade ouverte ou proche (ou' ).</span><span class="sxs-lookup"><span data-stu-id="98851-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="98851-111">Notes</span><span class="sxs-lookup"><span data-stu-id="98851-111">Remarks</span></span>

<span data-ttu-id="98851-112">La séquence{}d’évacuation ( ) est utilisée de sorte qu’une accolade ouverte peut être utilisée comme personnage littéral dans XAML.</span><span class="sxs-lookup"><span data-stu-id="98851-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="98851-113">Les lecteurs de XAML utilisent généralement l’attelle ouverte pour désigner le point d’entrée d’une extension de balisage; cependant, ils vérifient d’abord le caractère suivant pour déterminer s’il s’agit d’une accolade de fermeture ( ).</span><span class="sxs-lookup"><span data-stu-id="98851-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="98851-114">Ce n’est que{}lorsque les deux accolades ( ) sont adjacentes, qu’elles sont considérées comme une séquence d’évacuation.</span><span class="sxs-lookup"><span data-stu-id="98851-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="98851-115">Si la séquence d’évacuation est rencontrée, le lecteur XAML doit traiter le reste de la chaîne comme une chaîne.</span><span class="sxs-lookup"><span data-stu-id="98851-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="98851-116">Toutefois, si la séquence d’échappement est appliquée à un membre qui a un convertisseur de type, la chaîne peut subir une conversion de type lorsqu’elle est interprétée par un auteur XAML.</span><span class="sxs-lookup"><span data-stu-id="98851-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="98851-117">La séquence d’évasion n’est pas une extension de balisage et n’est pas soutenue par une classe.</span><span class="sxs-lookup"><span data-stu-id="98851-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="98851-118">Cependant, il s’agit d’une convention que les lecteurs XAML (y compris les lecteurs personnalisés XAML) devraient respecter.</span><span class="sxs-lookup"><span data-stu-id="98851-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="98851-119">Une marque de citation (") ne peut pas être utilisée comme séquence d’évasion de cette manière.</span><span class="sxs-lookup"><span data-stu-id="98851-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="98851-120">Si vous avez besoin de définir une marque de de cotation comme valeur de propriété pour une propriété non contente, utilisez la syntaxe d’élément de propriété et placez la marque de citation comme chaîne à l’intérieur de l’élément de propriété, ou employez une entité de caractère XML.</span><span class="sxs-lookup"><span data-stu-id="98851-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="98851-121">Pour une propriété de contenu, la marque de citation peut être l’ensemble du contenu.</span><span class="sxs-lookup"><span data-stu-id="98851-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="98851-122">La séquence{}d’évasion ( ) est fréquemment nécessaire lors de la spécalisation d’un type XML qui doit inclure un qualificatif namespace dans un endroit où une extension de balisage XAML peut apparaître.</span><span class="sxs-lookup"><span data-stu-id="98851-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="98851-123">Cet emplacement comprend le début d’une valeur d’attribut XAML, et dans une extension de balisage immédiatement après un signe égal ( ).</span><span class="sxs-lookup"><span data-stu-id="98851-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="98851-124">L’exemple suivant montre des séquences d’évasion pour un espace de nom XML qui apparaît au début d’une valeur d’attribut XAML.</span><span class="sxs-lookup"><span data-stu-id="98851-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="98851-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98851-125">See also</span></span>

- [<span data-ttu-id="98851-126">Convertisseurs de types et extensions de balisage pour XAML</span><span class="sxs-lookup"><span data-stu-id="98851-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="98851-127">Entités de caractères XML et XAML</span><span class="sxs-lookup"><span data-stu-id="98851-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)
