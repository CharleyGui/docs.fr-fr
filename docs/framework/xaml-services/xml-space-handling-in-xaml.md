---
title: Gestion de xml:space en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458792"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="825fa-102">Gestion de xml:space en XAML</span><span class="sxs-lookup"><span data-stu-id="825fa-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="825fa-103">L’attribut `xml:space` est un attribut XML qui déclare le comportement significatif du traitement des espaces blancs dans un élément objet.</span><span class="sxs-lookup"><span data-stu-id="825fa-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="825fa-104">Ce comportement est pertinent pour tout le contenu (texte interne) contenu dans l’élément où `xml:space` est déclaré, ainsi que les étendues aux éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="825fa-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="825fa-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="825fa-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="825fa-106">\- ou -</span><span class="sxs-lookup"><span data-stu-id="825fa-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="825fa-107">Notes</span><span class="sxs-lookup"><span data-stu-id="825fa-107">Remarks</span></span>  
 <span data-ttu-id="825fa-108">La définition de l’attribut `xml:space` en XAML, y compris ses deux valeurs possibles, est dérivée de `xml:space` comme défini comme un « attribut spécial » par les spécifications W3C pour XML.</span><span class="sxs-lookup"><span data-stu-id="825fa-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="825fa-109">La valeur par défaut de l’attribut `xml:space` est la valeur littérale `"default"`.</span><span class="sxs-lookup"><span data-stu-id="825fa-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="825fa-110">Pour la valeur `"default"`, ou si `xml:space` n’est pas indiqué, le comportement de l’analyse de l’espace blanc significatif est le traitement par défaut, tel que défini dans la rubrique traitement des espaces [blancs en XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="825fa-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="825fa-111">Pour conserver les espaces blancs dans le contenu de l’élément objet, spécifiez `xml:space="preserve"` sur cet élément objet.</span><span class="sxs-lookup"><span data-stu-id="825fa-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="825fa-112">Dans la plupart des interprétations, les effets de l’attribut `xml:space` et la valeur de l’attribut sont limités aux éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="825fa-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="825fa-113">Pour une présentation complète du traitement des espaces blancs en XAML, consultez [traitement des espaces blancs en XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="825fa-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825fa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="825fa-114">See also</span></span>

- [<span data-ttu-id="825fa-115">Traitement des espaces blancs en XAML</span><span class="sxs-lookup"><span data-stu-id="825fa-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="825fa-116">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="825fa-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
