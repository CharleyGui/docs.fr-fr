---
title: 'Comment : définir et référencer une ressource'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460173"
---
# <a name="how-to-define-and-reference-a-resource"></a>Comment : définir et référencer une ressource

Cet exemple montre comment définir une ressource et la référencer à l’aide d’un attribut dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Exemple

L’exemple suivant définit deux types de ressources : une ressource <xref:System.Windows.Media.SolidColorBrush> et plusieurs ressources <xref:System.Windows.Style>. La ressource <xref:System.Windows.Media.SolidColorBrush> `MyBrush` est utilisée pour fournir la valeur de plusieurs propriétés qui acceptent chacune une valeur de type <xref:System.Windows.Media.Brush>. Les ressources <xref:System.Windows.Style> `PageBackground`, `TitleText` et `Label` chaque cible un type de contrôle particulier. Les styles définissent une variété de propriétés différentes sur les contrôles ciblés, lorsque cette ressource de style est référencée par la clé de ressource et est utilisée pour définir la propriété <xref:System.Windows.FrameworkElement.Style%2A> de plusieurs éléments de contrôle spécifiques définis dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Notez que l’une des propriétés dans les accesseurs set du style `Label` fait également référence à la ressource `MyBrush` définie précédemment. Il s’agit d’une technique courante, mais il est important de se souvenir que les ressources sont analysées et entrées dans un dictionnaire de ressources dans l’ordre dans lequel elles sont fournies. Les ressources sont également demandées par la commande trouvée dans le dictionnaire si vous utilisez l' [extension de balisage StaticResource](staticresource-markup-extension.md) pour les référencer à partir d’une autre ressource. Assurez-vous qu’une ressource que vous référencez est définie plus tôt dans la collection de ressources que dans laquelle cette ressource est ensuite demandée. Si nécessaire, vous pouvez contourner l’ordre de création strict des références de ressource en utilisant une [extension de balisage DynamicResource](dynamicresource-markup-extension.md) pour référencer la ressource au moment de l’exécution, mais vous devez savoir que cette technique DynamicResource a des performances. incidences. Pour plus d’informations, consultez [ressources XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Voir aussi

- [Ressources XAML](xaml-resources.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
