---
title: 'Procédure : Utiliser des déclencheurs d’événements pour contrôler une table de montage séquentiel après son démarrage'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855846"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="b20ff-102">Procédure : Utiliser des déclencheurs d’événements pour contrôler une table de montage séquentiel après son démarrage</span><span class="sxs-lookup"><span data-stu-id="b20ff-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="b20ff-103">Cet exemple montre comment contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="b20ff-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="b20ff-104">Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> à l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]aide de <xref:System.Windows.Media.Animation.BeginStoryboard>, utilisez, qui distribue les animations aux objets et propriétés qu’ils animent, puis démarre le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="b20ff-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="b20ff-105">Si vous donnez <xref:System.Windows.Media.Animation.BeginStoryboard> un nom en spécifiant <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> sa propriété, vous en faites une table de montage séquentiel contrôlable.</span><span class="sxs-lookup"><span data-stu-id="b20ff-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="b20ff-106">Vous pouvez ensuite contrôler de manière interactive le storyboard après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="b20ff-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="b20ff-107">Utilisez les actions de Storyboard suivantes avec <xref:System.Windows.EventTrigger> des objets pour contrôler une table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="b20ff-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="b20ff-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Suspend le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="b20ff-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="b20ff-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend une table de montage séquentiel suspendue.</span><span class="sxs-lookup"><span data-stu-id="b20ff-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="b20ff-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifie la vitesse de la table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="b20ff-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="b20ff-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Fait avancer un Storyboard jusqu’à la fin de sa période de remplissage, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b20ff-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="b20ff-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Arrête le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="b20ff-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="b20ff-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le Storyboard, en libérant des ressources.</span><span class="sxs-lookup"><span data-stu-id="b20ff-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="b20ff-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="b20ff-114">Example</span></span>

<span data-ttu-id="b20ff-115">L’exemple suivant utilise des actions de Storyboard contrôlable pour contrôler de manière interactive une table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="b20ff-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="b20ff-116">Pour voir un exemple de contrôle d’une table de montage séquentiel à l’aide de code, consultez [contrôler une table de montage séquentiel après son démarrage à l’aide de ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="b20ff-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="b20ff-117">Pour obtenir des exemples supplémentaires, consultez la Galerie d’exemples d' [animation](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="b20ff-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="b20ff-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b20ff-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="b20ff-119">Contrôler un storyboard après son démarrage à l'aide de ses méthodes interactives</span><span class="sxs-lookup"><span data-stu-id="b20ff-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="b20ff-120">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="b20ff-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b20ff-121">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="b20ff-121">Storyboards Overview</span></span>](storyboards-overview.md)
