---
title: Modèles et styles intralignes
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460004"
---
# <a name="inline-styles-and-templates"></a>Modèles et styles intralignes
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit des objets <xref:System.Windows.Style> et des objets de modèle (<xref:System.Windows.FrameworkTemplate> sous-classes) comme un moyen de définir l’apparence visuelle d’un élément dans les ressources, afin qu’ils puissent être utilisés plusieurs fois. Pour cette raison, les attributs de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui prennent les types <xref:System.Windows.Style> et <xref:System.Windows.FrameworkTemplate>nt presque toujours créer des références de ressource aux styles et aux modèles existants, plutôt que d’en définir d’autres Inline.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Limitations des styles et des modèles Inline  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], il est techniquement possible de définir les propriétés de style et de modèle de deux manières. Vous pouvez utiliser la syntaxe d’attribut pour faire référence à un style qui a été défini dans une ressource, par exemple `<`*objet*`Style="{StaticResource`*myResourceKey*`}" .../>`. Ou vous pouvez utiliser la syntaxe d’élément de propriété pour définir un style inline, par exemple :  
  
 *objet* `<` `>`  
  
 *objet* `<` `.Style>`  
  
 `<` `Style``.../>`  
  
 *objet* `</` `.Style>`  
  
 *objet* `</` `>`  
  
 L’utilisation des attributs est bien plus courante. Un style défini en ligne et non défini dans les ressources est nécessairement limité à l’élément conteneur uniquement et ne peut pas être réutilisé facilement, car il n’a pas de clé de ressource. En général, un style défini par ressource est plus polyvalent et utile, et est plus conforme au principe général du modèle de programmation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de la séparation de la logique du programme dans le code de la conception dans le balisage.  
  
 En général, il n’y a aucune raison de définir un style ou un modèle Inline, même si vous envisagez uniquement d’utiliser ce style ou ce modèle dans cet emplacement. La plupart des éléments qui peuvent prendre un style ou un modèle prennent également en charge une propriété de contenu et un modèle de contenu. Si vous utilisez uniquement l’arborescence logique que vous créez par le biais du style ou de la création de modèles, il serait encore plus facile de remplir cette propriété de contenu avec les éléments enfants équivalents dans le balisage direct. Cela contournerait complètement les mécanismes de style et de modèle.  
  
 D’autres syntaxes activées par les extensions de balisage qui retournent un objet sont également possibles pour les styles et les modèles. Deux extensions de ce type qui ont des scénarios possibles incluent [TemplateBinding](templatebinding-markup-extension.md) et <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
