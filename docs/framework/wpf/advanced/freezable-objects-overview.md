---
title: Vue d'ensemble des objets Freezable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: b2ef3c3dbbfbcef08f58c47948f76cb2c238b48a
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238529"
---
# <a name="freezable-objects-overview"></a>Vue d'ensemble des objets Freezable
Cette rubrique explique comment utiliser efficacement et créer <xref:System.Windows.Freezable> objets, qui offrent des fonctionnalités spéciales qui peuvent aider à améliorer les performances de l’application. Pinceaux, les stylets, les transformations, les géométries et les animations sont des exemples d’objets freezable.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Qu’est un élément Freezable ?  
 Un <xref:System.Windows.Freezable> est un type spécial d’objet qui a deux états : figé et non figé. Lors de la non figé, un <xref:System.Windows.Freezable> semble se comporter comme tout autre objet. Quand il est figé, un <xref:System.Windows.Freezable> ne peut plus être modifié.  
  
 Un <xref:System.Windows.Freezable> fournit un <xref:System.Windows.Freezable.Changed> événement d’informer les observateurs de toute modification apportée à l’objet. Figer un <xref:System.Windows.Freezable> peut améliorer ses performances, car il n’a plus besoin de consacrer des notifications de modification de ressources. Figé <xref:System.Windows.Freezable> peut également être partagé entre plusieurs threads, un non figées <xref:System.Windows.Freezable> ne peut pas.  
  
 Bien que le <xref:System.Windows.Freezable> classe possède de nombreuses applications, plus <xref:System.Windows.Freezable> dans des objets [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont liés au sous-système graphique.  
  
 Le <xref:System.Windows.Freezable> classe rend plus facile à utiliser certains objets du système graphique et peut améliorer les performances de l’application. Exemples de types qui héritent de <xref:System.Windows.Freezable> incluent le <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, et <xref:System.Windows.Media.Geometry> classes. Parce qu’elles contiennent des ressources non managées, le système doit surveiller ces objets pour les modifications, puis mettez à jour leurs ressources non managées correspondants lorsqu’il existe une modification apportée à l’objet d’origine. Même si vous ne modifiez en fait un objet de système de graphismes, le système doit toujours consacrer une partie de ses ressources de surveillance de l’objet, au cas où vous la modifiez.  
  
 Par exemple, supposons que vous créez un <xref:System.Windows.Media.SolidColorBrush> brush et l’utiliser pour peindre l’arrière-plan d’un bouton.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Lorsque le bouton est affiché, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sous-système graphique utilise les informations fournies pour peindre un groupe de pixels utilisés pour créer l’apparence d’un bouton. Bien que vous avez utilisé un pinceau de couleur unie pour décrire comment le bouton doit être peint, votre pinceau de couleur unie n’effectue pas elle-même la peinture. Le système graphique génère des objets rapides de bas niveau pour le bouton et le pinceau, et ce sont ces objets qui apparaissent réellement sur l’écran.  
  
 Si vous deviez modifier le pinceau, ces objets de bas niveau devrait être régénérée. La classe freezable est ce qui permet un pinceau pour rechercher ses objets correspondants générés de bas niveau et les mettre à jour quand il change. Lorsque cette fonctionnalité est activée, le pinceau est dit « non figé ».  
  
 Un freezable <xref:System.Windows.Freezable.Freeze%2A> méthode vous permet de désactiver cette possibilité de mise à jour automatique. Vous pouvez utiliser cette méthode pour rendre le pinceau « figée », ou non modifiable.  
  
> [!NOTE]
>  Tous les objets Freezable peuvent être figée. Pour éviter de lever une <xref:System.InvalidOperationException>, vérifiez la valeur de l’objet Freezable <xref:System.Windows.Freezable.CanFreeze%2A> propriété afin de déterminer s’il peut être figé avant d’essayer de le figer.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Lorsque vous n’avez plus besoin de modifier un élément freezable, Figer offre des avantages de performances. Si vous deviez figer le pinceau dans cet exemple, le système graphique serait n’avez plus besoin de le surveiller les modifications. Le système graphique peut également effectuer d’autres optimisations, car il sait que le pinceau ne changera pas.  
  
> [!NOTE]
>  Pour des raisons pratiques, des objets freezable restent non figées, sauf si vous les figer explicitement.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>À l’aide des objets Freezable  
 À l’aide d’une non figées freezable ressemble à l’aide de n’importe quel autre type d’objet. Dans l’exemple suivant, la couleur d’un <xref:System.Windows.Media.SolidColorBrush> est modifié du jaune au rouge après qu’il est utilisé pour peindre l’arrière-plan d’un bouton. Le système graphique fonctionne en arrière-plan pour modifier automatiquement le bouton du jaune au rouge la prochaine qu'actualisation de l’écran.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Figer un Freezable  
 Pour rendre un <xref:System.Windows.Freezable> non modifiable, vous appelez son <xref:System.Windows.Freezable.Freeze%2A> (méthode). Lorsque vous gelez un objet qui contient des objets freezable, ces objets sont aussi figées. Par exemple, si vous gelez un <xref:System.Windows.Media.PathGeometry>, les chiffres et les segments qu’il contient seraient également figés.  
  
 Un Freezable **ne peut pas** être figé si une des opérations suivantes est vraie :  
  
- Il a animé ou propriétés liées aux données.  
  
- Il possède des propriétés définies par une ressource dynamique. (Consultez le [XAML ressources](xaml-resources.md) pour plus d’informations sur les ressources dynamiques.)  
  
- Il contient <xref:System.Windows.Freezable> sous-objets qui ne peut pas être figés.  
  
 Si ces conditions ont la valeur false et que vous ne souhaitez pas modifier le <xref:System.Windows.Freezable>, puis vous devez figer afin de bénéficier des avantages de performances décrits précédemment.  
  
 Une fois que vous appelez un freezable <xref:System.Windows.Freezable.Freeze%2A> (méthode), il ne peut plus être modifié. Tente de modifier un objet figé objet entraîne une <xref:System.InvalidOperationException> levée. Le code suivant lève une exception, étant donné que nous tentons de modifier le pinceau une fois qu’il a été figé.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Pour éviter de lever cette exception, vous pouvez utiliser la <xref:System.Windows.Freezable.IsFrozen%2A> méthode pour déterminer si un <xref:System.Windows.Freezable> est figée.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Dans l’exemple de code précédent, une copie modifiable a été effectuée d’un objet figé en utilisant le <xref:System.Windows.Freezable.Clone%2A> (méthode). La section suivante présente le clonage plus en détail.  
  
 **Remarque** car figé freezable ne peut pas être animé, le système d’animation créera automatiquement des clones modifiables de figé <xref:System.Windows.Freezable> objets lorsque vous essayez de les animer avec un <xref:System.Windows.Media.Animation.Storyboard>. Pour éliminer la surcharge de performance liée par le clonage, laissez un objet non figé si vous souhaitez animer. Pour plus d’informations sur l’animation avec des storyboards, consultez le [vue d’ensemble des Storyboards](../graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Gel à partir du balisage  
 Pour figer un <xref:System.Windows.Freezable> objet déclaré dans le balisage, vous utilisez le `PresentationOptions:Freeze` attribut. Dans l’exemple suivant, un <xref:System.Windows.Media.SolidColorBrush> est déclaré comme une ressource de page et figé. Il est ensuite utilisé pour définir l’arrière-plan d’un bouton.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Pour utiliser le `Freeze` attribut, vous devez mapper l’espace de noms d’options de présentation : `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` est le préfixe recommandé pour le mappage de cet espace de noms :  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Étant donné que tous les lecteurs XAML reconnaissent cet attribut, il est recommandé d’utiliser le [mc : Ignorable, attribut](mc-ignorable-attribute.md) pour marquer le `Presentation:Freeze` attribut comme pouvant être ignoré :  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Pour plus d’informations, consultez le [mc : Ignorable, attribut](mc-ignorable-attribute.md) page.  
  
### <a name="unfreezing-a-freezable"></a>« Libération » d’un élément Freezable  
 Une fois figé, un <xref:System.Windows.Freezable> ne peut jamais être modifié ou non figé ; Toutefois, vous pouvez créer un clone non figé à l’aide de la <xref:System.Windows.Freezable.Clone%2A> ou <xref:System.Windows.Freezable.CloneCurrentValue%2A> (méthode).  
  
 Dans l’exemple suivant, l’arrière-plan du bouton est défini avec un pinceau et ce pinceau est figé. Une copie non figée est effectuée du pinceau en utilisant le <xref:System.Windows.Freezable.Clone%2A> (méthode). Le clone est modifié et sert à modifier l’arrière-plan du bouton du jaune au rouge.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Quelle que soit la méthode de clone que vous utilisez, les animations ne sont jamais copiées vers le nouveau <xref:System.Windows.Freezable>.  
  
 Le <xref:System.Windows.Freezable.Clone%2A> et <xref:System.Windows.Freezable.CloneCurrentValue%2A> méthodes produisent des copies complètes de freezable. Si le freezable contient d’autres objets freezable figés, ils sont également clonés et rendus modifiables. Par exemple, si vous clonez un figé <xref:System.Windows.Media.PathGeometry> pour le rendre modifiable, les figures et les segments qu’il contient sont également copiés et rendus modifiables.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Création de votre propre classe Freezable  
 Une classe qui dérive de <xref:System.Windows.Freezable> acquiert les fonctionnalités suivantes.  
  
- États spéciaux : en lecture seule (figé) et un état accessible en écriture.  
  
- Sécurité des threads : figé <xref:System.Windows.Freezable> peut être partagé entre plusieurs threads.  
  
- Notification de modifications détaillée : Contrairement à d’autres <xref:System.Windows.DependencyObject>s, des objets Freezable fournissent des notifications de modifications lorsque les valeurs de sous-propriété changent.  
  
- Le clonage facile : la classe Freezable a déjà implémenté plusieurs méthodes qui génèrent des clones complets.  
  
 Un <xref:System.Windows.Freezable> est un type de <xref:System.Windows.DependencyObject>et par conséquent utilise le système de propriétés de dépendance. Propriétés de votre classe n’êtes pas obligé d’être des propriétés de dépendance, mais l’utilisation des propriétés de dépendance réduit la quantité de code que vous avez à écrire, car la <xref:System.Windows.Freezable> classe a été conçue avec les propriétés de dépendance à l’esprit. Pour plus d’informations sur le système de propriétés de dépendance, consultez le [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
 Chaque <xref:System.Windows.Freezable> sous-classe doit remplacer le <xref:System.Windows.Freezable.CreateInstanceCore%2A> (méthode). Si votre classe utilise les propriétés de dépendance pour toutes ses données, vous avez terminé.  
  
 Si votre classe contient des membres de données de propriétés de non dépendance, vous devez également substituer les méthodes suivantes :  
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Vous devez également respecter les règles suivantes pour l’accès et en écriture aux membres de données qui ne sont pas des propriétés de dépendance :  
  
- Au début de toute API qui lit les données membres de propriétés de non dépendance, appelez le <xref:System.Windows.Freezable.ReadPreamble%2A> (méthode).  
  
- Au début de toute API qui écrit des données membres de propriétés de non dépendance, appelez le <xref:System.Windows.Freezable.WritePreamble%2A> (méthode). (Une fois que vous avez appelé <xref:System.Windows.Freezable.WritePreamble%2A> dans une API, vous n’avez pas besoin effectuer un appel supplémentaire à <xref:System.Windows.Freezable.ReadPreamble%2A> si vous lisez également les membres de données de propriété de dépendance non.)  
  
- Appelez le <xref:System.Windows.Freezable.WritePostscript%2A> méthode avant de quitter les méthodes qui écrivent dans les membres de données de propriété de dépendance non.  
  
 Si votre classe contient des membres de données de la propriété de dépendance qui sont <xref:System.Windows.DependencyObject> objets, vous devez également appeler le <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> méthode chaque fois que vous modifiez l’une de leurs valeurs, même si vous définissez le membre aux `null`.  
  
> [!NOTE]
>  Il est très important de commencer chaque <xref:System.Windows.Freezable> méthode que vous substituez avec un appel à l’implémentation de base.  
  
 Pour obtenir un exemple de personnalisé <xref:System.Windows.Freezable> de classe, consultez le [Animation personnalisée, exemple](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Freezable>
- [Exemple d’animation personnalisée](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
