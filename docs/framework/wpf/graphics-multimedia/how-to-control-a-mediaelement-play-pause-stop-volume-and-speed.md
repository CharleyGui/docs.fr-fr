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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="88769-104">Comment : contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)</span><span class="sxs-lookup"><span data-stu-id="88769-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="88769-105">L’exemple suivant montre comment contrôler la lecture d’un média à l’aide d’un <xref:System.Windows.Controls.MediaElement> .</span><span class="sxs-lookup"><span data-stu-id="88769-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="88769-106">L’exemple crée un lecteur multimédia simple qui vous permet de lire, d’interrompre, d’arrêter et d’ignorer les éléments du support, ainsi que d’ajuster le volume et la vitesse.</span><span class="sxs-lookup"><span data-stu-id="88769-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88769-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="88769-107">Example</span></span>  
 <span data-ttu-id="88769-108">Le code ci-dessous crée l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="88769-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88769-109">La <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriété de <xref:System.Windows.Controls.MediaElement> doit être définie sur afin de pouvoir `Manual` arrêter, suspendre et lire interactivement le média.</span><span class="sxs-lookup"><span data-stu-id="88769-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="88769-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="88769-110">Example</span></span>  
 <span data-ttu-id="88769-111">Le code ci-dessous implémente les fonctionnalités des exemples de contrôles d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="88769-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="88769-112">Les <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A> méthodes, et <xref:System.Windows.Controls.MediaElement.Stop%2A> sont utilisées pour lire, suspendre et arrêter le média.</span><span class="sxs-lookup"><span data-stu-id="88769-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="88769-113">La modification <xref:System.Windows.Controls.MediaElement.Position%2A> de la propriété du <xref:System.Windows.Controls.MediaElement> vous permet d’ignorer le contenu multimédia.</span><span class="sxs-lookup"><span data-stu-id="88769-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="88769-114">Enfin, les <xref:System.Windows.Controls.MediaElement.Volume%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> Propriétés et sont utilisées pour ajuster le volume et la vitesse de lecture du média.</span><span class="sxs-lookup"><span data-stu-id="88769-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="88769-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88769-115">See also</span></span>

- [<span data-ttu-id="88769-116">Contrôler un MediaElement à l’aide d’une table de montage séquentiel</span><span class="sxs-lookup"><span data-stu-id="88769-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
