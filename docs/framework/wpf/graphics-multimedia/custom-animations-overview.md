---
title: Vue d'ensemble des animations personnalisées
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186549"
---
# <a name="custom-animations-overview"></a>Vue d'ensemble des animations personnalisées
Cette rubrique décrit comment et quand étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en créant des images clés personnalisées et des classes d’animation, ou à l’aide du rappel image par image pour l’ignorer.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez connaître les différents types d’animations offerts par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez la Vue d’ensemble des animations From/To/By, la [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md) et la [Vue d'ensemble des animations de tracés](path-animations-overview.md).  
  
 Parce que les classes <xref:System.Windows.Freezable> d’animation héritent de la classe, vous devriez être familier avec <xref:System.Windows.Freezable> les objets et comment hériter de <xref:System.Windows.Freezable>. Pour plus d’informations, consultez la [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>Extension du système d’animation  
 Il existe plusieurs façons d’étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en fonction du niveau de fonctionnalités intégrées que vous souhaitez utiliser.  Il existe trois points d’extensibilité principaux dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
- Créez un objet cadre à clé personnalisé * \< *en héritant de l’une <xref:System.Windows.Media.Animation.DoubleKeyFrame>des classes Type>KeyFrame, telles que . Cette approche utilise la plupart des fonctionnalités intégrées dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Créez votre propre classe d’animation en héritant de ou de <xref:System.Windows.Media.Animation.AnimationTimeline> l’un * \< *des cours Type>AnimationBase.  
  
- Utilisez le rappel image par image pour générer des animations image par image. Cette approche ignore entièrement l’animation et le système de minutage.  
  
 Le tableau suivant décrit certains scénarios permettant d’étendre le système d’animation.  
  
|Si vous souhaitez...|Utiliser cette approche|  
|-------------------------|-----------------------|  
|Personnaliser l’interpolation entre les valeurs d’un type qui a un * \<type *correspondant>AnimationUsingKeyFrames|Créez une image clé personnalisée. Pour plus d’informations, consultez la section [Création d’une image clé personnalisée](#createacustomkeyframe).|  
|Personnalisez plus que l’interpolation entre les valeurs d’un type qui a un * \<type *correspondant>Animation.|Créez un cours d’animation * \< *personnalisé qui hérite de la classe Type>AnimationBase qui correspond au type que vous souhaitez animer. Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animation d’un type qui ne possède aucune animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante|Utilisez <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> un ou créez une <xref:System.Windows.Media.Animation.AnimationTimeline>classe qui hérite de . Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animer plusieurs objets avec des valeurs calculées à chaque frame et basées sur le dernier jeu d’interactions avec les objets|Utilisez un rappel image par image. Pour plus d’informations, consultez la section [Création d’un rappel image par image](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>Création d’une image clé personnalisée  
 La création d’une classe d’image clé personnalisée est la façon la plus simple d’étendre le système d’animation. Utilisez cette approche lorsque vous souhaitez une autre méthode d’interpolation pour une animation d’image clé.  Comme décrit dans la [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md), une animation d’image clé utilise des objets d’images clés pour générer ses valeurs de sortie. Chaque objet d’image clé remplit trois fonctions :  
  
- Spécifie une <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> valeur cible à l’aide de sa propriété.  
  
- Précise l’heure à laquelle cette valeur <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> doit être atteinte à l’aide de sa propriété.  
  
- Interpole entre la valeur de l’image clé précédente et sa propre valeur en implémentant la méthode InterpolateValueCore.  
  
 **Instructions d’implémentation**  
  
 Dérivez * \< *de la classe abstraite Type>KeyFrame et implémenter la méthode InterpolateValueCore. La méthode InterpolateValueCore retourne la valeur actuelle de l’image clé. Elle accepte deux paramètres : la valeur de l’image clé précédente et une valeur de progression comprise entre 0 et 1. Un progrès de 0 indique que le cadre clé vient de commencer, et une valeur de 1 indique que le cadre clé vient de terminer et devrait retourner la valeur spécifiée par sa <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriété.  
  
 Étant * \< *donné que les classes Type><xref:System.Windows.Freezable> KeyFrame héritent de la classe, vous devez également remplacer <xref:System.Windows.Freezable.CreateInstanceCore%2A> le noyau pour retourner une nouvelle instance de votre classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Après avoir créé votre animation * \<Type>* KeyFrame personnalisée, vous * \< *pouvez l’utiliser avec le Type>AnimationUsingKeyFrames pour ce type.  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>Création d’une classe d’animation personnalisée  
 La création de votre propre type d’animation vous donne plus de contrôle sur la façon dont objet est animé. Il existe deux façons recommandées de créer votre <xref:System.Windows.Media.Animation.AnimationTimeline> propre type d’animation : vous pouvez tirer de la classe ou de la * \< *classe Type>AnimationBase. Il n’est pas recommandé de déduire des cours * \<Type>* Animation ou * \<Type>* AnimationUsingKeyFrames.  
  
### <a name="derive-from-typeanimationbase"></a>Dérivation à partir de \<Type > AnimationBase  
 La sortie d’une * \< *classe Type>AnimationBase est le moyen le plus simple de créer un nouveau type d’animation. Utilisez cette approche lorsque vous souhaitez créer une nouvelle animation pour le type qui dispose déjà d’une classe * \<type>* AnimationBase correspondante.  
  
 **Instructions d’implémentation**  
  
 Dérivez * \< *d’une classe d’animation Type>et implémentez la méthode GetCurrentValueCore. La méthode GetCurrentValueCore retourne la valeur actuelle de l’animation. Il faut trois paramètres: une valeur de départ suggérée, une valeur de fin suggérée, et un <xref:System.Windows.Media.Animation.AnimationClock>, que vous utilisez pour déterminer l’évolution de l’animation.  
  
 Étant * \< *donné que les classes Type><xref:System.Windows.Freezable> AnimationBase héritent <xref:System.Windows.Freezable.CreateInstanceCore%2A> de la classe, vous devez également remplacer le noyau pour retourner une nouvelle instance de votre classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Pour plus d’informations, consultez la documentation de * \< *la méthode GetCurrentValueCore pour la classe Type>AnimationBase pour le type que vous souhaitez animer. Pour obtenir un exemple, consultez [Exemple d’animation personnalisée](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Approches alternatives**  
  
 Si vous voulez simplement changer la façon dont les valeurs d’animation sont interpolées, envisagez de provenmer de l’une * \< *des classes Type>KeyFrame. Le cadre clé que vous créez peut être utilisé avec le * \<type * [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]correspondant>AnimationUsingKeyFrames fourni par .  
  
### <a name="derive-from-animationtimeline"></a>Dérivation à partir de AnimationTimeline  
 Dérivez <xref:System.Windows.Media.Animation.AnimationTimeline> de la classe lorsque vous voulez créer une animation pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un type qui n’a pas déjà une animation correspondant, ou vous voulez créer une animation qui n’est pas fortement tapé.  
  
 **Instructions d’implémentation**  
  
 Dérivez <xref:System.Windows.Media.Animation.AnimationTimeline> de la classe et remplacez les membres suivants :  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>Si votre nouvelle classe est concrète, <xref:System.Windows.Freezable.CreateInstanceCore%2A> vous devez passer outre pour retourner une nouvelle instance de votre classe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>Remplacer cette méthode pour retourner la valeur actuelle de votre animation. Il faut trois paramètres : une valeur d’origine <xref:System.Windows.Media.Animation.AnimationClock>par défaut, une valeur de destination par défaut et une . Utilisez <xref:System.Windows.Media.Animation.AnimationClock> le pour obtenir l’heure actuelle ou les progrès pour l’animation. Vous pouvez choisir d’utiliser les valeurs d’origine et de destination par défaut.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>- Remplacer cette propriété pour indiquer si votre animation <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> utilise la valeur de destination par défaut spécifiée par la méthode.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>- Remplacer cette propriété <xref:System.Type> pour indiquer la sortie de votre animation produit.  
  
 Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Le paradigme recommandé (utilisé par les animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) consiste à utiliser deux niveaux d’héritage :  
  
1. Créez une classe * \<abstraite Type>* AnimationBase <xref:System.Windows.Media.Animation.AnimationTimeline>qui dérive de . Cette classe devrait <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> passer outre à la méthode. Il devrait également introduire une nouvelle méthode abstraite, GetCurrentValueCore, et passer outre <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> afin qu’il valide les types de la valeur d’origine par défaut et les paramètres de valeur de destination par défaut, puis appelle GetCurrentValueCore.  
  
2. Créez une autre classe qui * \< *hérite de votre nouveau type><xref:System.Windows.Freezable.CreateInstanceCore%2A> classe AnimationBase et remplace la méthode, la <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> méthode GetCurrentValueCore que vous avez introduite et la propriété.  
  
 **Approches alternatives**  
  
 Si vous souhaitez animer un type qui n’a pas d’animation ou d’animation à cadre clé correspondant, envisagez d’utiliser un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Parce qu’il est faiblement dactylographié, un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> peut animer n’importe quel type de valeur. L’inconvénient de cette <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> approche est que ne prend en charge que l’interpolation discrète.  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>Rappel image par image  
 Utilisez cette approche lorsque vous devez ignorer entièrement le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Un scénario pour cette approche est l’animation physique, où pour chaque étape animation une nouvelle direction ou position doit être recalculée pour les objets animés en fonction du dernier jeu d’interactions avec les objets.  
  
 **Instructions d’implémentation**  
  
 Contrairement aux autres approches décrites dans cette vue d’ensemble, le rappel image par image ne nécessite pas de créer une animation personnalisée ou une classe d’image clé.  
  
 Au lieu de <xref:System.Windows.Media.CompositionTarget.Rendering> cela, vous vous inscrivez pour l’événement de l’objet qui contient les objets que vous souhaitez animer. Cette méthode de gestionnaire d’événements est appelée une fois par frame. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur l’arborescence de composition, votre méthode de gestionnaire d’événements est appelée.  
  
 Dans votre gestionnaire d’événements, effectuez les calculs nécessaires pour votre effet d’animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir le temps de présentation <xref:System.EventArgs> du cadre actuel, <xref:System.Windows.Media.RenderingEventArgs>l’associé <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> à cet événement peut être moulé comme , qui fournissent une propriété que vous pouvez utiliser pour obtenir le temps de rendu du cadre actuel.  
  
 Pour plus d’informations, consultez la <xref:System.Windows.Media.CompositionTarget.Rendering> page.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Vue d'ensemble des techniques d'animation de propriétés](property-animation-techniques-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble des animations de tracés](path-animations-overview.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Exemple d’animation personnalisée](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
