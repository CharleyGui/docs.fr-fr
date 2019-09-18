---
title: x:XData, type XAML intrinsèque
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053695"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData, type XAML intrinsèque
Active le placement des îlots de données XML dans une production XAML. Les éléments XML `x:XData` dans ne doivent pas être traités par les processeurs XAML comme s’ils font partie de l’espace de noms XAML par défaut en cours d’action ou de tout autre espace de noms XAML. `x:XData`peut contenir du code XML bien formé arbitrairement.  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Élément racine unique de l’îlot de données délimité. Pour la plupart des consommateurs éventuels, le XML qui n’a pas de racine unique est considéré comme non valide. En particulier, une racine unique est requise si le `x:XData` est destiné à être une source de données XML pour WPF ou de nombreuses autres technologies qui utilisent des sources XML pour la liaison de données.|  
|`[elementData]`|facultatif. XML qui représente les données XML. Vous pouvez faire figurer un nombre quelconque d’éléments en tant que données d’élément et les éléments imbriqués peuvent être contenus dans d’autres éléments ; Toutefois, les règles générales de XML s’appliquent.|  
  
## <a name="remarks"></a>Notes  
 Les éléments XML dans un `x:XData` objet peuvent redéclarer tous les espaces de noms et préfixes possibles de l’objet XMLDOM contenant les données.  
  
 L’accès par programme aux données XML `x:XData` et au type XAML intrinsèque est possible dans .NET Framework les services <xref:System.Windows.Markup.XData> XAML par le biais de la classe.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 L' `x:XData` objet est principalement utilisé comme un objet enfant d’un <xref:System.Windows.Data.XmlDataProvider>objet, ou, en tant qu’objet enfant de la <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriété (en XAML, il est généralement exprimé dans la syntaxe d’élément de propriété).  
  
 Les données doivent généralement redéfinir l’espace de noms XML de base dans l’îlot de données pour qu’il s’agit d’un nouvel espace de noms XML par défaut (défini sur une chaîne vide). Cela est plus facile pour les îlots de <xref:System.Windows.Data.Binding.XPath%2A> données simples, car les expressions utilisées pour référencer les données et les lier aux données peuvent éviter l’inclusion de préfixes. Des îlots de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de noms XML à la racine. Dans ce cas, toutes <xref:System.Windows.Data.Binding.XPath%2A> les références d’expression doivent inclure le préfixe mappé à l’espace de noms approprié. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../wpf/data/data-binding-overview.md).  
  
 Techniquement, `x:XData` peut être utilisé comme contenu de n’importe quelle propriété de <xref:System.Xml.Serialization.IXmlSerializable>type. Toutefois, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule implémentation évidente.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.XmlDataProvider>
- [Vue d’ensemble de la liaison de données](../wpf/data/data-binding-overview.md)
- [Binding, extension de balisage](../wpf/advanced/binding-markup-extension.md)
