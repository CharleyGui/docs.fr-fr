---
title: 'Procédure : Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930159"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Procédure : Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)
L’exemple suivant montre comment contrôler la lecture d’un média à <xref:System.Windows.Controls.MediaElement>l’aide d’un. L’exemple crée un lecteur multimédia simple qui vous permet de lire, d’interrompre, d’arrêter et d’ignorer les éléments du support, ainsi que d’ajuster le volume et la vitesse.  
  
## <a name="example"></a>Exemples  
 Le code ci-dessous crée l’interface utilisateur.  
  
> [!NOTE]
> La <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriété de <xref:System.Windows.Controls.MediaElement> doit être définie sur `Manual` afin de pouvoir arrêter, suspendre et lire interactivement le média.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous implémente les fonctionnalités des exemples de contrôles d’interface utilisateur. Les <xref:System.Windows.Controls.MediaElement.Play%2A>méthodes <xref:System.Windows.Controls.MediaElement.Pause%2A>, et<xref:System.Windows.Controls.MediaElement.Stop%2A> sont utilisées pour lire, suspendre et arrêter le média. La modification <xref:System.Windows.Controls.MediaElement.Position%2A> <xref:System.Windows.Controls.MediaElement> de la propriété du vous permet d’ignorer le contenu multimédia. Enfin, les <xref:System.Windows.Controls.MediaElement.Volume%2A> propriétés <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> et sont utilisées pour ajuster le volume et la vitesse de lecture du média.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Contrôler un MediaElement à l'aide d'un storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md)
