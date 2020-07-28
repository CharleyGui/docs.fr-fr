---
title: Modèles d'événement faible
description: En savoir plus sur le modèle d’événement faible Windows Presentation Foundation, qui résout le problème des gestionnaires qui ne sont pas détruits, évitant les fuites de mémoire.
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168265"
---
# <a name="weak-event-patterns"></a>Modèles d'événement faible
Dans les applications, il est possible que les gestionnaires qui sont attachés à des sources d’événements ne soient pas détruits avec l’objet d’écouteur qui a attaché le gestionnaire à la source. Cette situation peut entraîner des fuites de mémoire. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]introduit un modèle de conception qui peut être utilisé pour résoudre ce problème, en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de cet événement. Ce modèle de conception est connu sous le nom de *modèle d’événement faible*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Pourquoi implémenter le modèle d’événement faible ?  
 L’écoute des événements peut entraîner des fuites de mémoire. La technique classique pour écouter un événement consiste à utiliser la syntaxe spécifique au langage qui attache un gestionnaire à un événement sur une source. Par exemple, en C#, cette syntaxe est la suivante : `source.SomeEvent += new SomeEventHandler(MyEventHandler)` .  
  
 Cette technique crée une référence forte de la source de l’événement à l’écouteur d’événements. En règle générale, l’attachement d’un gestionnaire d’événements pour un écouteur amène l’écouteur à avoir une durée de vie d’objet influencée par la durée de vie de l’objet de la source (sauf si le gestionnaire d’événements est supprimé explicitement). Toutefois, dans certaines circonstances, vous souhaiterez peut-être que la durée de vie des objets de l’écouteur soit contrôlée par d’autres facteurs, par exemple s’il appartient actuellement à l’arborescence d’éléments visuels de l’application, et non par la durée de vie de la source. Chaque fois que la durée de vie de l’objet source s’étend au-delà de la durée de vie des objets de l’écouteur, le modèle d’événement normal entraîne une fuite de mémoire : l’écouteur reste actif plus longtemps que prévu.  
  
 Le modèle d’événement faible est conçu pour résoudre ce problème de fuite de mémoire. Le modèle d’événement faible peut être utilisé chaque fois qu’un écouteur doit s’inscrire pour un événement, mais l’écouteur ne sait pas explicitement quand annuler l’inscription. Le modèle d’événement faible peut également être utilisé chaque fois que la durée de vie d’objet de la source dépasse la durée de vie d’objet utile de l’écouteur. (Dans ce cas, *utile* est déterminé par vous.) Le modèle d’événement faible permet à l’écouteur de s’inscrire pour recevoir l’événement sans affecter les caractéristiques de durée de vie des objets de l’écouteur de quelque manière que ce soit. En effet, la référence implicite de la source ne détermine pas si l’écouteur est éligible pour garbage collection. La référence est une référence faible, donc la dénomination du modèle d’événement faible et les API associées. L’écouteur peut être récupéré par le garbage collector ou détruit, et la source peut continuer sans conserver les références de gestionnaire non collectées à un objet désormais détruit.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Qui doit implémenter le modèle d’événement faible ?  
 L’implémentation du modèle d’événement faible est particulièrement intéressante pour les auteurs de contrôle. En tant qu’auteur de contrôle, vous êtes en grande partie responsable du comportement et de la relation contenant-contenu de votre contrôle, ainsi que de l’impact qu’il a sur les applications dans lesquelles il est inséré. Cela comprend le comportement de durée de vie des objets de contrôle, en particulier la gestion du problème de fuite de mémoire décrit.  
  
 Certains scénarios se prêtent par nature à l’application du modèle d’événement faible. La liaison de données est un scénario de ce type. Dans la liaison de données, il est courant que l’objet source soit complètement indépendant de l’objet d’écouteur, qui est la cible d’une liaison. De nombreux aspects de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] liaison de données ont déjà le modèle d’événement faible qui est appliqué dans la manière dont les événements sont implémentés.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Comment implémenter le modèle d’événement faible  
 Il existe trois façons d’implémenter un modèle d’événement faible. Le tableau suivant répertorie les trois approches et fournit des conseils sur l’utilisation de chacune d’elles.  
  
|Approche|Quand implémenter|  
|--------------|-----------------------|  
|Utiliser une classe de gestionnaire d’événements faible existante|Si l’événement auquel vous souhaitez vous abonner a un correspondant <xref:System.Windows.WeakEventManager> , utilisez le gestionnaire d’événements faible existant. Pour obtenir la liste des gestionnaires d’événements faibles inclus dans WPF, consultez la hiérarchie d’héritage dans la <xref:System.Windows.WeakEventManager> classe. Étant donné que les gestionnaires d’événements faibles inclus sont limités, vous devrez probablement choisir l’une des autres approches.|  
|Utiliser une classe de gestionnaire d’événements faible générique|Utilisez un générique <xref:System.Windows.WeakEventManager%602> lorsqu’un existant <xref:System.Windows.WeakEventManager> n’est pas disponible, vous avez besoin d’un moyen simple d’implémenter et vous ne vous inquiétez pas de l’efficacité. Le générique <xref:System.Windows.WeakEventManager%602> est moins efficace qu’un gestionnaire d’événements faible existant ou personnalisé. Par exemple, la classe générique fait plus de réflexion pour découvrir l’événement en fonction du nom de l’événement. En outre, le code permettant d’enregistrer l’événement à l’aide du générique <xref:System.Windows.WeakEventManager%602> est plus détaillé que l’utilisation d’un existant ou d’un personnalisé <xref:System.Windows.WeakEventManager> .|  
|Créer une classe de gestionnaire d’événements faibles personnalisée|Créez un personnalisé <xref:System.Windows.WeakEventManager> lorsqu’un existant <xref:System.Windows.WeakEventManager> n’est pas disponible et que vous souhaitez obtenir une efficacité optimale. L’utilisation d’un personnalisé <xref:System.Windows.WeakEventManager> pour s’abonner à un événement est plus efficace, mais vous encourez le coût de l’écriture de code supplémentaire au début.|  
|Utiliser un gestionnaire d’événements faibles tiers|NuGet possède [plusieurs gestionnaires d’événements faibles](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) et de nombreuses infrastructures WPF prennent également en charge le modèle (par exemple, consultez la [documentation de Prism sur l’abonnement aux événements faiblement couplés](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).|

 Les sections suivantes décrivent comment implémenter le modèle d’événement faible.  Dans le cadre de cette discussion, l’événement auquel s’abonner a les caractéristiques suivantes.  
  
- Le nom de l’événement est `SomeEvent` .  
  
- L’événement est déclenché par la `EventSource` classe.  
  
- Le gestionnaire d’événements a le type : `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>` ).  
  
- L’événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d’événements.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Utilisation d’une classe de gestionnaire d’événements faible existante  
  
1. Recherchez un gestionnaire d’événements faible existant.  
  
     Pour obtenir la liste des gestionnaires d’événements faibles inclus dans WPF, consultez la hiérarchie d’héritage dans la <xref:System.Windows.WeakEventManager> classe.  
  
2. Utilisez le nouveau gestionnaire d’événements faible plutôt que le raccordement d’événement normal.  
  
     Par exemple, si votre code utilise le modèle suivant pour s’abonner à un événement :  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Remplacez-le par le modèle suivant :  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour se désabonner d’un événement :  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Remplacez-le par le modèle suivant :  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Utilisation de la classe de gestionnaire d’événements faible générique  
  
1. Utilisez la classe générique à <xref:System.Windows.WeakEventManager%602> la place de l’événement de raccordement normal.  
  
     Quand vous utilisez <xref:System.Windows.WeakEventManager%602> pour inscrire des écouteurs d’événements, vous fournissez la source et le type de l’événement <xref:System.EventArgs> en tant que paramètres de type à la classe et appelez <xref:System.Windows.WeakEventManager%602.AddHandler%2A> comme indiqué dans le code suivant :  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Création d’une classe de gestionnaire d’événements faibles personnalisée  
  
1. Copiez le modèle de classe suivant dans votre projet.  
  
     Cette classe hérite de la <xref:System.Windows.WeakEventManager> classe.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Remplacez le `SomeEventWeakEventManager` nom par votre propre nom.  
  
3. Remplacez les trois noms décrits précédemment par les noms correspondants pour votre événement. ( `SomeEvent` , `EventSource` et `SomeEventEventArgs` )  
  
4. Affectez à la visibilité (publique/interne/privée) de la classe de gestionnaire d’événements faible la même visibilité que l’événement qu’elle gère.  
  
5. Utilisez le nouveau gestionnaire d’événements faible plutôt que le raccordement d’événement normal.  
  
     Par exemple, si votre code utilise le modèle suivant pour s’abonner à un événement :  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Remplacez-le par le modèle suivant :  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Remplacez-le par le modèle suivant :  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Vue d'ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
