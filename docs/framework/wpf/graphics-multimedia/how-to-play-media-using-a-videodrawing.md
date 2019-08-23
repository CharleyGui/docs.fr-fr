---
title: 'Procédure : Lire un média à l’aide d’un VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956952"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Procédure : Lire un média à l’aide d’un VideoDrawing
Pour lire un fichier audio ou vidéo, utilisez un <xref:System.Windows.Media.VideoDrawing> et un. <xref:System.Windows.Media.MediaPlayer> Il y a deux façons de charger et de lire des médias. La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> par eux-mêmes, et la deuxième consiste à créer votre <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> propre à utiliser avec et <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour obtenir un contrôle de minutage supplémentaire sur le média, <xref:System.Windows.Media.MediaTimeline> utilisez un <xref:System.Windows.Media.MediaPlayer> avec <xref:System.Windows.Media.VideoDrawing> les objets et. Vous <xref:System.Windows.Media.MediaTimeline> permet de spécifier si la vidéo doit se répéter.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec les <xref:System.Windows.Media.MediaPlayer> objets <xref:System.Windows.Media.VideoDrawing> et pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que, lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline>, vous utilisez le interactif <xref:System.Windows.Media.Animation.ClockController> retourné <xref:System.Windows.Media.MediaClock> à partir <xref:System.Windows.Media.Animation.Clock.Controller%2A> de la propriété de pour contrôler la lecture du média au lieu des <xref:System.Windows.Media.MediaPlayer>méthodes interactives de.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.VideoDrawing>
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
