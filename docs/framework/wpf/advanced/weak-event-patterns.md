---
title: Modèles d'événement faible
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 0c5bae64fbbeddedd905e5df0b5789542e29f2f1
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833930"
---
# <a name="weak-event-patterns"></a>Modèles d'événement faible
Dans les applications, il est possible que les gestionnaires qui sont attachés à des sources d’événements ne seront pas détruits en coordination avec l’objet écouteur qui joint le gestionnaire à la source. Cette situation peut entraîner des fuites de mémoire. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] introduit un modèle de conception qui peut être utilisé pour résoudre ce problème, en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de cet événement. Ce modèle de conception est appelé le *modèle d’événement faible*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Pourquoi implémenter le modèle d’événement faible ?  
 Écoute des événements peut entraîner des fuites de mémoire. La technique standard pour écouter un événement consiste à utiliser la syntaxe spécifique au langage qui attache un gestionnaire à un événement sur une source. Par exemple, dans C#, que la syntaxe est : `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Cette technique crée une référence forte à partir de la source d’événements à l’écouteur d’événements. En règle générale, y attacher un gestionnaire d’événements pour un écouteur de provoque l’écouteur avoir une durée de vie d’objet qui est influencée par la durée de vie de la source (à moins que le Gestionnaire d’événements est supprimé explicitement). Toutefois, dans certaines circonstances, vous pouvez la durée de vie de l’écouteur à être contrôlé par d’autres facteurs, tels que si elle appartient actuellement à l’arborescence visuelle de l’application et non par la durée de vie de la source. Chaque fois que la durée de vie source s’étend au-delà de la durée de vie de l’écouteur, le modèle d’événement normal entraîne une fuite de mémoire : l’écouteur est maintenu actif plus longtemps que prévu.  
  
 Le modèle d’événement faible est conçu pour résoudre ce problème de fuite de mémoire. Le modèle d’événement faible peut être utilisé chaque fois qu’un écouteur doit s’inscrire à un événement, mais l’écouteur ne sait pas explicitement quand annuler l’inscription. Le modèle d’événement faible peut également servir à chaque fois que la durée de vie de la source dépasse la durée de vie utile de l’écouteur. (Dans ce cas, *utile* est déterminée par vous.) Le modèle d’événement faible permet à l’écouteur pour vous inscrire et recevoir l’événement sans affecter les caractéristiques de durée de vie d’objet de l’écouteur en aucune façon. En effet, la référence implicite à partir de la source ne détermine pas si l’écouteur est éligible pour le garbage collection. La référence est une référence faible, d'où le nom du modèle d’événement faible et connexes [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. L’écouteur peut être le garbage collector ou détruit, et la source peut continuer sans conserver des références de gestionnaire non-collectable à un objet détruit.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Qui doit implémenter le modèle d’événement faible ?  
 L’implémentation du modèle d’événement faible est intéressante principalement pour les auteurs de contrôles. En tant qu’auteur de contrôle, il vous incombe en grande partie pour le comportement et la relation contenant-contenu de votre contrôle et l’impact sur les applications dans lequel elle est insérée. Cela inclut le comportement de durée de vie l’objet contrôle, notamment la gestion du problème de fuite de mémoire décrit.  
  
 Certains scénarios, par nature, se prêtent à l’application du modèle d’événement faible. Un tel scénario est la liaison de données. Dans la liaison de données, il est courant de l’objet source soit complètement indépendante de l’objet de l’écouteur, qui est une cible d’une liaison. De nombreuses tâches associées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déjà une liaison de données ont le modèle d’événement faible appliqué dans la façon dont les événements sont implémentées.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Comment implémenter le modèle d’événement faible  
 Il existe trois façons d’implémenter le modèle d’événement faible. Le tableau suivant répertorie les trois approches et fournit quelques conseils pour l’utilisation de chacun.  
  
|Approche|Moment auquel implémenter|  
|--------------|-----------------------|  
|Utiliser une classe de gestionnaire d’événement faible existante|Si l’événement que vous voulez vous abonner correspond un <xref:System.Windows.WeakEventManager>, utilisez le Gestionnaire d’événement faible existant. Pour obtenir la liste des gestionnaires d’événements faible qui sont inclus avec WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe. Étant donné que les gestionnaires d’événements faible inclus sont limitées, vous devrez probablement choisir l’une des autres approches.|  
|Utiliser une classe de gestionnaire d’événement faible générique|Utiliser un générique <xref:System.Windows.WeakEventManager%602> lorsque existant <xref:System.Windows.WeakEventManager> est non disponible, vous cherchez un moyen simple d’implémenter, et vous ne le sont pas concernées par l’efficacité. Le modèle générique <xref:System.Windows.WeakEventManager%602> est moins efficace que d’un gestionnaire d’événements faibles existantes ou personnalisées. Par exemple, la classe générique fait plus de réflexion pour découvrir l’événement étant donné le nom de l’événement. En outre, le code pour inscrire l’événement à l’aide du modèle générique <xref:System.Windows.WeakEventManager%602> est plus longue que d’utiliser un existant ou personnalisé <xref:System.Windows.WeakEventManager>.|  
|Créer une classe de gestionnaire d’événement faible personnalisé|Créer un personnalisé <xref:System.Windows.WeakEventManager> lorsque existant <xref:System.Windows.WeakEventManager> n’est pas disponible et que vous souhaitez plus d’efficacité. L’aide d’un <xref:System.Windows.WeakEventManager> pour vous abonner à un événement sera plus efficace, mais vous n’entraînent pas le coût de l’écriture de code plus au début.|  
|Utiliser un gestionnaire d’événements faibles de tiers|NuGet a [plusieurs gestionnaires d’événements faible](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) et de nombreuses infrastructures WPF prennent également en charge le modèle (par exemple, consultez [documentation de Prism sur l’abonnement aux événements faiblement couplés](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).|

 Les sections suivantes décrivent comment implémenter le modèle d’événement faible.  Pour les besoins de cette discussion, l’événement pour vous abonner à présente les caractéristiques suivantes.  
  
- Le nom de l’événement est `SomeEvent`.  
  
- L’événement est déclenché par la `EventSource` classe.  
  
- Le Gestionnaire d’événements a le type : `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>`).  
  
- L’événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d’événements.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>À l’aide d’une classe de gestionnaire d’événements faible existante  
  
1. Recherchez un événement existant de faible manager.  
  
     Pour obtenir la liste des gestionnaires d’événements faible qui sont inclus avec WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe.  
  
2. Utilisez le nouveau gestionnaire d’événements faible au lieu de la connexion d’événements normal.  
  
     Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Modifier le modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour vous désabonner d’un événement :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Modifier le modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>À l’aide de la classe de gestionnaire d’événements faible générique  
  
1. Utiliser le modèle générique <xref:System.Windows.WeakEventManager%602> classe au lieu de la connexion d’événements normal.  
  
     Lorsque vous utilisez <xref:System.Windows.WeakEventManager%602> pour inscrire les écouteurs d’événements, vous fournissez la source d’événements et <xref:System.EventArgs> type que les paramètres de type pour la classe et appelez <xref:System.Windows.WeakEventManager%602.AddHandler%2A> comme indiqué dans le code suivant :  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Création d’une classe de gestionnaire d’événements faible personnalisée  
  
1. Copiez le modèle de classe suivant à votre projet.  
  
     Cette classe hérite de la <xref:System.Windows.WeakEventManager> classe.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Remplacez le `SomeEventWeakEventManager` nom avec votre propre nom.  
  
3. Remplacez les trois noms décrits précédemment avec les noms correspondants pour votre événement. (`SomeEvent`, `EventSource`, et `SomeEventEventArgs`)  
  
4. Définir la visibilité (publique / interne / privée) de la classe de gestionnaire d’événements faible pour la même visibilité que les événements qu’il gère.  
  
5. Utilisez le nouveau gestionnaire d’événements faible au lieu de la connexion d’événements normal.  
  
     Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Modifier le modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Modifier le modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
