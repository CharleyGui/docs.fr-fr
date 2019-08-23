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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="2f374-102">Procédure : Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)</span><span class="sxs-lookup"><span data-stu-id="2f374-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="2f374-103">L’exemple suivant montre comment contrôler la lecture d’un média à <xref:System.Windows.Controls.MediaElement>l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="2f374-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="2f374-104">L’exemple crée un lecteur multimédia simple qui vous permet de lire, d’interrompre, d’arrêter et d’ignorer les éléments du support, ainsi que d’ajuster le volume et la vitesse.</span><span class="sxs-lookup"><span data-stu-id="2f374-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f374-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f374-105">Example</span></span>  
 <span data-ttu-id="2f374-106">Le code ci-dessous crée l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f374-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f374-107">La <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriété de <xref:System.Windows.Controls.MediaElement> doit être définie sur `Manual` afin de pouvoir arrêter, suspendre et lire interactivement le média.</span><span class="sxs-lookup"><span data-stu-id="2f374-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="2f374-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f374-108">Example</span></span>  
 <span data-ttu-id="2f374-109">Le code ci-dessous implémente les fonctionnalités des exemples de contrôles d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f374-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="2f374-110">Les <xref:System.Windows.Controls.MediaElement.Play%2A>méthodes <xref:System.Windows.Controls.MediaElement.Pause%2A>, et<xref:System.Windows.Controls.MediaElement.Stop%2A> sont utilisées pour lire, suspendre et arrêter le média.</span><span class="sxs-lookup"><span data-stu-id="2f374-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="2f374-111">La modification <xref:System.Windows.Controls.MediaElement.Position%2A> <xref:System.Windows.Controls.MediaElement> de la propriété du vous permet d’ignorer le contenu multimédia.</span><span class="sxs-lookup"><span data-stu-id="2f374-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="2f374-112">Enfin, les <xref:System.Windows.Controls.MediaElement.Volume%2A> propriétés <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> et sont utilisées pour ajuster le volume et la vitesse de lecture du média.</span><span class="sxs-lookup"><span data-stu-id="2f374-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2f374-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f374-113">See also</span></span>

- [<span data-ttu-id="2f374-114">Contrôler un MediaElement à l'aide d'un storyboard</span><span class="sxs-lookup"><span data-stu-id="2f374-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
