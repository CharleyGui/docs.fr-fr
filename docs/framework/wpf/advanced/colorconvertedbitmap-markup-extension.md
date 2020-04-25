---
title: ColorConvertedBitmap, extension de balisage
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141224"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="fd08a-102">ColorConvertedBitmap, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="fd08a-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="fd08a-103">Fournit un moyen de spécifier une source bitmap qui n’a pas de profil incorporé.</span><span class="sxs-lookup"><span data-stu-id="fd08a-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="fd08a-104">Les contextes de couleur/profils sont spécifiés par l’URI, comme l’URI de la source de l’image.</span><span class="sxs-lookup"><span data-stu-id="fd08a-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="fd08a-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="fd08a-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="fd08a-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="fd08a-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="fd08a-107">URI de l’image bitmap qui n’est pas profilée.</span><span class="sxs-lookup"><span data-stu-id="fd08a-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="fd08a-108">URI de la configuration du profil source.</span><span class="sxs-lookup"><span data-stu-id="fd08a-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="fd08a-109">URI de la configuration du profil de destination</span><span class="sxs-lookup"><span data-stu-id="fd08a-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd08a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="fd08a-110">Remarks</span></span>  
 <span data-ttu-id="fd08a-111">Cette extension de balisage est conçue pour remplir un ensemble connexe de valeurs de propriété de <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>source d’image, telles que.</span><span class="sxs-lookup"><span data-stu-id="fd08a-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="fd08a-112">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="fd08a-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="fd08a-113">`ColorConvertedBitmap`(ou `ColorConvertedBitmapExtension`) ne peut pas être utilisé dans la syntaxe d’élément de propriété, car les valeurs peuvent uniquement être définies en tant que valeurs sur le constructeur initial, qui est la chaîne qui suit l’identificateur d’extension.</span><span class="sxs-lookup"><span data-stu-id="fd08a-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="fd08a-114">`ColorConvertedBitmap` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="fd08a-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="fd08a-115">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="fd08a-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="fd08a-116">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="fd08a-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="fd08a-117">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fd08a-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd08a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd08a-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="fd08a-119">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="fd08a-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="fd08a-120">Vue d'ensemble de la création d'images</span><span class="sxs-lookup"><span data-stu-id="fd08a-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
