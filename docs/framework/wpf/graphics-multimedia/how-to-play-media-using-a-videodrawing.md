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
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="61a18-102">Procédure : Lire un média à l’aide d’un VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="61a18-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="61a18-103">Pour lire un fichier audio ou vidéo, utilisez un <xref:System.Windows.Media.VideoDrawing> et un. <xref:System.Windows.Media.MediaPlayer></span><span class="sxs-lookup"><span data-stu-id="61a18-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="61a18-104">Il y a deux façons de charger et de lire des médias.</span><span class="sxs-lookup"><span data-stu-id="61a18-104">There are two ways to load and play media.</span></span> <span data-ttu-id="61a18-105">La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> par eux-mêmes, et la deuxième consiste à créer votre <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> propre à utiliser avec et <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="61a18-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a18-106">Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image.</span><span class="sxs-lookup"><span data-stu-id="61a18-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="61a18-107">Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.</span><span class="sxs-lookup"><span data-stu-id="61a18-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a18-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="61a18-108">Example</span></span>  
 <span data-ttu-id="61a18-109">L’exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.</span><span class="sxs-lookup"><span data-stu-id="61a18-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="61a18-110">Pour obtenir un contrôle de minutage supplémentaire sur le média, <xref:System.Windows.Media.MediaTimeline> utilisez un <xref:System.Windows.Media.MediaPlayer> avec <xref:System.Windows.Media.VideoDrawing> les objets et.</span><span class="sxs-lookup"><span data-stu-id="61a18-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="61a18-111">Vous <xref:System.Windows.Media.MediaTimeline> permet de spécifier si la vidéo doit se répéter.</span><span class="sxs-lookup"><span data-stu-id="61a18-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a18-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="61a18-112">Example</span></span>  
 <span data-ttu-id="61a18-113">L’exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec les <xref:System.Windows.Media.MediaPlayer> objets <xref:System.Windows.Media.VideoDrawing> et pour lire une vidéo à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="61a18-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="61a18-114">Notez que, lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline>, vous utilisez le interactif <xref:System.Windows.Media.Animation.ClockController> retourné <xref:System.Windows.Media.MediaClock> à partir <xref:System.Windows.Media.Animation.Clock.Controller%2A> de la propriété de pour contrôler la lecture du média au lieu des <xref:System.Windows.Media.MediaPlayer>méthodes interactives de.</span><span class="sxs-lookup"><span data-stu-id="61a18-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a18-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a18-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="61a18-116">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="61a18-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
