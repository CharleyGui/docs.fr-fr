---
title: Vue d'ensemble des événements de minutage
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145408"
---
# <a name="timing-events-overview"></a>Vue d'ensemble des événements de minutage
Ce sujet décrit comment utiliser les cinq <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> événements de chronométrage disponibles sur et des objets.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez être en mesure de créer et d’utiliser des animations. Pour commencer avec l’animation, voir [l’Aperçu de l’animation](animation-overview.md).  
  
 Il existe de multiples façons [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]d’animer les propriétés dans :  
  
- **À l’aide d’objets storyboard** <xref:System.Windows.Media.Animation.Storyboard> (balisage et code) : vous pouvez utiliser des objets pour organiser et distribuer des animations à un ou plusieurs objets. Par exemple, voir [Animate a Property en utilisant un storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **À l’aide d’animations locales** (code uniquement) : vous pouvez appliquer des <xref:System.Windows.Media.Animation.AnimationTimeline> objets directement aux propriétés qu’ils animent. Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **En utilisant des horloges** (code uniquement) : vous pouvez gérer la création d’horloge explicitement et distribuer vous-même les horloges d’animation.  Par exemple, voir [Animate a Property en utilisant une animationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Parce que vous pouvez les utiliser dans le balisage et le code, les exemples dans cette vue d’ensemble utilisent des <xref:System.Windows.Media.Animation.Storyboard> objets. Toutefois, les concepts décrits sont applicables aux autres méthodes d’animation des propriétés.  
  
### <a name="what-is-a-clock"></a>Qu’est-ce qu’une horloge ?  
 Une chronologie, par elle-même, ne fait rien d’autre que décrire un segment de temps. C’est l’objet <xref:System.Windows.Media.Animation.Clock> de la chronologie qui fait le vrai travail : il maintient l’état de temps de fonctionnement lié au calendrier pour le calendrier. Dans la plupart des cas, par exemple quand vous utilisez des tables de montage séquentiel, une horloge est créée automatiquement pour votre chronologie. Vous pouvez également <xref:System.Windows.Media.Animation.Clock> créer un <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> explicitement en utilisant la méthode. Pour plus <xref:System.Windows.Media.Animation.Clock> d’informations sur les objets, consultez [l’aperçu du système d’animation et de synchronisation](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Pourquoi utiliser des événements ?  
 À une exception près (seekAlignedToLastTick), toutes les opérations de minutage interactives sont asynchrones. Il n’existe aucun moyen de savoir exactement quand elles s’exécutent. Ceci peut être un problème lorsque vous avez d’autres codes qui dépendent de l’opération de minutage. Supposons que vous souhaitiez arrêter une chronologie qui animait un rectangle. Après l’arrêt de la chronologie, vous modifiez la couleur du rectangle.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Dans l’exemple précédent, la deuxième ligne de code peut s’exécuter avant l’arrêt de la table de montage séquentiel. Cela est dû au fait que l’arrêt est une opération asynchrone. Si vous demandez à une chronologie ou à une horloge de s’arrêter, elle crée une « demande d’arrêt » qui n’est pas traitée avant le prochain battement du moteur de minutage.  
  
 Pour exécuter des commandes après la fin d’une chronologie, utilisez les événements de minutage. Dans l’exemple suivant, un gestionnaire d’événements est utilisé pour modifier la couleur d’un rectangle, après l’arrêt de la table de montage séquentiel.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Pour un exemple plus complet, voir [Notification Recevoir la notification lorsque l’état d’une horloge change](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Événements publics  
 Les <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> deux et les classes fournissent cinq événements de chronométrage. Le tableau suivant répertorie ces événements et les conditions qui les déclenchent.  
  
|Événement|Opération interactive déclenchante|Autres déclencheurs|  
|-----------|--------------------------------------|--------------------|  
|**Terminé**|Passer au remplissage|L’horloge s’arrête.|  
|**CurrentGlobalSpeedInvalidated**|Suspendre, reprendre, rechercher, définir le ratio vitesse, passer au remplissage, s’arrêter|L’horloge s’inverse, accélère, démarre ou s’arrête.|  
|**CurrentStateInvalidated**|Démarrer, passer au remplissage, s’arrêter|L’horloge démarre, s’arrête ou remplit.|  
|**CurrentTimeInvalidated**|Démarrer, rechercher, passer au remplissage, s’arrêter|L’horloge progresse.|  
|**RemoveRequested**|Supprimer||  
  
## <a name="ticking-and-event-consolidation"></a>Cycles et regroupement des événements  
 Lorsque vous animez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]des objets dans , c’est le moteur de chronométrage qui gère vos animations. Le moteur de minutage suit l’écoulement du temps et calcule l’état de chaque animation. Il effectue plusieurs calculs de ce type en une seconde. Ces calculs sont appelés « cycles ».  
  
 Étant donné que ces cycles sont fréquents, beaucoup de choses peuvent se passer entre chaque cycle. Par exemple, une chronologie peut s’arrêter, démarrer et s’arrêter à nouveau. Dans ce cas, son état actuel aura changé trois fois. En théorie, l’événement peut être déclenché plusieurs fois dans un seul cycle. Toutefois, le moteur de minutage regroupe les événements, afin que chacun ne puisse être déclenché qu’une fois par cycle.  
  
## <a name="registering-for-events"></a>Inscription pour des événements  
 Il existe deux façons d’inscrire des événements de minutage : vous pouvez les inscrire avec la chronologie ou avec l’horloge créée à partir de la chronologie. Il est assez simple d’inscrire un événement directement avec une horloge, mais il n’est possible de le faire qu’à partir du code. Vous pouvez inscrire des événements avec une chronologie, à partir d’une balise ou du code. La section suivante décrit comment inscrire les événements d’horloge avec une chronologie.  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>Inscription des événements d’horloge avec une chronologie  
 Bien que la <xref:System.Windows.Media.Animation.Timeline.Completed> <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>chronologie, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> , <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, et les événements semblent être associés à la <xref:System.Windows.Media.Animation.Clock> chronologie, l’inscription à ces événements associe en fait un gestionnaire d’événements avec le créé pour la chronologie.  
  
 Lorsque vous vous <xref:System.Windows.Media.Animation.Timeline.Completed> inscrivez à l’événement sur une chronologie, par exemple, vous dites au système de vous inscrire à l’événement <xref:System.Windows.Media.Animation.Clock.Completed> de chaque horloge qui est créée pour la chronologie. Dans le code, vous devez <xref:System.Windows.Media.Animation.Clock> vous inscrire à cet événement avant que le soit créé pour cette chronologie; sinon, vous ne recevrez pas de notification. Cela se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]produit automatiquement dans ; le parseur s’inscrit automatiquement <xref:System.Windows.Media.Animation.Clock> à l’événement avant la création.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des comportements de minutage](timing-behaviors-overview.md)
