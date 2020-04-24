---
title: 'Comment : définir et référencer une ressource'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646512"
---
# <a name="how-to-define-and-reference-a-resource"></a>Comment : définir et référencer une ressource

Cet exemple montre comment définir une ressource et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]la référencer en utilisant un attribut dans .

## <a name="example"></a>Exemple

L’exemple suivant définit deux types <xref:System.Windows.Media.SolidColorBrush> de ressources <xref:System.Windows.Style> : une ressource et plusieurs ressources. La <xref:System.Windows.Media.SolidColorBrush> `MyBrush` ressource est utilisée pour fournir la valeur <xref:System.Windows.Media.Brush> de plusieurs propriétés qui prennent chacune une valeur de type. Les <xref:System.Windows.Style> `PageBackground` `TitleText` ressources, `Label` et chaque cible un type de contrôle particulier. Les styles fixent une variété de propriétés différentes sur les contrôles ciblés, lorsque <xref:System.Windows.FrameworkElement.Style%2A> cette ressource de style [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]est référencée par clé de ressource et est utilisée pour définir la propriété de plusieurs éléments de contrôle spécifiques définis dans .

Notez que l’une des propriétés dans les setters du `Label` style fait également référence à la `MyBrush` ressource définie plus tôt. Il s’agit d’une technique courante, mais il est important de se rappeler que les ressources sont analysées et inscrites dans un dictionnaire des ressources dans l’ordre qu’elles sont données. Les ressources sont également demandées par la commande trouvée dans le dictionnaire si vous utilisez [l’extension de balisage StaticResource](staticresource-markup-extension.md) pour les référer à partir d’une autre ressource. Assurez-vous que toute ressource que vous faites référence est définie plus tôt dans la collecte des ressources que lorsque cette ressource est alors demandée. Si nécessaire, vous pouvez contourner l’ordre de création strict de références de ressources en utilisant une [extension de markup DynamicResource](dynamicresource-markup-extension.md) pour référencer la ressource au moment de l’exécution à la place, mais vous devez être conscient que cette technique DynamicResource a des conséquences de performance. Pour plus de détails, voir [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
