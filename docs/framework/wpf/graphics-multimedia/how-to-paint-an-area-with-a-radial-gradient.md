---
title: 'Procédure : Peindre une zone avec un pinceau dégradé radial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916097"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Procédure : Peindre une zone avec un pinceau dégradé radial
Cet exemple montre comment utiliser la <xref:System.Windows.Media.RadialGradientBrush> classe pour peindre une zone avec un dégradé radial.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Windows.Media.RadialGradientBrush> pour peindre un rectangle avec un dégradé radial qui passe du jaune au rouge, au bleu et au vert citron.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 L’illustration suivante montre le dégradé de l’exemple précédent. Les arrêts du dégradé ont été mis en surbrillance.  
  
 ![Points de dégradé dans un dégradé radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour la définition des points de contrôle. Le système de coordonnées par défaut est relatif à un cadre englobant: 0 indique 0 pour cent de la zone englobante, et 1 indique 100 pour cent de la zone englobante. Vous pouvez modifier ce système de coordonnées en affectant à la <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriété la valeur. <xref:System.Windows.Media.BrushMappingMode.Absolute> Un système de coordonnées absolu n’est pas relatif à un rectangle englobant. Les valeurs sont interprétées directement dans l’espace local.  
  
 Pour obtenir <xref:System.Windows.Media.RadialGradientBrush> des exemples supplémentaires, consultez l' [exemple pinceaux](https://go.microsoft.com/fwlink/?LinkID=159973). Pour plus d’informations sur les dégradés et d’autres types de pinceaux, consultez [vue d’ensemble de la peinture avec des couleurs unies et](painting-with-solid-colors-and-gradients-overview.md)des dégradés.
