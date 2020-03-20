---
title: Vue d'ensemble des techniques d'animation de propriétés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181841"
---
# <a name="property-animation-techniques-overview"></a>Vue d'ensemble des techniques d'animation de propriétés
Cette rubrique décrit les différentes approches pour animer des propriétés : tables de montage séquentiel, animations locales, horloges et animations par image.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez connaître les fonctionnalités de base utilisées pour l’animation, décrites dans [Vue d’ensemble de l’animation](animation-overview.md).  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>Différentes méthodes d’animation  
 Puisque de nombreux scénarios différents d’animation de propriétés existent, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose plusieurs approches pour animer des propriétés.  
  
 Pour chaque approche, le tableau suivant indique si elle peut être utilisée par instance, dans des styles, dans des modèles de contrôle ou dans des modèles de données ; si elle peut être utilisée en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; et si l’approche vous permet de contrôler l’animation de manière interactive.  « Par instance » fait référence à la technique consistant à appliquer une animation ou une table de montage séquentiel directement aux instances d’un objet, plutôt qu’à un style, un modèle de contrôle ou un modèle de données.  
  
|Technique d’animation|Scénarios|XAML pris en charge|Contrôlable de manière interactive|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animation de table de montage séquentiel|Par exemple, <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate>, ,<xref:System.Windows.DataTemplate>|Oui|Oui|  
|Animation locale|Par instance|Non |Non |  
|Animation horloge|Par instance|Non |Oui|  
|Animation par image|Par instance|Non |N/A|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>Animations de table de montage séquentiel  
 Utilisez <xref:System.Windows.Media.Animation.Storyboard> un lorsque vous voulez définir et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]appliquer vos animations dans , contrôler interactivement vos animations après leur <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate> début, créer un arbre complexe d’animations, ou d’animer dans un , ou <xref:System.Windows.DataTemplate>. Pour qu’un objet <xref:System.Windows.Media.Animation.Storyboard>soit animé par <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>un, il doit être <xref:System.Windows.FrameworkElement> un <xref:System.Windows.FrameworkContentElement>ou , ou il doit être utilisé pour définir un ou . Pour plus d’informations, consultez l’article [Vue d’ensemble des tables de montage séquentiel](storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> est un type <xref:System.Windows.Media.Animation.Timeline> spécial de conteneur qui fournit des informations de ciblage pour les animations qu’il contient. Pour animer avec <xref:System.Windows.Media.Animation.Storyboard>un , vous complétez les trois étapes suivantes.  
  
1. Déclarez <xref:System.Windows.Media.Animation.Storyboard> une ou plusieurs animations.  
  
2. Utilisez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> les <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> propriétés et les propriétés ci-jointes pour spécifier l’objet cible et la propriété de chaque animation.  
  
3. (Code seulement) Définir <xref:System.Windows.NameScope> un <xref:System.Windows.FrameworkElement> pour <xref:System.Windows.FrameworkContentElement>un ou . Enregistrez les noms des objets à <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>animer avec cela ou .  
  
4. Commencer <xref:System.Windows.Media.Animation.Storyboard>le .  
  
 Début <xref:System.Windows.Media.Animation.Storyboard> d’une applique des animations aux propriétés qu’ils animent et les démarre. Il y a deux <xref:System.Windows.Media.Animation.Storyboard>façons de <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> commencer un <xref:System.Windows.Media.Animation.Storyboard> : vous pouvez utiliser <xref:System.Windows.Media.Animation.BeginStoryboard> la méthode fournie par la classe, ou vous pouvez utiliser une action. La seule façon d’animer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est <xref:System.Windows.Media.Animation.BeginStoryboard> d’utiliser une action. Une <xref:System.Windows.Media.Animation.BeginStoryboard> action peut être <xref:System.Windows.EventTrigger>utilisée <xref:System.Windows.Trigger>dans <xref:System.Windows.DataTrigger>un , propriété, ou un .  
  
 Le tableau suivant montre les <xref:System.Windows.Media.Animation.Storyboard> différents endroits où chaque technique de démarrage est pris en charge : par instance, style, modèle de contrôle et modèle de données.  
  
|La table de montage séquentiel démarre à l’aide de…|Par instance|Style|Modèle de contrôle|Modèle de données| Exemple|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et une propriété<xref:System.Windows.Trigger>|Non |Oui|Oui|Oui|[Déclencher une animation en cas de modification d’une valeur de propriété](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.DataTrigger>|Non |Oui|Oui|Oui|[Comment : déclencher une animation en cas de modification de données](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non |Non |Non |[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Pour plus <xref:System.Windows.Media.Animation.Storyboard> d’informations sur les objets, voir le [Aperçu Storyboards](storyboards-overview.md).  
  
## <a name="local-animations"></a>Animations locales  
 Les animations locales offrent un moyen pratique <xref:System.Windows.Media.Animation.Animatable> d’animer une propriété de dépendance de tout objet. Utilisez les animations locales lorsque vous souhaitez appliquer une seule animation à une propriété et quand vous n’avez pas besoin de contrôler de manière interactive l’animation après son démarrage. Contrairement <xref:System.Windows.Media.Animation.Storyboard> à une animation, une animation locale peut animer <xref:System.Windows.FrameworkElement> un <xref:System.Windows.FrameworkContentElement>objet qui n’est pas associé à un ou un . Vous n’avez pas non <xref:System.Windows.NameScope> plus à définir un pour ce type d’animation.  
  
 Les animations locales peuvent uniquement être utilisées dans le code et ne peuvent pas être définies dans des styles, modèles de contrôle ou modèles de données. Une animation locale ne peut pas être contrôlée de façon interactive après son démarrage.  
  
 Pour animer à l’aide d’une animation locale, procédez comme suit.  
  
1. Créez <xref:System.Windows.Media.Animation.AnimationTimeline> un objet.  
  
2. Utilisez <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> la méthode de l’objet que vous <xref:System.Windows.Media.Animation.AnimationTimeline> souhaitez animer pour appliquer la propriété que vous spécifiez.  
  
 L’exemple suivant montre comment animer la largeur <xref:System.Windows.Controls.Button>et la couleur de fond d’un .  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animation horloge  
 Utilisez <xref:System.Windows.Media.MediaPlayer.Clock%2A> des objets lorsque vous souhaitez <xref:System.Windows.Media.Animation.Storyboard> animer sans utiliser un et vous voulez créer des arbres de chronométrage complexes ou contrôler interactivement les animations après leur démarrage. Vous pouvez utiliser des objets Horloge pour <xref:System.Windows.Media.Animation.Animatable> animer une propriété de dépendance de n’importe quel objet.  
  
 Vous ne <xref:System.Windows.Media.Animation.Clock> pouvez pas utiliser des objets directement pour animer dans les styles, les modèles de contrôle ou les modèles de données. (Le système d’animation <xref:System.Windows.Media.Animation.Clock> et de synchronisation utilise en fait des objets pour animer dans <xref:System.Windows.Media.Animation.Clock> les styles, <xref:System.Windows.Media.Animation.Storyboard>les modèles de contrôle et les modèles de données, mais il doit créer ces objets pour vous à partir d’un . Pour plus d’informations <xref:System.Windows.Media.Animation.Storyboard> sur <xref:System.Windows.Media.Animation.Clock> la relation entre les objets et les objets, voir [l’aperçu du système d’animation et de synchronisation](animation-and-timing-system-overview.md).)  
  
 Pour appliquer <xref:System.Windows.Media.Animation.Clock> un single à une propriété, vous remplissez les étapes suivantes.  
  
1. Créez <xref:System.Windows.Media.Animation.AnimationTimeline> un objet.  
  
2. Utilisez <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> la méthode <xref:System.Windows.Media.Animation.AnimationTimeline> de <xref:System.Windows.Media.Animation.AnimationClock>la pour créer un .  
  
3. Utilisez <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> la méthode de l’objet que vous <xref:System.Windows.Media.Animation.AnimationClock> souhaitez animer pour appliquer la propriété que vous spécifiez.  
  
 L’exemple suivant montre <xref:System.Windows.Media.Animation.AnimationClock> comment créer un et l’appliquer à deux propriétés similaires.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Pour créer une arborescence de minutage et l’utiliser pour animer des propriétés, effectuez les étapes suivantes.  
  
1. Utiliser <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Media.Animation.AnimationTimeline> et des objets pour créer l’arbre de chronométrage.  
  
2. Utilisez <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> la racine <xref:System.Windows.Media.Animation.ParallelTimeline> pour <xref:System.Windows.Media.Animation.ClockGroup>créer un .  
  
3. Itérer à <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> travers <xref:System.Windows.Media.Animation.ClockGroup> le de <xref:System.Windows.Media.Animation.Clock> la et appliquer ses objets enfant. Pour <xref:System.Windows.Media.Animation.AnimationClock> chaque enfant, <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> utilisez la méthode de l’objet que <xref:System.Windows.Media.Animation.AnimationClock> vous souhaitez animer pour appliquer la propriété que vous spécifiez  
  
 Pour plus d’informations sur les objets Clock, consultez [Vue d’ensemble de l’animation et du système de minutage](animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animation par image : ignorer le système d’animation et de minutage  
 Utilisez cette approche lorsque vous devez ignorer entièrement le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Un scénario pour cette approche est l’animation physique, où pour chaque étape de l’animation les objets doivent être traités une nouvelle fois en fonction du dernier jeu d’interactions d’objet.  
  
 Les animations par image ne peuvent pas être définies dans des styles, modèles de contrôle ou modèles de données.  
  
 Pour animer image par image, vous <xref:System.Windows.Media.CompositionTarget.Rendering> vous inscrivez à l’événement de l’objet qui contient les objets que vous souhaitez animer. Cette méthode de gestionnaire d’événements est appelée une fois par frame. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur l’arborescence de composition, votre méthode de gestionnaire d’événements est appelée.  
  
 Dans votre gestionnaire d’événements, effectuez les calculs nécessaires pour votre effet d’animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir le temps de présentation <xref:System.EventArgs> pour le cadre actuel, l’associé à cet événement peut être moulé comme <xref:System.Windows.Media.RenderingEventArgs>, qui fournissent une <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> propriété que vous pouvez utiliser pour obtenir le temps de rendu du cadre actuel.  
  
 Pour plus d’informations, consultez la <xref:System.Windows.Media.CompositionTarget.Rendering> page.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des plans conceptuels](storyboards-overview.md)
- [Vue d’ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Aperçu des propriétés de dépendance](../advanced/dependency-properties-overview.md)
