---
title: Initialisation d'éléments objet ne figurant pas dans une arborescence d'objets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: b0032492a9403660e91980f5e968b519a4306589
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610493"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Initialisation d'éléments objet ne figurant pas dans une arborescence d'objets
Certains aspects de l’initialisation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont différés à des processus qui reposent généralement sur le fait que cet élément est connecté à l’arborescence logique ou à l’arborescence d’éléments visuels. Cette rubrique décrit les étapes qui peuvent être nécessaires pour initialiser un élément qui n’est connecté à aucune de ces arborescences.  

## <a name="elements-and-the-logical-tree"></a>Éléments et arborescence logique  
 Quand vous créez une instance d’une classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans le code, vous devez savoir que plusieurs aspects de l’initialisation de l’objet pour une classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne font délibérément pas partie du code qui est exécuté lors de l’appel du constructeur de classe. En particulier pour une classe de contrôle, la majeure partie de la représentation visuelle de ce contrôle n’est pas définie par le constructeur. Au lieu de cela, la représentation visuelle est définie par le modèle du contrôle. Le modèle peut provenir de diverses sources, mais le plus souvent il est obtenu à partir de styles de thème. Les modèles sont en fait à liaison tardive ; le modèle nécessaire n’est attaché au contrôle en question qu’une fois le contrôle prêt pour la disposition. Et le contrôle est prêt pour la disposition seulement une fois qu’il est attaché à une arborescence logique qui se connecte à une surface de rendu à la racine. C’est cet élément de niveau racine qui démarre le rendu de tous ses éléments enfants tels que définis dans l’arborescence logique.  
  
 L’arborescence d’éléments visuels participe également à ce processus. De plus, les éléments qui font partie de l’arborescence d’éléments visuels par l’intermédiaire des modèles ne sont totalement instanciés que quand ils sont connectés.  
  
 Les conséquences de ce comportement sont que certaines opérations qui reposent sur l’achèvement des caractéristiques visuelles d’un élément nécessitent des étapes supplémentaires. (par exemple si vous essayez d’obtenir les caractéristiques visuelles d’une classe qui a été construite mais pas encore attachée à une arborescence). Par exemple, si vous souhaitez appeler <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> sur un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et le visuel que vous transmettez est un élément non connecté à une arborescence, cet élément n’est pas terminé visuellement tant que vous devez effectuer les étapes d’initialisation supplémentaires.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Utilisation de BeginInit et EndInit pour initialiser l’élément  
 Différentes classes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémenter la <xref:System.ComponentModel.ISupportInitialize> interface. Vous utilisez le <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> et <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> méthodes de l’interface pour désigner une région dans votre code qui contient les étapes d’initialisation (telles que la définition de propriété valeurs affectant le rendu). Après avoir <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> est appelée dans la séquence, le système de disposition peut traiter l’élément et commencer à rechercher un style implicite.  
  
 Si l’élément vous définissez les propriétés est un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe dérivée, vous pouvez appeler les versions de la classe de <xref:System.Windows.FrameworkElement.BeginInit%2A> et <xref:System.Windows.FrameworkElement.EndInit%2A> au lieu d’effectuer un cast vers <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Exemple de code  
 L’exemple suivant est l’exemple de code pour une application console qui utilise le rendu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] et <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> de libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier pour illustrer le positionnement correct de <xref:System.Windows.FrameworkElement.BeginInit%2A> et <xref:System.Windows.FrameworkElement.EndInit%2A> autour d’autres appels d’API ajustent propriétés qui affectent le rendu.  
  
 L’exemple illustre uniquement la fonction principale. Les fonctions `Rasterize` et `Save` (non illustrées) sont des fonctions utilitaires qui assurent le traitement d’image et les E/S.  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Voir aussi

- [Arborescences dans WPF](trees-in-wpf.md)
- [Vue d’ensemble du rendu graphique de WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
