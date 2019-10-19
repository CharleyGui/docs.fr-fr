---
title: ColorConvertedBitmap, extension de balisage
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582767"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap, extension de balisage
Fournit un moyen de spécifier une source bitmap qui n’a pas de profil incorporé. Les contextes de couleur/profils sont spécifiés par l’URI, comme l’URI de la source de l’image.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`imageSource`|URI de l’image bitmap qui n’est pas profilée.|  
|`sourceIIC`|URI de la configuration du profil source.|  
|`destinationIIC`|URI de la configuration du profil de destination|  
  
## <a name="remarks"></a>Notes  
 Cette extension de balisage est conçue pour remplir un ensemble connexe de valeurs de propriétés de source d’image, telles que <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. `ColorConvertedBitmap` (ou `ColorConvertedBitmapExtension`) ne peut pas être utilisé dans la syntaxe d’élément de propriété, car les valeurs peuvent uniquement être définies en tant que valeurs sur le constructeur initial, qui est la chaîne qui suit l’identificateur d’extension.  
  
 `ColorConvertedBitmap` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Vue d’ensemble de la création d’images](../graphics-multimedia/imaging-overview.md)
