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
ms.openlocfilehash: 854565e28e646ef57658e2bfdb7326d8453448d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856072"
---
# <a name="freezable-objects-overview"></a>Vue d'ensemble des objets Freezable

Cette rubrique explique comment utiliser et créer <xref:System.Windows.Freezable> efficacement des objets, qui fournissent des fonctionnalités spéciales qui peuvent aider à améliorer les performances de l’application. Les pinceaux, les stylets, les transformations, les géométries et les animations sont des exemples d’objets Freezable.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>Qu’est-ce qu’un Freezable ?

Un <xref:System.Windows.Freezable> est un type spécial d’objet qui a deux États: non figé et figé. Lorsqu’il est non figé <xref:System.Windows.Freezable> , un semble se comporter comme n’importe quel autre objet. Lorsqu’il est figé <xref:System.Windows.Freezable> , un ne peut plus être modifié.

Un <xref:System.Windows.Freezable> fournit un <xref:System.Windows.Freezable.Changed> événement pour notifier aux observateurs toute modification apportée à l’objet. Le gel <xref:System.Windows.Freezable> d’un peut améliorer ses performances, car il n’a plus besoin de consacrer des ressources aux notifications de modification. Un figé <xref:System.Windows.Freezable> peut également être partagé entre les threads, contrairement à <xref:System.Windows.Freezable> un non figé.

Bien que <xref:System.Windows.Freezable> la classe ait de nombreuses applications <xref:System.Windows.Freezable> , la [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] plupart des objets dans sont liés au sous-système Graphics.

La <xref:System.Windows.Freezable> classe facilite l’utilisation de certains objets système graphiques et peut aider à améliorer les performances de l’application. Les <xref:System.Windows.Freezable> classes<xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>et sontdesexemplesdetypesquihéritentde.<xref:System.Windows.Media.Geometry> Étant donné qu’ils contiennent des ressources non managées, le système doit surveiller ces objets pour y apporter des modifications, puis mettre à jour leurs ressources non managées correspondantes lorsqu’une modification est apportée à l’objet d’origine. Même si vous ne modifiez pas réellement un objet système Graphics, le système doit toujours consacrer certaines de ses ressources à la surveillance de l’objet, au cas où vous le modifieriez.

Par exemple, supposons que vous <xref:System.Windows.Media.SolidColorBrush> créez un pinceau et que vous l’utilisiez pour peindre l’arrière-plan d’un bouton.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Lorsque le bouton est rendu, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sous-système Graphics utilise les informations que vous avez fournies pour peindre un groupe de pixels afin de créer l’apparence d’un bouton. Bien que vous ayez utilisé un pinceau de couleur unie pour décrire comment le bouton doit être peint, votre pinceau de couleur unie ne fait pas réellement la peinture. Le système graphique génère des objets rapides et de bas niveau pour le bouton et le pinceau, et il s’agit des objets qui s’affichent réellement à l’écran.

Si vous deviez modifier le pinceau, ces objets de bas niveau doivent être régénérés. La classe Freezable permet à un pinceau de trouver ses objets de bas niveau et générés correspondants, et de les mettre à jour lorsqu’il change. Lorsque cette fonctionnalité est activée, le pinceau est dit « non figé ».

La méthode d' <xref:System.Windows.Freezable.Freeze%2A> un Freezable vous permet de désactiver cette fonctionnalité de mise à jour automatique. Vous pouvez utiliser cette méthode pour que le pinceau devienne « figé » ou non modifiable.

> [!NOTE]
> Tous les objets Freezable ne peuvent pas être figés. Pour éviter de lever <xref:System.InvalidOperationException>une exception, vérifiez la valeur de la <xref:System.Windows.Freezable.CanFreeze%2A> propriété de l’objet Freezable pour déterminer si elle peut être figée avant d’essayer de la geler.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Lorsque vous n’avez plus besoin de modifier un Freezable, le gel offre des avantages en matière de performances. Si vous deviez figer le pinceau dans cet exemple, le système graphique n’aurait plus besoin de le surveiller pour les modifications. Le système graphique peut également effectuer d’autres optimisations, car il sait que le pinceau ne changera pas.

> [!NOTE]
> Pour plus de commodité, les objets Freezable restent non figés, sauf si vous les figez explicitement.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Utilisation de Freezables

L’utilisation d’un Freezable non figé est semblable à l’utilisation d’un autre type d’objet. Dans l’exemple suivant, la couleur d’un <xref:System.Windows.Media.SolidColorBrush> est remplacée de jaune par rouge après son utilisation pour peindre l’arrière-plan d’un bouton. Le système graphique fonctionne en arrière-plan pour changer automatiquement le bouton du jaune en rouge lors de la prochaine actualisation de l’écran.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Figer un Freezable

Pour rendre un <xref:System.Windows.Freezable> non modifiable, vous devez appeler <xref:System.Windows.Freezable.Freeze%2A> sa méthode. Quand vous figez un objet qui contient des objets Freezable, ces objets sont également figés. Par exemple, si vous figez <xref:System.Windows.Media.PathGeometry>un, les figures et les segments qu’il contient seraient également figés.

Un Freezable **ne peut pas** être figé si l’une des conditions suivantes est vraie :

- Il a des propriétés animées ou liées aux données.

- Ses propriétés sont définies par une ressource dynamique. (Pour plus d’informations sur les ressources dynamiques, consultez les [ressources XAML](xaml-resources.md) .)

- Il contient <xref:System.Windows.Freezable> des sous-objets qui ne peuvent pas être figés.

Si ces conditions sont fausses et que vous n’envisagez pas <xref:System.Windows.Freezable>de modifier le, vous devez le geler pour bénéficier des avantages en matière de performances décrits précédemment.

Une fois que vous appelez la <xref:System.Windows.Freezable.Freeze%2A> méthode d’un Freezable, elle ne peut plus être modifiée. Toute tentative de modification d’un objet figé <xref:System.InvalidOperationException> entraîne la levée d’une exception. Le code suivant lève une exception, car nous tentons de modifier le pinceau après qu’il a été figé.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Pour éviter de lever cette exception, vous pouvez utiliser <xref:System.Windows.Freezable.IsFrozen%2A> la méthode pour déterminer si <xref:System.Windows.Freezable> un est figé.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

Dans l’exemple de code précédent, une copie modifiable a été effectuée d’un objet figé <xref:System.Windows.Freezable.Clone%2A> à l’aide de la méthode. La section suivante décrit le clonage plus en détail.

> [!NOTE]
> Comme un Freezable figé ne peut pas être animé, le système d’animation crée automatiquement des clones modifiables d’objets figés <xref:System.Windows.Freezable> quand vous essayez de les animer avec un. <xref:System.Windows.Media.Animation.Storyboard> Pour éliminer la surcharge de performances causée par le clonage, laissez un objet non figé si vous envisagez de l’animer. Pour plus d’informations sur l’animation avec les storyboards, consultez [vue d’ensemble des storyboards](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Figer à partir du balisage

Pour figer <xref:System.Windows.Freezable> un objet déclaré dans le balisage, `PresentationOptions:Freeze` vous utilisez l’attribut. Dans l’exemple suivant, un <xref:System.Windows.Media.SolidColorBrush> est déclaré en tant que ressource de page et figé. Elle est ensuite utilisée pour définir l’arrière-plan d’un bouton.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Pour utiliser l' `Freeze` attribut, vous devez mapper à l’espace de noms des `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`options de présentation :. `PresentationOptions`est le préfixe recommandé pour le mappage de cet espace de noms :

```
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Étant donné que tous les lecteurs XAML ne reconnaissent pas cet attribut, il est recommandé d’utiliser l' [attribut MC : Ignorable](mc-ignorable-attribute.md) pour marquer l' `Presentation:Freeze` attribut comme étant pouvant être ignoré :

```
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Pour plus d’informations, consultez la page de l' [attribut MC : Ignorable](mc-ignorable-attribute.md) .

### <a name="unfreezing-a-freezable"></a>« Libération » d’un Freezable

Une fois figé, <xref:System.Windows.Freezable> un ne peut jamais être modifié ou non figé ; Toutefois, vous pouvez créer un clone non <xref:System.Windows.Freezable.Clone%2A> figé <xref:System.Windows.Freezable.CloneCurrentValue%2A> à l’aide de la méthode ou.

Dans l’exemple suivant, l’arrière-plan du bouton est défini avec un pinceau et ce pinceau est alors figé. Une copie non figée est faite du pinceau à l' <xref:System.Windows.Freezable.Clone%2A> aide de la méthode. Le clone est modifié et utilisé pour changer l’arrière-plan du bouton du jaune au rouge.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Quelle que soit la méthode de clonage que vous utilisez, les animations ne <xref:System.Windows.Freezable>sont jamais copiées dans le nouveau.

Les <xref:System.Windows.Freezable.Clone%2A> méthodes <xref:System.Windows.Freezable.CloneCurrentValue%2A> et produisent des copies complètes du Freezable. Si le Freezable contient d’autres objets Freezable figés, ils sont également clonés et rendus modifiables. Par exemple, si vous clonez un <xref:System.Windows.Media.PathGeometry> figé pour le rendre modifiable, les figures et les segments qu’il contient sont également copiés et rendus modifiables.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Création de votre propre classe Freezable

Une classe qui dérive de <xref:System.Windows.Freezable> obtient les fonctionnalités suivantes.

- États spéciaux : un État en lecture seule (figé) et un état accessible en écriture.

- Sécurité des threads : <xref:System.Windows.Freezable> un figé peut être partagé entre les threads.

- Notification de modification détaillée : Contrairement aux <xref:System.Windows.DependencyObject>autres, les objets Freezable fournissent des notifications de modification lorsque les valeurs de sous-propriétés changent.

- Clonage facile : la classe Freezable a déjà implémenté plusieurs méthodes qui produisent des clones profonds.

Un <xref:System.Windows.Freezable> est un type de <xref:System.Windows.DependencyObject>, et par conséquent utilise le système de propriétés de dépendance. Vos propriétés de classe n’ont pas besoin d’être des propriétés de dépendance, mais l’utilisation de propriétés de dépendance réduit la quantité de code <xref:System.Windows.Freezable> que vous devez écrire, car la classe a été conçue avec les propriétés de dépendance à l’esprit. Pour plus d’informations sur le système de propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).

Chaque <xref:System.Windows.Freezable> sous-classe doit se substituer à la <xref:System.Windows.Freezable.CreateInstanceCore%2A> méthode. Si votre classe utilise des propriétés de dépendance pour toutes ses données, vous avez terminé.

Si votre classe contient des membres de données de propriété de non dépendance, vous devez également substituer les méthodes suivantes :

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Vous devez également respecter les règles suivantes pour l’accès et l’écriture aux membres de données qui ne sont pas des propriétés de dépendance :

- Au début de toute API qui lit les données membres de propriété de non dépendance, appelez <xref:System.Windows.Freezable.ReadPreamble%2A> la méthode.

- Au début de toute API qui écrit des membres de données de propriété de non dépendance, <xref:System.Windows.Freezable.WritePreamble%2A> appelez la méthode. (Une fois que vous <xref:System.Windows.Freezable.WritePreamble%2A> avez appelé dans une API, vous n’avez pas besoin d’effectuer <xref:System.Windows.Freezable.ReadPreamble%2A> un appel supplémentaire à si vous lisez également des membres de données de propriété de non dépendance.)

- Appelez la <xref:System.Windows.Freezable.WritePostscript%2A> méthode avant de quitter les méthodes qui écrivent dans les membres de données de propriété de non dépendance.

Si votre classe contient des membres de données de propriété non-dépendance <xref:System.Windows.DependencyObject> qui sont des objets, vous devez <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> également appeler la méthode chaque fois que vous modifiez l’une de leurs valeurs, même si vous `null`définissez le membre sur.

> [!NOTE]
> Il est très important de commencer chaque <xref:System.Windows.Freezable> méthode que vous remplacez par un appel à l’implémentation de base.

Pour obtenir un exemple de classe <xref:System.Windows.Freezable> personnalisée, consultez l' [exemple animation personnalisée](https://go.microsoft.com/fwlink/?LinkID=159981).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Freezable>
- [Exemple d’animation personnalisée](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
