---
title: 'Comment : contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)'
description: Contrôler la lecture des médias dans Windows Presentation Foundation (WPF). Démarrer, arrêter, suspendre, ignorer et basculer, et ajuster le volume et la vitesse.
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
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853599"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Comment : contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)
L’exemple suivant montre comment contrôler la lecture d’un média à l’aide d’un <xref:System.Windows.Controls.MediaElement> . L’exemple crée un lecteur multimédia simple qui vous permet de lire, d’interrompre, d’arrêter et d’ignorer les éléments du support, ainsi que d’ajuster le volume et la vitesse.  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous crée l’interface utilisateur.  
  
> [!NOTE]
> La <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriété de <xref:System.Windows.Controls.MediaElement> doit être définie sur afin de pouvoir `Manual` arrêter, suspendre et lire interactivement le média.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous implémente les fonctionnalités des exemples de contrôles d’interface utilisateur. Les <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A> méthodes, et <xref:System.Windows.Controls.MediaElement.Stop%2A> sont utilisées pour lire, suspendre et arrêter le média. La modification <xref:System.Windows.Controls.MediaElement.Position%2A> de la propriété du <xref:System.Windows.Controls.MediaElement> vous permet d’ignorer le contenu multimédia. Enfin, les <xref:System.Windows.Controls.MediaElement.Volume%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> Propriétés et sont utilisées pour ajuster le volume et la vitesse de lecture du média.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Contrôler un MediaElement à l’aide d’une table de montage séquentiel](how-to-control-a-mediaelement-by-using-a-storyboard.md)
