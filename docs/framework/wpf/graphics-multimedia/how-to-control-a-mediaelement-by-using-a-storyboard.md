---
title: "Comment : contrôler un MediaElement à l'aide d'un storyboard"
description: Contrôler la lecture de médias à l’aide d’un Storyboard dans Windows Presentation Foundation (WPF). Prenons l’exemple suivant pour créer un lecteur multimédia simple.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853738"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Comment : contrôler un MediaElement à l'aide d'un storyboard
Cet exemple montre comment contrôler un <xref:System.Windows.Controls.MediaElement> en utilisant un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> .  
  
## <a name="example"></a>Exemple  
 Quand vous utilisez un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> pour contrôler le minutage d’un <xref:System.Windows.Controls.MediaElement> , les fonctionnalités sont identiques à celles d’autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que les animations. Par exemple, un <xref:System.Windows.Media.MediaTimeline> utilise des <xref:System.Windows.Media.Animation.Timeline> propriétés telles que la <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété pour spécifier le moment où démarrer un <xref:System.Windows.Controls.MediaElement> (démarrer la lecture du média). Elle utilise également la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété pour spécifier la durée pendant laquelle le <xref:System.Windows.Controls.MediaElement> est actif (durée de la lecture du média). Pour plus d’informations sur l’utilisation d' <xref:System.Windows.Media.Animation.Timeline> objets avec un <xref:System.Windows.Media.Animation.Storyboard> , consultez [vue d’ensemble des storyboards](storyboards-overview.md).  
  
 Cet exemple montre comment créer un lecteur multimédia simple qui utilise un <xref:System.Windows.Media.MediaTimeline> pour contrôler la lecture. Le lecteur multimédia comprend des boutons lire, suspendre, reprendre et arrêter. Le lecteur possède également un <xref:System.Windows.Controls.Slider> contrôle qui agit comme une barre de progression.  
  
 L’exemple suivant crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pour le lecteur multimédia.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 L’exemple suivant crée les fonctionnalités de la barre de progression.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Vue d'ensemble des storyboards](storyboards-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble de l'animation](animation-overview.md)
- [Rubriques de procédures](audio-and-video-how-to-topics.md)
- [Graphiques et multimédia](index.md)
