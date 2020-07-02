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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="aabfb-104">Comment : contrôler un MediaElement à l'aide d'un storyboard</span><span class="sxs-lookup"><span data-stu-id="aabfb-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="aabfb-105">Cet exemple montre comment contrôler un <xref:System.Windows.Controls.MediaElement> en utilisant un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> .</span><span class="sxs-lookup"><span data-stu-id="aabfb-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aabfb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="aabfb-106">Example</span></span>  
 <span data-ttu-id="aabfb-107">Quand vous utilisez un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> pour contrôler le minutage d’un <xref:System.Windows.Controls.MediaElement> , les fonctionnalités sont identiques à celles d’autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que les animations.</span><span class="sxs-lookup"><span data-stu-id="aabfb-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="aabfb-108">Par exemple, un <xref:System.Windows.Media.MediaTimeline> utilise des <xref:System.Windows.Media.Animation.Timeline> propriétés telles que la <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété pour spécifier le moment où démarrer un <xref:System.Windows.Controls.MediaElement> (démarrer la lecture du média).</span><span class="sxs-lookup"><span data-stu-id="aabfb-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="aabfb-109">Elle utilise également la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété pour spécifier la durée pendant laquelle le <xref:System.Windows.Controls.MediaElement> est actif (durée de la lecture du média).</span><span class="sxs-lookup"><span data-stu-id="aabfb-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="aabfb-110">Pour plus d’informations sur l’utilisation d' <xref:System.Windows.Media.Animation.Timeline> objets avec un <xref:System.Windows.Media.Animation.Storyboard> , consultez [vue d’ensemble des storyboards](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aabfb-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="aabfb-111">Cet exemple montre comment créer un lecteur multimédia simple qui utilise un <xref:System.Windows.Media.MediaTimeline> pour contrôler la lecture.</span><span class="sxs-lookup"><span data-stu-id="aabfb-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="aabfb-112">Le lecteur multimédia comprend des boutons lire, suspendre, reprendre et arrêter.</span><span class="sxs-lookup"><span data-stu-id="aabfb-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="aabfb-113">Le lecteur possède également un <xref:System.Windows.Controls.Slider> contrôle qui agit comme une barre de progression.</span><span class="sxs-lookup"><span data-stu-id="aabfb-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="aabfb-114">L’exemple suivant crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pour le lecteur multimédia.</span><span class="sxs-lookup"><span data-stu-id="aabfb-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="aabfb-115">L’exemple suivant crée les fonctionnalités de la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="aabfb-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="aabfb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aabfb-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="aabfb-117">Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)</span><span class="sxs-lookup"><span data-stu-id="aabfb-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="aabfb-118">Vue d'ensemble des storyboards</span><span class="sxs-lookup"><span data-stu-id="aabfb-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="aabfb-119">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="aabfb-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="aabfb-120">Vue d'ensemble de l'animation</span><span class="sxs-lookup"><span data-stu-id="aabfb-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="aabfb-121">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="aabfb-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="aabfb-122">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="aabfb-122">Graphics and Multimedia</span></span>](index.md)
