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
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544802"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData, type XAML intrinsèque
Active le placement des îlots de données XML dans une production XAML. Les éléments XML dans `x:XData` ne doivent pas être traités par les processeurs XAML comme s’ils font partie de l’espace de noms XAML par défaut en cours d’action ou de tout autre espace de noms XAML. `x:XData` peut contenir du code XML bien formé arbitrairement.

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
|`[elementData]`|Optionnel. XML qui représente les données XML. Vous pouvez faire figurer un nombre quelconque d’éléments en tant que données d’élément et les éléments imbriqués peuvent être contenus dans d’autres éléments ; Toutefois, les règles générales de XML s’appliquent.|

## <a name="remarks"></a>Notes

Les éléments XML dans un `x:XData` objet peuvent redéclarer tous les espaces de noms et préfixes possibles de l’objet XMLDOM contenant les données.

L’accès par programme aux données XML et au `x:XData` type XAML intrinsèque est possible dans les services XAML .NET par le biais de la <xref:System.Windows.Markup.XData> classe.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

L' `x:XData` objet est principalement utilisé comme un objet enfant d’un objet <xref:System.Windows.Data.XmlDataProvider> , ou, en tant qu’objet enfant de la <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriété (en XAML, il est généralement exprimé dans la syntaxe d’élément de propriété).

Les données doivent généralement redéfinir l’espace de noms XML de base dans l’îlot de données pour qu’il s’agit d’un nouvel espace de noms XML par défaut (défini sur une chaîne vide). Cela est plus facile pour les îlots de données simples, car les <xref:System.Windows.Data.Binding.XPath%2A> expressions utilisées pour référencer les données et les lier aux données peuvent éviter l’inclusion de préfixes. Des îlots de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de noms XML à la racine. Dans ce cas, toutes les <xref:System.Windows.Data.Binding.XPath%2A> références d’expression doivent inclure le préfixe mappé à l’espace de noms approprié. Pour plus d’informations, consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.

Techniquement, `x:XData` peut être utilisé comme contenu de n’importe quelle propriété de type <xref:System.Xml.Serialization.IXmlSerializable> . Toutefois, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule implémentation évidente.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.XmlDataProvider>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Liaison avec l’extension de balisage](/dotnet/desktop/wpf/advanced/binding-markup-extension)
