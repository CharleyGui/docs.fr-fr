---
title: 'Procédure : Contrôler un storyboard après son démarrage'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855865"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="ce552-102">Procédure : Contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="ce552-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="ce552-103">Cet exemple montre comment utiliser du code pour contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="ce552-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="ce552-104">Pour contrôler un Storyboard dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez <xref:System.Windows.Trigger> les <xref:System.Windows.TriggerAction> objets et ; pour obtenir un exemple, consultez [utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="ce552-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="ce552-105">Pour démarrer une table de montage séquentiel, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> vous utilisez sa méthode, qui distribue les animations de la table de montage séquentiel aux propriétés qu’elles animent et démarre le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="ce552-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="ce552-106">Pour rendre un Storyboard contrôlable, vous utilisez la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode et spécifiez **true** comme deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="ce552-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="ce552-107">Vous pouvez ensuite utiliser les méthodes interactives de la table de montage séquentiel pour suspendre, reprendre, Rechercher, arrêter, accélérer ou ralentir le Storyboard, ou l’avancer jusqu’à sa période de remplissage.</span><span class="sxs-lookup"><span data-stu-id="ce552-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="ce552-108">Voici une liste des méthodes interactives de la table de montage séquentiel :</span><span class="sxs-lookup"><span data-stu-id="ce552-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="ce552-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Suspend le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="ce552-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="ce552-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Reprend une table de montage séquentiel suspendue.</span><span class="sxs-lookup"><span data-stu-id="ce552-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="ce552-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Définit la vitesse interactive de la table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="ce552-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="ce552-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Recherche l’emplacement spécifié dans le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="ce552-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="ce552-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Recherche le Storyboard à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce552-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="ce552-114">Contrairement à <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> la méthode, cette opération est traitée avant le cycle suivant.</span><span class="sxs-lookup"><span data-stu-id="ce552-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="ce552-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Fait avancer le Storyboard jusqu’à sa période de remplissage, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ce552-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="ce552-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Arrête le Storyboard.</span><span class="sxs-lookup"><span data-stu-id="ce552-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="ce552-117">Dans l’exemple suivant, plusieurs méthodes de Storyboard sont utilisées pour contrôler de manière interactive une table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="ce552-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="ce552-118">Pour voir un exemple de contrôle d’une table de montage séquentiel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]à l’aide de déclencheurs avec, consultez [utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="ce552-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="ce552-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce552-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="ce552-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce552-120">See also</span></span>

- [<span data-ttu-id="ce552-121">Utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="ce552-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
