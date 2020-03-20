---
title: Vue d'ensemble du glisser-déplacer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
ms.openlocfilehash: dd42af77300a7a93bbcbfa4c8f1fc365fc3f5da1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185980"
---
# <a name="drag-and-drop-overview"></a>Vue d'ensemble du glisser-déplacer
Cette rubrique offre une vue d'ensemble de la prise en charge du glisser-déplacer dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Le glisser-déplacer fait généralement référence à une méthode de transfert de données qui implique l'utilisation d'une souris (ou d'un autre dispositif de pointage) pour sélectionner un ou plusieurs objets, les faire glisser vers une cible de déplacement souhaitée dans l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et les y déplacer.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>Prise en charge du glisser-déplacer dans WPF  
 Les opérations de glisser-déplacer se composent généralement de deux parties : une source de glissement d'où provient l'objet glissé et une cible de déplacement qui reçoit l'objet déplacé.  La source de glissement et la cible de déplacement peuvent être des éléments d'interface utilisateur d'une même application ou d'une application différente.  
  
 Le type et le nombre d'objets qui peuvent être manipulés par glisser-déplacer sont totalement aléatoires. Par exemple, les fichiers, dossiers et sélections de contenu font partie des objets les plus couramment manipulés par les opérations de glisser-déplacer.  
  
 Les actions particulières exécutées pendant une opération de glisser-déplacer varient en fonction de l'application et sont souvent déterminées par le contexte.  Par exemple, glisser une sélection de fichiers d’un dossier à un autre sur le même périphérique de stockage déplace les fichiers par défaut, tandis que le fait de glisser des fichiers d’une convention universelle de nommage (UNC) se partage vers un dossier local copie les fichiers par défaut.  
  
 Les fonctionnalités de glisser-déplacer fournies par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont été conçues pour être très souples et personnalisables et ainsi prendre en charge un large éventail de scénarios de glisser-déplacer.  Le glisser-déplacer prend en charge la manipulation d'objets au sein d'une même application ou entre différentes applications. Le fait de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] traîner entre les applications et les autres applications Windows est également entièrement pris en charge.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tout <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> peut participer à l'opération de glisser-déplacer. Les événements et méthodes nécessaires aux opérations de glisser-déplacer sont définis dans la classe <xref:System.Windows.DragDrop>. Les classes <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> contiennent des alias pour les événements attachés <xref:System.Windows.DragDrop>, si bien que les événements apparaissent dans la liste des membres de classe quand un <xref:System.Windows.UIElement> ou un <xref:System.Windows.ContentElement> est hérité en tant qu'élément de base. Les gestionnaires d'événements attachés à ces événements sont attachés à l'événement attaché <xref:System.Windows.DragDrop> sous-jacent et reçoivent la même instance de données d'événement. Pour plus d'informations, consultez l'événement <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Le glisser-déplacer OLE ne fonctionne pas dans la zone Internet.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Transfert de données  
 Le glisser-déplacer fait partie du domaine plus général du transfert de données. Le transfert de données comprend les opérations de glisser-déplacer et de copier-coller. L'opération de glisser-déplacer est similaire aux opérations de copier-coller et de couper-coller utilisées pour transférer des données d'un objet ou d'une application à l'autre, à l'aide du presse-papiers du système. Ces deux types d'opération nécessitent :  
  
- un objet source qui fournit les données ;  
  
- un moyen de stockage temporaire des données transférées ;  
  
- un objet cible qui reçoit les données.  
  
 Dans une opération de copier-coller, le presse-papiers du système est utilisé pour stocker temporairement les données transférées ; dans une opération de glisser-déplacer, <xref:System.Windows.DataObject> est utilisé pour stocker les données. Par concept, un objet de données se compose d'une ou plusieurs paires de <xref:System.Object> qui contient les données réelles et un identificateur de format de données correspondant.  
  
 La source de glissement initie l'opération de glisser-déplacer en appelant la méthode statique <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> et en lui passant les données transférées. La méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> inclut automatiquement les données d'un <xref:System.Windows.DataObject> dans un wrapper, si nécessaire. Pour mieux contrôler le format de données, vous pouvez inclure les données d'un <xref:System.Windows.DataObject> dans un wrapper avant de les passer à la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>. La cible de déplacement est chargée d'extraire les données du <xref:System.Windows.DataObject>. Pour plus d’informations sur l’utilisation des objets de données, consultez [Données et objets de données](data-and-data-objects.md).  
  
 La source et la cible d'une opération de glisser-déplacer sont des éléments d'interface utilisateur ; cependant, les données réellement transférées ne sont généralement pas représentées visuellement. Vous pouvez écrire du code pour fournir une représentation visuelle des données déplacées, à l'instar de ce qui se produit quand vous faites glisser des fichiers dans l'Explorateur Windows. Par défaut, l'utilisateur est tenu au courant de l'effet de son action par la modification du curseur, par la représentation de l'effet que l'opération de glisser-déplacer aura sur les données si ces dernières sont déplacées ou copiées.  
  
### <a name="drag-and-drop-effects"></a>Effets de glisser-déplacer  
 Les opérations de glisser-déplacer peuvent avoir différents effets sur les données transférées. Par exemple, vous pouvez copier les données ou bien les déplacer. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit une énumération <xref:System.Windows.DragDropEffects> que vous pouvez utiliser pour spécifier l'effet d'une opération de glisser-déplacer. Dans la source de glissement, vous pouvez spécifier les effets que la source autorisera dans la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>. Dans la cible de déplacement, vous pouvez spécifier l'effet attendu de la cible dans la propriété <xref:System.Windows.DragEventArgs.Effects%2A> de la classe <xref:System.Windows.DragEventArgs>. Quand la cible de déplacement spécifie son effet prévu dans l'événement <xref:System.Windows.DragDrop.DragOver>, ces informations sont passées à la source de glissement dans l'événement <xref:System.Windows.DragDrop.GiveFeedback>. La source du glissement utilise ces informations pour informer l'utilisateur de l'effet prévu de la cible du déplacement sur les données. Quand les données sont déplacées, la cible de déplacement spécifie son effet réel dans l'événement <xref:System.Windows.DragDrop.Drop>. Ces informations sont passées à la source de glissement en tant que valeur de retour de la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>. Si la cible du déplacement retourne un effet qui n'est pas dans la liste des sources de glissement de `allowedEffects`, l'opération de glisser-déplacer est annulée sans que le transfert de données soit effectué.  
  
 Il est important de se rappeler que dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les valeurs <xref:System.Windows.DragDropEffects> servent uniquement à établir une communication entre la source de glissement et la cible de déplacement au sujet des effets de l'opération de glisser-déplacer. L'effet réel de l'opération de glisser-déplacer dépend de la façon dont vous aurez écrit le code de votre application.  
  
 Par exemple, la cible du déplacement peut spécifier que le déplacement de données vers celle-ci a pour effet de déplacer les données. Cependant, pour être déplacées, les données doivent être à la fois ajoutées à l'élément cible et supprimées de l'élément source. L'élément source peut indiquer qu'il permet le déplacement des données, mais si vous ne fournissez pas de code pour supprimer les données de l'élément source, cette action se traduit par la copie des données et non par leur déplacement.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Événements de glisser-déplacer  
 Les opérations de glisser-déplacer prennent en charge un modèle piloté par les événements.  La source du glissement et la cible du déplacement utilisent toutes deux un ensemble standard d'événements pour gérer les opérations de glisser-déplacer.  Les tableaux suivants récapitulent les événements de glisser-déplacer standard. Il s'agit d'événements attachés de la classe <xref:System.Windows.DragDrop>. Pour plus d’informations sur les événements attachés, consultez [Vue d’ensemble des événements attachés](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Événements de la source du glissement  
  
|Événement|Résumé|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Cet événement se produit continuellement pendant une opération de glisser-déplacer et permet à la source du déplacement de fournir une rétroaction visuelle à l'utilisateur. Cette rétroaction est généralement fournie par la modification de l'apparence du pointeur de la souris, indiquant les effets autorisés par la cible du déplacement.  Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Cet événement se produit quand il y a une modification dans les états du clavier ou du bouton de la souris pendant une opération de glisser-déplacer ; il permet à la source du déplacement d'annuler l'opération de glisser-déplacer selon les états de la touche/du bouton. Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Version de tunneling de <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Version de tunneling de <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Événements de la cible du déplacement  
  
|Événement|Résumé|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Cet événement se produit quand vous faites glisser un objet dans les limites de la cible du déplacement. Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.DragLeave>|Cet événement se produit quand vous faites glisser un objet hors des limites de la cible du déplacement.  Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.DragOver>|Cet événement se produit continuellement pendant le glissement (déplacement) d'un objet dans les limites de la cible du déplacement. Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.Drop>|Cet événement se produit quand vous déplacez un objet sur la cible du déplacement.  Il s'agit d'une propagation d'événements.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Version de tunneling de <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Version de tunneling de <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Version de tunneling de <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Version de tunneling de <xref:System.Windows.DragDrop.Drop>.|  
  
 Pour gérer les événements de glisser-déplacer des instances d'un objet, ajoutez des gestionnaires pour les événements répertoriés dans les tableaux précédents. Pour gérer des événements de glisser-déplacer au niveau de la classe, substituez les méthodes virtuelles On*Event et On\*PreviewEvent correspondantes. Pour plus d’informations, consultez [Gestion de classe des événements routés par les classes de base de contrôle](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Implémentation du glisser-déplacer  
 Un élément d'interface utilisateur peut être une source du glissement, une cible du déplacement ou les deux à la fois. Pour implémenter le glisser-déplacer de base, écrivez du code pour initier l'opération de glisser-déplacer et traiter les données déplacées. Vous pouvez améliorer le glisser-déplacer en gérant les événements de glisser-déplacer facultatifs.  
  
 Pour implémenter le glisser-déplacer de base, effectuez les tâches suivantes :  
  
- Identifiez l'élément destiné à être la source du glissement. Une source de glissement peut être un <xref:System.Windows.UIElement> ou un <xref:System.Windows.ContentElement>.  
  
- Créez un gestionnaire d’événements pour la source du glissement, qui sera chargé de lancer l’opération de glisser-déplacer. L'événement est généralement un événement <xref:System.Windows.UIElement.MouseMove>.  
  
- Dans le gestionnaire d'événements de la source de glissement, appelez la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> pour initier l'opération de glisser-déplacer. Dans l'appel <xref:System.Windows.DragDrop.DoDragDrop%2A>, spécifiez la source de glissement, les données à transférer et les effets autorisés.  
  
- Identifiez l'élément destiné à être la cible du glissement. Une cible de déplacement peut être un <xref:System.Windows.UIElement> ou un <xref:System.Windows.ContentElement>.  
  
- Sur la cible de déplacement, attribuez la valeur <xref:System.Windows.UIElement.AllowDrop%2A> à la propriété `true`.  
  
- Dans la cible de déplacement, créez un gestionnaire d'événements <xref:System.Windows.DragDrop.Drop>  pour traiter les données déplacées.  
  
- Dans le gestionnaire d'événements <xref:System.Windows.DragDrop.Drop>, extrayez les données de <xref:System.Windows.DragEventArgs> à l'aide des méthodes <xref:System.Windows.DataObject.GetDataPresent%2A> et <xref:System.Windows.DataObject.GetData%2A>.  
  
- Dans le gestionnaire d'événements <xref:System.Windows.DragDrop.Drop>, utilisez les données pour effectuer l'opération de glisser-déplacer souhaitée.  
  
 Vous pouvez améliorer votre implémentation du glisser-déplacer en créant un <xref:System.Windows.DataObject> personnalisé et en gérant des événements facultatifs de source de glissement et de cible de déplacement, comme le montrent les tâches suivantes :  
  
- Pour transférer des données personnalisées ou plusieurs éléments de données, créez un <xref:System.Windows.DataObject> à passer à la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
- Pour effectuer des actions supplémentaires pendant une opération de glissement, gérez les événements <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver> et <xref:System.Windows.DragDrop.DragLeave> sur la cible de déplacement.  
  
- Pour modifier l'apparence du pointeur de la souris, gérez l'événement <xref:System.Windows.DragDrop.GiveFeedback> sur la source de glissement.  
  
- Pour modifier la façon dont l'opération de glisser-déplacer est annulée, gérez l'événement <xref:System.Windows.DragDrop.QueryContinueDrag> sur la source de glissement.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Exemple de glisser-déplacer  
 Cette section explique comment implémenter le glisser-déplacer pour un élément <xref:System.Windows.Shapes.Ellipse>. <xref:System.Windows.Shapes.Ellipse> est à la fois une source de glissement et une cible de déplacement. Les données transférées sont la représentation sous forme de chaîne de la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de l'ellipse. Le code XAML suivant illustre l'élément <xref:System.Windows.Shapes.Ellipse> et les événements de glisser-déplacer associés qu'il gère. Pour obtenir les procédures complètes d’implémentation du glisser-déplacer, consultez [Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Autoriser un élément à être une source de glissement  
 Un objet qui devient source de glissement est chargé des opérations suivantes :  
  
- Identification du moment où se produit le glissement.  
  
- Lancement de l’opération de glisser-déplacer.  
  
- Identification des données à transférer.  
  
- Spécification des effets que l’opération de glisser-déplacer est autorisée à avoir sur les données transférées.  
  
 La source de glissement peut aussi fournir une rétroaction visuelle au sujet des actions autorisées (déplacement, copie, aucune) et peut annuler l'opération de glisser-déplacer en fonction d'autres entrées utilisateur, comme par exemple, appuyer sur la touche Échap durant l'opération de glissement.  
  
 Il revient à votre application de déterminer à quel moment une opération de glissement se produit et d'initier l'opération de glisser-déplacer en appelant la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>. Il s'agit en général d'un événement <xref:System.Windows.UIElement.MouseMove> qui se produit sur l'élément à faire glisser pendant que l'utilisateur appuie sur un bouton de la souris. L’exemple suivant montre comment initier une opération de glisser-déposer à partir du gestionnaire d’événements <xref:System.Windows.UIElement.MouseMove> d’un élément <xref:System.Windows.Shapes.Ellipse> pour faire de ce dernier la source de glissement. Les données transférées sont la représentation sous forme de chaîne de la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de l'ellipse.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Dans le gestionnaire d'événements <xref:System.Windows.UIElement.MouseMove>, appelez la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> pour initier l'opération de glisser-déplacer. La méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> accepte trois paramètres :  
  
- `dragSource` : référence à l'objet de dépendance correspondant à la source des données transférées ; il s'agit généralement de la source de l'événement <xref:System.Windows.UIElement.MouseMove>.  
  
- `data` : objet qui contient les données transférées, inclus dans un wrapper dans un <xref:System.Windows.DataObject>.  
  
- `allowedEffects` : une des valeurs d'énumération <xref:System.Windows.DragDropEffects> qui spécifie les effets autorisés de l'opération de glisser-déplacer.  
  
 N'importe quel objet sérialisable peut être passé dans le paramètre `data`. Si les données ne sont pas déjà incluses dans un wrapper dans un <xref:System.Windows.DataObject>, elles sont automatiquement incluses dans un wrapper dans un nouveau <xref:System.Windows.DataObject>. Pour passer plusieurs éléments de données, vous devez créer vous-même le <xref:System.Windows.DataObject> et le passer à la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A>. Pour plus d’informations, consultez [Données et objets de données](data-and-data-objects.md).  
  
 Le paramètre `allowedEffects` est utilisé pour spécifier ce que la source du glissement autorise la cible du glissement à faire des données transférées. Les valeurs courantes pour une source de glissement sont <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move> et <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
> La cible du déplacement peut aussi spécifier les effets prévus en réponse aux données déplacées. Par exemple, si la cible de déplacement ne reconnaît pas le type de données à déplacer, elle peut refuser les données en attribuant à ses effets autorisés la valeur <xref:System.Windows.DragDropEffects.None>. C'est généralement le cas de son gestionnaire d'événements <xref:System.Windows.DragDrop.DragOver>.  
  
 Une source de glissement peut éventuellement gérer les événements <xref:System.Windows.DragDrop.GiveFeedback> et <xref:System.Windows.DragDrop.QueryContinueDrag>. Ces événements possèdent des gestionnaires par défaut qui sont utilisés, à moins que vous marquiez les événements comme gérés. En général, vous pouvez ignorer ces événements, sauf si vous avez besoin de modifier leur comportement par défaut.  
  
 L'événement <xref:System.Windows.DragDrop.GiveFeedback> est déclenché en continu pendant l'opération de glissement de la source. Le gestionnaire par défaut de cet événement vérifie que la source du glissement se trouve sur une cible de dépôt valide. Si c'est le cas, il vérifie les effets autorisés de la cible du déplacement. Il fournit ensuite une rétroaction visuelle au sujet des effets de déplacement autorisés. Cette rétroaction visuelle se traduit généralement par le changement du curseur de la souris en curseur ne permettant ni copie, ni déplacement. Cet événement doit uniquement être géré si vous avez besoin d'utiliser des curseurs personnalisés pour fournir une rétroaction visuelle. Si vous gérez cet événement, assurez-vous de le marquer comme étant géré de sorte que le gestionnaire par défaut ne substitue pas à votre gestionnaire.  
  
 L'événement <xref:System.Windows.DragDrop.QueryContinueDrag> est déclenché en continu pendant l'opération de glissement de la source. Vous pouvez gérer cet événement pour déterminer l’action qui doit terminer l’opération de glisser-déplacer, en fonction de l’état des touches Échap, Maj, Ctrl et Alt, ainsi que de l’état des boutons de la souris. Le gestionnaire par défaut de cet événement annule l'opération de glisser-déplacer si la touche Échap est enfoncée et déplace les données si le bouton de la souris est relâché.  
  
> [!CAUTION]
> Ces événements sont déclenchés en continu pendant l'opération de glisser-déplacer. Par conséquent, vous devez éviter les tâches nécessitant de nombreuses ressources dans les gestionnaires d'événements.  Utilisez, par exemple, un curseur mis en cache au lieu de créer un nouveau curseur chaque fois qu'un événement <xref:System.Windows.DragDrop.GiveFeedback> est déclenché.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Autoriser un élément à être une cible de déplacement  
 Un objet qui devient cible de déplacement est chargé des opérations suivantes :  
  
- Confirmation qu’il s’agit d’une cible de déplacement valide.  
  
- Réponse à la source du glissement quand elle effectue le glissement vers la cible.  
  
- Vérification que les données transférées sont dans un format qu’elle peut recevoir.  
  
- Traitement des données déplacées.  
  
 Pour spécifier un élément en tant que cible de déplacement, attribuez la valeur <xref:System.Windows.UIElement.AllowDrop%2A> à la propriété `true`. Les événements de cible de déplacement seront ensuite déclenchés sur cet élément pour que vous puissiez les gérer. Pendant une opération de glisser-déplacer, la séquence d'événements suivante se produit sur la cible du déplacement :  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> ou <xref:System.Windows.DragDrop.Drop>  
  
 L'événement <xref:System.Windows.DragDrop.DragEnter> se produit quand les données sont glissées dans les limites de la cible de déplacement. En général, la gestion de cet événement vous permet d’obtenir un aperçu des effets de l’opération de glisser-déplacer, si cela est adapté à votre application. Ne définissez pas la propriété <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> dans l'événement <xref:System.Windows.DragDrop.DragEnter>, car elle sera remplacée dans l'événement <xref:System.Windows.DragDrop.DragOver>.  
  
 L'exemple suivant illustre le gestionnaire d'événements <xref:System.Windows.DragDrop.DragEnter> pour un élément <xref:System.Windows.Shapes.Ellipse>. Ce code permet d'obtenir un aperçu des effets de l'opération de glisser-déplacer en enregistrant le pinceau <xref:System.Windows.Shapes.Shape.Fill%2A> actif. Il utilise ensuite la méthode <xref:System.Windows.DataObject.GetDataPresent%2A> pour vérifier que le <xref:System.Windows.DataObject> déplacé sur l'ellipse contient bien les données de chaîne qui peuvent être converties en <xref:System.Windows.Media.Brush>. Si tel est le cas, les données sont extraites à l'aide de la méthode <xref:System.Windows.DataObject.GetData%2A>. Elles sont ensuite converties en <xref:System.Windows.Media.Brush> avant d'être appliquées à l'ellipse. La modification peut être annulée dans le gestionnaire d'événements <xref:System.Windows.DragDrop.DragLeave>. Si les données ne peuvent pas être converties en <xref:System.Windows.Media.Brush>, aucune action n'est effectuée.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 L'événement <xref:System.Windows.DragDrop.DragOver> se produit en continu pendant le déplacement des données sur la cible de déplacement. Cet événement est couplé à l'événement <xref:System.Windows.DragDrop.GiveFeedback> sur la source de glissement. Dans le gestionnaire d'événements <xref:System.Windows.DragDrop.DragOver>, les méthodes <xref:System.Windows.DataObject.GetDataPresent%2A> et <xref:System.Windows.DataObject.GetData%2A> sont généralement utilisées pour vérifier que les données transférées sont dans un format que la cible de déplacement peut traiter. Vous pouvez aussi vérifier si des touches de modification sont enfoncées, ce qui indique en général que l'utilisateur a l'intention d'opérer une copie ou un déplacement. Une fois ces vérifications effectuées, définissez la propriété <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> pour notifier la source de glissement de l’effet prévu du dépôt des données. La source de glissement reçoit ces informations dans les arguments de l'événement <xref:System.Windows.DragDrop.GiveFeedback> et peut définir un curseur approprié de façon à fournir une rétroaction visuelle.  
  
 L'exemple suivant illustre le gestionnaire d'événements <xref:System.Windows.DragDrop.DragOver> pour un élément <xref:System.Windows.Shapes.Ellipse>. Ce code vérifie que le <xref:System.Windows.DataObject> déplacé sur l'ellipse contient bien des données de chaîne qui peuvent être converties en <xref:System.Windows.Media.Brush>. Si tel est le cas, il attribue à la propriété <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.DragDropEffects.Copy>. Cela indique à la source du glissement que les données peuvent être copiées vers l'ellipse. Si les données ne peuvent pas être converties en <xref:System.Windows.Media.Brush>, la propriété <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> prend la valeur <xref:System.Windows.DragDropEffects.None>. Cela indique à la source du glissement que l’ellipse n’est pas une cible de dépôt valide pour les données.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 L'événement <xref:System.Windows.DragDrop.DragLeave> se produit quand les données sont glissées hors des limites de la cible sans être déplacées. Cet événement permet d'annuler toutes vos actions dans le gestionnaire d'événements <xref:System.Windows.DragDrop.DragEnter>.  
  
 L'exemple suivant illustre le gestionnaire d'événements <xref:System.Windows.DragDrop.DragLeave> pour un élément <xref:System.Windows.Shapes.Ellipse>. Ce code annule l'aperçu fourni par le gestionnaire d'événements <xref:System.Windows.DragDrop.DragEnter> en appliquant le <xref:System.Windows.Media.Brush> enregistré à l'ellipse.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 L'événement <xref:System.Windows.DragDrop.Drop>  se produit quand les données sont déplacées sur la cible de déplacement ; par défaut, cela se produit quand le bouton de la souris est relâché. Dans le gestionnaire d'événements <xref:System.Windows.DragDrop.Drop>, utilisez la méthode <xref:System.Windows.DataObject.GetData%2A> pour extraire les données transférées à partir du <xref:System.Windows.DataObject> et exécuter tout traitement de données requis par votre application. L'événement <xref:System.Windows.DragDrop.Drop> met fin à l'opération de glisser-déplacer.  
  
 L'exemple suivant illustre le gestionnaire d'événements <xref:System.Windows.DragDrop.Drop> pour un élément <xref:System.Windows.Shapes.Ellipse>. Ce code applique les effets de l'opération de glisser-déplacer et est similaire à celui du gestionnaire d'événements <xref:System.Windows.DragDrop.DragEnter>. Il vérifie que le <xref:System.Windows.DataObject> déplacé sur l'ellipse contient bien des données de chaîne qui peuvent être converties en <xref:System.Windows.Media.Brush>. Dans ce cas, le <xref:System.Windows.Media.Brush> est appliqué à l'ellipse. Si les données ne peuvent pas être converties en <xref:System.Windows.Media.Brush>, aucune action n'est effectuée.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Clipboard>
- [Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Sujets comment se passer](drag-and-drop-how-to-topics.md)
- [Drag and Drop](drag-and-drop.md)
