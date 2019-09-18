---
title: '{}Séquence d’échappement-extension de balisage'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053876"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="85c9f-102">{} Séquence d’échappement/Extension de balisage</span><span class="sxs-lookup"><span data-stu-id="85c9f-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="85c9f-103">Fournit la séquence d’échappement XAML pour les valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="85c9f-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="85c9f-104">La séquence d’échappement permet d’interpréter les valeurs suivantes dans l’attribut comme un littéral.</span><span class="sxs-lookup"><span data-stu-id="85c9f-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="85c9f-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="85c9f-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="85c9f-106">Utilisation des éléments de propriété XAML</span><span class="sxs-lookup"><span data-stu-id="85c9f-106">XAML Property Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="85c9f-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="85c9f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85c9f-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="85c9f-108">*literalValue*</span></span>|<span data-ttu-id="85c9f-109">Chaîne littérale qui suit la séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="85c9f-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="85c9f-110">En général, cette chaîne contient une accolade ouvrante ou fermante ({ou}).</span><span class="sxs-lookup"><span data-stu-id="85c9f-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c9f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="85c9f-111">Remarks</span></span>  
 <span data-ttu-id="85c9f-112">La séquence d’échappement{}() est utilisée pour qu’une accolade ouvrante ({) puisse être utilisée comme caractère littéral en XAML.</span><span class="sxs-lookup"><span data-stu-id="85c9f-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="85c9f-113">Les lecteurs XAML utilisent généralement l’accolade ouvrante ({) pour désigner le point d’entrée d’une extension de balisage ; Toutefois, ils vérifient d’abord le caractère suivant pour déterminer s’il s’agit d’une accolade fermante (}).</span><span class="sxs-lookup"><span data-stu-id="85c9f-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="85c9f-114">La seule fois lorsque les deux accolades ({}) sont adjacentes, elles sont considérées comme une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="85c9f-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="85c9f-115">Si la séquence d’échappement est rencontrée, le lecteur XAML doit traiter le reste de la chaîne comme une chaîne.</span><span class="sxs-lookup"><span data-stu-id="85c9f-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="85c9f-116">Toutefois, si la séquence d’échappement est appliquée à un membre qui possède un convertisseur de type, la chaîne peut subir une conversion de type lorsqu’elle est interprétée par un writer XAML.</span><span class="sxs-lookup"><span data-stu-id="85c9f-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="85c9f-117">La séquence d’échappement n’est pas une extension de balisage et n’est pas sauvegardée par une classe.</span><span class="sxs-lookup"><span data-stu-id="85c9f-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="85c9f-118">Toutefois, il est recommandé de respecter les lecteurs XAML (y compris les lecteurs XAML personnalisés).</span><span class="sxs-lookup"><span data-stu-id="85c9f-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="85c9f-119">Un guillemet (") ne peut pas être utilisé comme une séquence d’échappement de cette manière.</span><span class="sxs-lookup"><span data-stu-id="85c9f-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="85c9f-120">Si vous devez définir un guillemet comme valeur de propriété pour une propriété qui n’est pas de contenu, utilisez la syntaxe d’élément de propriété et placez le guillemet en tant que chaîne à l’intérieur de l’élément de propriété, ou utilisez une entité de caractère XML.</span><span class="sxs-lookup"><span data-stu-id="85c9f-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="85c9f-121">Pour une propriété de contenu, le guillemet peut correspondre à tout le contenu.</span><span class="sxs-lookup"><span data-stu-id="85c9f-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="85c9f-122">La séquence d’échappement{}() est souvent requise lors de la spécification d’un type XML qui doit inclure un qualificateur d’espace de noms dans un emplacement où une extension de balisage XAML peut apparaître.</span><span class="sxs-lookup"><span data-stu-id="85c9f-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="85c9f-123">Cela comprend le début d’une valeur d’attribut XAML, et dans une extension de balisage, immédiatement après un signe égal (=).</span><span class="sxs-lookup"><span data-stu-id="85c9f-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="85c9f-124">L’exemple suivant montre des séquences d’échappement pour un espace de noms XML qui apparaît au début d’une valeur d’attribut XAML.</span><span class="sxs-lookup"><span data-stu-id="85c9f-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="85c9f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c9f-125">See also</span></span>

- [<span data-ttu-id="85c9f-126">Convertisseurs de types et extensions de balisage pour XAML</span><span class="sxs-lookup"><span data-stu-id="85c9f-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="85c9f-127">Entités de caractères XML et XAML</span><span class="sxs-lookup"><span data-stu-id="85c9f-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
