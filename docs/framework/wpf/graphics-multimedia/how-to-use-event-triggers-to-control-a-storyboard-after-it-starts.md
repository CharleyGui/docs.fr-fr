---
title: "Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage"
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186704"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="cf514-102">Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="cf514-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="cf514-103">Cet exemple montre comment <xref:System.Windows.Media.Animation.Storyboard> contrôler un après qu’il commence.</span><span class="sxs-lookup"><span data-stu-id="cf514-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="cf514-104">Pour commencer <xref:System.Windows.Media.Animation.Storyboard> par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utiliser <xref:System.Windows.Media.Animation.BeginStoryboard>, utiliser , qui distribue les animations aux objets et aux propriétés qu’ils animent, puis commence le storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="cf514-105">Si vous <xref:System.Windows.Media.Animation.BeginStoryboard> donnez un nom <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> en spécifiant sa propriété, vous en faites un storyboard contrôlable.</span><span class="sxs-lookup"><span data-stu-id="cf514-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="cf514-106">Vous pouvez ensuite contrôler interactivement le storyboard après qu’il commence.</span><span class="sxs-lookup"><span data-stu-id="cf514-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="cf514-107">Utilisez les actions suivantes <xref:System.Windows.EventTrigger> de storyboard avec des objets pour contrôler un storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="cf514-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses du storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="cf514-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend un storyboard en pause.</span><span class="sxs-lookup"><span data-stu-id="cf514-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="cf514-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Change la vitesse du storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="cf514-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avance un storyboard jusqu’à la fin de sa période de remplissage, s’il en a un.</span><span class="sxs-lookup"><span data-stu-id="cf514-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="cf514-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Arrête le storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="cf514-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le storyboard, libérant des ressources.</span><span class="sxs-lookup"><span data-stu-id="cf514-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="cf514-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="cf514-114">Example</span></span>

<span data-ttu-id="cf514-115">L’exemple suivant utilise des actions de storyboard contrôlables pour contrôler de manière interactive un storyboard.</span><span class="sxs-lookup"><span data-stu-id="cf514-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="cf514-116">Pour voir un exemple de contrôle d’un storyboard en utilisant du code, voir [Contrôlez un storyboard après qu’il commence à utiliser ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="cf514-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="cf514-117">Pour d’autres exemples, voir [l’Animation Exemple Galerie](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="cf514-117">For additional examples, see the [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf514-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf514-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="cf514-119">Contrôler une table de montage séquentiel après son démarrage à l’aide de ses méthodes interactives</span><span class="sxs-lookup"><span data-stu-id="cf514-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="cf514-120">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="cf514-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="cf514-121">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="cf514-121">Storyboards Overview</span></span>](storyboards-overview.md)
