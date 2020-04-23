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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071541"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData, type XAML intrinsèque
Permet le placement d’îles de données XML dans une production XAML. Les éléments `x:XData` XML à l’intérieur ne doivent pas être traités par les processeurs XAML comme s’ils faisaient partie de l’espace de nom XAML par défaut d’action ou tout autre espace de nom XAML. `x:XData`peut contenir un XML arbitraire bien formé.

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
|`elementDataRoot`|L’élément racine unique de l’île de données fermée. Pour la plupart des consommateurs éventuels, XML qui n’a pas une seule racine est considéré comme invalide. En particulier, une seule racine `x:XData` est nécessaire si l’est destiné comme une source de données XML pour WPF ou de nombreuses autres technologies qui utilisent des sources XML pour la liaison de données.|
|`[elementData]`|facultatif. XML qui représente les données XML. N’importe quel nombre d’éléments peut être contenu comme données d’éléments et les éléments imbriqués peuvent être contenus dans d’autres éléments; cependant, les règles générales de XML s’appliquent.|

## <a name="remarks"></a>Notes

Les éléments XML `x:XData` d’un objet peuvent re-déclarer tous les espaces de nom possibles et les préfixes du XMLDOM contenant dans les données.

L’accès programmatique aux `x:XData` données XML et au type XAML intrinsèque <xref:System.Windows.Markup.XData> est possible dans .NET XAML Services à travers la classe.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

L’objet `x:XData` est principalement utilisé comme <xref:System.Windows.Data.XmlDataProvider>objet enfant d’un , ou <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> alternativement, comme l’objet enfant de la propriété (dans XAML, cela est généralement exprimé dans la syntaxe élément de propriété).

Les données doivent généralement redéfinir l’espace de nom XML de base dans l’île de données pour être un nouvel espace de nom XML par défaut (réglé sur une chaîne vide). Ceci est plus facile pour <xref:System.Windows.Data.Binding.XPath%2A> les îles de données simples parce que les expressions qui sont utilisées pour référencer et se lier aux données peuvent éviter l’inclusion de préfixes. Des îles de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de nom XML à la racine. Dans ce cas, toutes les <xref:System.Windows.Data.Binding.XPath%2A> références d’expression doivent inclure le préfixe approprié cartographié par l’espace de nom. Pour plus d’informations, voir [Aperçu de la liaison des données](../data/data-binding-overview.md).

Techniquement, `x:XData` peut être utilisé comme le <xref:System.Xml.Serialization.IXmlSerializable>contenu de toute propriété de type . Cependant, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule mise en œuvre importante.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.XmlDataProvider>
- [Aperçu de la liaison de données](../data/data-binding-overview.md)
- [Binding, extension de balisage](../../framework/wpf/advanced/binding-markup-extension.md)
