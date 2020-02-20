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
ms.openlocfilehash: 5a9ca51b87f73a24b90d0bd843ee306f8a1b970a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453089"
---
# <a name="custom-animations-overview"></a>Vue d'ensemble des animations personnalisées
Cette rubrique décrit comment et quand étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en créant des images clés personnalisées et des classes d’animation, ou à l’aide du rappel image par image pour l’ignorer.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez connaître les différents types d’animations offerts par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez la Vue d’ensemble des animations From/To/By, la [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md) et la [Vue d'ensemble des animations de tracés](path-animations-overview.md).  
  
 Étant donné que les classes d’animation héritent de la classe <xref:System.Windows.Freezable>, vous devez être familiarisé avec les objets <xref:System.Windows.Freezable> et savoir comment hériter de <xref:System.Windows.Freezable>. Pour plus d’informations, consultez la [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Extension du système d’animation  
 Il existe plusieurs façons d’étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en fonction du niveau de fonctionnalités intégrées que vous souhaitez utiliser.  Il existe trois points d’extensibilité principaux dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
- Créez un objet d’image clé personnalisé en héritant de l’un des *types de\<>* les classes d’images clés, telles que <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Cette approche utilise la plupart des fonctionnalités intégrées dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Créez votre propre classe d’animation en héritant de <xref:System.Windows.Media.Animation.AnimationTimeline> ou de l’une des classes *\<>* AnimationBase.  
  
- Utilisez le rappel image par image pour générer des animations image par image. Cette approche ignore entièrement l’animation et le système de minutage.  
  
 Le tableau suivant décrit certains scénarios permettant d’étendre le système d’animation.  
  
|Si vous souhaitez...|Utiliser cette approche|  
|-------------------------|-----------------------|  
|Personnalisez l’interpolation entre les valeurs d’un type qui possède un *\<Type >* AnimationUsingKeyFrames correspondant|Créez une image clé personnalisée. Pour plus d’informations, consultez la section [Création d’une image clé personnalisée](#createacustomkeyframe).|  
|Personnalisez plus que l’interpolation entre les valeurs d’un type qui possède un *\<Type >* Animation correspondant.|Créez une classe d’animation personnalisée qui hérite de la classe *\<Type >* AnimationBase qui correspond au type que vous souhaitez animer. Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animation d’un type qui ne possède aucune animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante|Utilisez un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> ou créez une classe qui hérite de <xref:System.Windows.Media.Animation.AnimationTimeline>. Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animer plusieurs objets avec des valeurs calculées à chaque frame et basées sur le dernier jeu d’interactions avec les objets|Utilisez un rappel image par image. Pour plus d’informations, consultez la section [Création d’un rappel image par image](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Création d’une image clé personnalisée  
 La création d’une classe d’image clé personnalisée est la façon la plus simple d’étendre le système d’animation. Utilisez cette approche lorsque vous souhaitez une autre méthode d’interpolation pour une animation d’image clé.  Comme décrit dans la [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md), une animation d’image clé utilise des objets d’images clés pour générer ses valeurs de sortie. Chaque objet d’image clé remplit trois fonctions :  
  
- Spécifie une valeur cible à l’aide de sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
- Spécifie l’heure à laquelle cette valeur doit être atteinte à l’aide de sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
- Interpole entre la valeur de l’image clé précédente et sa propre valeur en implémentant la méthode InterpolateValueCore.  
  
 **Instructions d’implémentation**  
  
 Dérivez à partir de la classe abstraite *\<Type >* KeyFrame et implémentez la méthode InterpolateValueCore. La méthode InterpolateValueCore retourne la valeur actuelle de l’image clé. Elle accepte deux paramètres : la valeur de l’image clé précédente et une valeur de progression comprise entre 0 et 1. Une progression de 0 indique que l’image clé vient de démarrer, et la valeur 1 indique que l’image clé vient d’être terminée et doit retourner la valeur spécifiée par sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
 Étant donné que le *type de\<>* classes KeyFrame héritent de la classe <xref:System.Windows.Freezable>, vous devez également substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core pour retourner une nouvelle instance de votre classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Une fois que vous avez créé votre propre animation *\<Type >* KeyFrame, vous pouvez l’utiliser avec *\<Type >* AnimationUsingKeyFrames pour ce type.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Création d’une classe d’animation personnalisée  
 La création de votre propre type d’animation vous donne plus de contrôle sur la façon dont objet est animé. Il existe deux méthodes recommandées pour créer votre propre type d’animation : vous pouvez dériver de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> ou du *type\<>* classe AnimationBase. La dérivation à partir des classes *\<Type >* Animation ou *\<Type >* AnimationUsingKeyFrames n’est pas recommandée.  
  
### <a name="derive-from-typeanimationbase"></a>Dérivation à partir de \<Type > AnimationBase  
 La dérivation d’une classe *\<Type >* AnimationBase est la méthode la plus simple pour créer un nouveau type d’animation. Utilisez cette approche lorsque vous souhaitez créer une nouvelle animation pour un type qui a déjà une classe *\<Type >* AnimationBase correspondante.  
  
 **Instructions d’implémentation**  
  
 Dérivez à partir d’une classe *\<Type >* Animation et implémentez la méthode GetCurrentValueCore. La méthode GetCurrentValueCore retourne la valeur actuelle de l’animation. Il accepte trois paramètres : une valeur de départ suggérée, une valeur de fin suggérée et une <xref:System.Windows.Media.Animation.AnimationClock>, que vous utilisez pour déterminer la progression de l’animation.  
  
 Étant donné que le *Type\<>* les classes AnimationBase héritent de la classe <xref:System.Windows.Freezable>, vous devez également substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core pour retourner une nouvelle instance de votre classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Pour plus d’informations, consultez la documentation sur la méthode GetCurrentValueCore pour la classe *\<Type >* AnimationBase du type que vous souhaitez animer. Pour obtenir un exemple, consultez [Exemple d’animation personnalisée](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Autres approches**  
  
 Si vous souhaitez simplement modifier la façon dont les valeurs d’animation sont interpolées, envisagez de dériver une des classes *\<Type >* KeyFrame. L’image clé que vous créez est utilisable par les *\<Type >* AnimationUsingKeyFrames correspondants fournis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Dérivation à partir de AnimationTimeline  
 Dérivez de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> lorsque vous souhaitez créer une animation pour un type qui n’a pas déjà une animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante, ou si vous souhaitez créer une animation qui n’est pas fortement typée.  
  
 **Instructions d’implémentation**  
  
 Dérivez de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> et substituez les membres suivants :  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> : Si votre nouvelle classe est concrète, vous devez substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de votre classe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> : substituez cette méthode pour retourner la valeur actuelle de votre animation. Il accepte trois paramètres : une valeur d’origine par défaut, une valeur de destination par défaut et une <xref:System.Windows.Media.Animation.AnimationClock>. Utilisez la <xref:System.Windows.Media.Animation.AnimationClock> pour obtenir l’heure actuelle ou la progression de l’animation. Vous pouvez choisir d’utiliser les valeurs d’origine et de destination par défaut.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> : remplacez cette propriété pour indiquer si votre animation utilise la valeur de destination par défaut spécifiée par la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> : remplacez cette propriété pour indiquer le <xref:System.Type> de sortie produit par votre animation.  
  
 Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Le paradigme recommandé (utilisé par les animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) consiste à utiliser deux niveaux d’héritage :  
  
1. Créez un *type de\<abstrait >* classe AnimationBase qui dérive de <xref:System.Windows.Media.Animation.AnimationTimeline>. Cette classe doit substituer la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>. Elle doit également introduire une nouvelle méthode abstraite, GetCurrentValueCore et substituer <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> afin de valider les types de la valeur d’origine par défaut et des paramètres de la valeur de destination par défaut, puis appelle GetCurrentValueCore.  
  
2. Créez une autre classe qui hérite de votre nouveau *type de\<>* classe AnimationBase et substitue la méthode <xref:System.Windows.Freezable.CreateInstanceCore%2A>, la méthode GetCurrentValueCore que vous avez introduite et la propriété <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>.  
  
 **Autres approches**  
  
 Si vous souhaitez animer un type qui n’a pas d’animation from/to/by et d’animation d’image clé correspondantes, envisagez d’utiliser un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Étant donné qu’il est faiblement typé, un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> peut animer n’importe quel type de valeur. L’inconvénient de cette approche est que <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> prend en charge uniquement l’interpolation discrète.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Rappel image par image  
 Utilisez cette approche lorsque vous devez ignorer entièrement le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Un scénario pour cette approche est l’animation physique, où pour chaque étape animation une nouvelle direction ou position doit être recalculée pour les objets animés en fonction du dernier jeu d’interactions avec les objets.  
  
 **Instructions d’implémentation**  
  
 Contrairement aux autres approches décrites dans cette vue d’ensemble, le rappel image par image ne nécessite pas de créer une animation personnalisée ou une classe d’image clé.  
  
 Au lieu de cela, vous vous inscrivez pour l’événement <xref:System.Windows.Media.CompositionTarget.Rendering> de l’objet qui contient les objets que vous souhaitez animer. Cette méthode de gestionnaire d’événements est appelée une fois par image. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur l’arborescence de composition, votre méthode de gestionnaire d’événements est appelée.  
  
 Dans votre gestionnaire d’événements, effectuez les calculs nécessaires pour votre effet d’animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir l’heure de présentation de l’image actuelle, les <xref:System.EventArgs> associées à cet événement peuvent être converties en <xref:System.Windows.Media.RenderingEventArgs>, qui fournissent une propriété <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> que vous pouvez utiliser pour obtenir le temps de rendu de l’image actuelle.  
  
 Pour plus d’informations, consultez la page <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Vue d'ensemble des techniques d'animation de propriétés](property-animation-techniques-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble des animations de tracés](path-animations-overview.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Exemple d’animation personnalisée](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
