---
title: UI Automation d'un contrôle personnalisé WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: ef045ffaac47c6cb196d821c25d96c4d2cd7bf88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254248"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>UI Automation d'un contrôle personnalisé WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] fournit une interface unique et généralisée que les clients Automation peuvent utiliser pour examiner ou utiliser les interfaces utilisateur de diverses plateformes et infrastructures. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] active à la fois le code d’assurance qualité (test) et les applications d’accessibilité, par exemple les lecteurs d’écran, pour examiner les éléments de l’interface utilisateur et simuler la manière dont les utilisateurs interagissent avec ces éléments à partir d’un autre code. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] pour toutes les plateformes, consultez la rubrique d’accessibilité.  
  
 Cette rubrique explique comment implémenter un fournisseur UI Automation côté serveur pour un contrôle personnalisé qui s’exécute dans une application WPF. WPF prend en charge [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] à travers une arborescence d’objets Automation homologues qui présente en parallèle l’arborescence des éléments de l’interface utilisateur. Le code de test et les applications qui fournissent des fonctionnalités d’accessibilité peuvent utiliser des objets homologues Automation, soit directement (pour le code in-process), soit travers l’interface généralisée fournie par [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Classes homologues Automation  
 Les contrôles WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prennent en charge via une arborescence de classes homologues qui dérivent de. <xref:System.Windows.Automation.Peers.AutomationPeer> Par convention, les noms de classes homologues commencent par le nom de la classe de contrôle et se terminent par « AutomationPeer ». Par exemple, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> est la classe homologue pour <xref:System.Windows.Controls.Button> la classe de contrôle. Les classes homologues sont à peu près équivalentes aux types de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], mais sont spécifiques aux éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Le code Automation qui accède aux applications WPF via l’interface [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] n’utilise pas directement les homologues Automation, mais le code Automation dans le même espace de processus peut utiliser directement les homologues Automation.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Classes homologues Automation intégrées  
 Des éléments implémentent une classe homologue Automation s’ils acceptent l’activité de l’utilisateur dans l’interface, ou s’ils contiennent les informations dont ont besoin les utilisateurs d’applications de lecteur d’écran. Tous les éléments visuels WPF n’ont pas d’homologues Automation. , Et <xref:System.Windows.Controls.Button> sont<xref:System.Windows.Controls.Label>des exemples de classes qui implémentent des homologues Automation. <xref:System.Windows.Controls.TextBox> Les classes qui <xref:System.Windows.Controls.Decorator>dérivent de, <xref:System.Windows.Controls.Border>telles <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> que et sont des classes qui n’implémentent pas d’homologues Automation, comme et <xref:System.Windows.Controls.Canvas>.  
  
 La classe <xref:System.Windows.Controls.Control> de base n’a pas de classe homologue correspondante. Si vous avez besoin d’une classe homologue pour correspondre à un contrôle personnalisé qui <xref:System.Windows.Controls.Control>dérive de, vous devez dériver la <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>classe homologue personnalisée de.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Considérations relatives à la sécurité des homologues dérivés  
 Les homologues Automation doivent s’exécuter dans un environnement de confiance partielle. Le code dans l’assembly UIAutomationClient n’est pas configuré pour s’exécuter dans un environnement de confiance partielle et le code homologue Automation ne doit pas référencer cet assembly. Au lieu de cela, vous devez utiliser les classes de l’assembly UIAutomationTypes. Par exemple, vous devez utiliser la <xref:System.Windows.Automation.AutomationElementIdentifiers> classe de l’assembly UIAutomationTypes, qui correspond à <xref:System.Windows.Automation.AutomationElement> la classe dans l’assembly UIAutomationClient. La démarche la plus sûre consiste à référencer l’assembly UIAutomationTypes dans le code homologue Automation.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Navigation homologue  
 Après avoir localisé un homologue Automation, le code in-process peut naviguer dans l’arborescence homologue en <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> appelant <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> les méthodes et de l’objet. La navigation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] entre les éléments d’un contrôle est prise en charge par l’implémentation <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> de la méthode par l’homologue. Le système UI Automation appelle cette méthode pour générer une arborescence de sous-éléments contenus dans un contrôle ; par exemple, des éléments de liste dans une zone de liste. La méthode <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> par défaut parcourt l’arborescence visuelle des éléments pour créer l’arborescence des homologues Automation. Les contrôles personnalisés contournent cette méthode pour exposer les éléments enfants aux clients Automation, en retournant les homologues Automation des éléments qui acheminent des informations ou qui permettent une interaction avec l’utilisateur.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Personnalisations dans un homologue dérivé  
 Toutes les classes qui dérivent de <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> contiennent la <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>méthode virtuelle protégée. Les appels <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> WPF pour obtenir l’objet homologue Automation pour chaque contrôle. Le code Automation peut utiliser l’homologue pour obtenir des informations sur les caractéristiques et les fonctionnalités d’un contrôle et pour simuler une utilisation interactive. Un contrôle personnalisé qui prend en charge Automation doit <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> substituer et retourner une instance d’une classe qui dérive de <xref:System.Windows.Automation.Peers.AutomationPeer>. Par exemple, si un contrôle personnalisé dérive de la <xref:System.Windows.Controls.Primitives.ButtonBase> classe, l’objet retourné par <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> doit dériver de <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Lorsque vous implémentez un contrôle personnalisé, vous devez substituer les méthodes « Core » à partir de la classe homologue Automation de base qui décrivent le comportement unique et spécifique à votre contrôle personnalisé.  
  
### <a name="override-oncreateautomationpeer"></a>Substituer la méthode OnCreateAutomationPeer  
 Substituez la <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> méthode pour votre contrôle personnalisé afin qu’il retourne votre objet fournisseur, qui doit dériver directement ou indirectement <xref:System.Windows.Automation.Peers.AutomationPeer>de.  
  
### <a name="override-getpattern"></a>Substituer la méthode GetPattern  
 Les homologues Automation simplifient certains aspects de l’implémentation des fournisseurs [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] côté serveur, fournisseurs, mais les homologues Automation d’un contrôle personnalisé doivent encore gérer les interfaces de modèle. Comme les fournisseurs non-WPF, les homologues prennent en charge les modèles de contrôle en <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> fournissant des implémentations <xref:System.Windows.Automation.Provider.IInvokeProvider>d’interfaces dans l’espace de noms, telles que. Les interfaces de modèle de contrôle peuvent être implémentées par l’homologue lui-même ou par un autre objet. L’implémentation de l’homologue de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> retourne l’objet qui prend en charge le modèle spécifié. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]le code appelle <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> la méthode et spécifie une valeur d' <xref:System.Windows.Automation.Peers.PatternInterface> énumération. Votre substitution de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> doit retourner l’objet qui implémente le modèle spécifié. Si votre contrôle n’a pas d’implémentation personnalisée d’un modèle, vous pouvez appeler l’implémentation du type de base <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> de pour récupérer son implémentation ou une valeur null si le modèle n’est pas pris en charge pour ce type de contrôle. Par exemple, un contrôle NumericUpDown personnalisé peut être défini sur une valeur comprise dans une plage [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] , donc son homologue implémente l' <xref:System.Windows.Automation.Provider.IRangeValueProvider> interface. L’exemple suivant montre comment la méthode de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> l’homologue est substituée pour répondre <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> à une valeur.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Une <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> méthode peut également spécifier un sous-élément comme fournisseur de modèles. Le code suivant montre comment <xref:System.Windows.Controls.ItemsControl> transfère la gestion du modèle de défilement vers l’homologue de son contrôle interne. <xref:System.Windows.Controls.ScrollViewer>  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Pour spécifier un sous-élément pour la gestion des modèles, ce code obtient l’objet de sous-élément, crée <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> un homologue à <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> l’aide de la méthode, affecte à la propriété du nouvel homologue la valeur de l’homologue actuel et retourne le nouvel homologue. La <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> définition d’un sous-élément empêche le sous-élément d’apparaître dans l’arborescence homologue Automation et désigne tous les événements déclenchés par le sous-élément comme <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>provenant du contrôle spécifié dans. Le <xref:System.Windows.Controls.ScrollViewer> contrôle n’apparaît pas dans l’arborescence Automation et les événements de défilement qu’il génère semblent provenir de l' <xref:System.Windows.Controls.ItemsControl> objet.  
  
### <a name="override-core-methods"></a>Substituer les méthodes « Core »  
 Le code Automation obtient des informations sur votre contrôle en appelant des méthodes publiques de la classe homologue. Pour fournir des informations sur votre contrôle, substituez chaque méthode dont le nom se termine par « Core » lorsque l’implémentation de votre contrôle diffère de celle fournie par la classe homologue Automation de base. Au minimum, votre contrôle doit implémenter les <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> méthodes <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> et, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Votre implémentation de <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> décrit votre contrôle en retournant <xref:System.Windows.Automation.ControlType> une valeur. Bien que vous puissiez <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>retourner, vous devez retourner l’un des types de contrôle plus spécifiques s’il décrit précisément votre contrôle. Une valeur de retour <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> de requiert un travail supplémentaire que le fournisseur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]doit implémenter, et [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] les produits clients ne peuvent pas anticiper la structure de contrôle, l’interaction du clavier et les modèles de contrôle possibles.  
  
 Implémentez <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> les <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> méthodes et pour indiquer si votre contrôle contient du contenu de données ou s’il accomplit un rôle interactif dans l’interface utilisateur (ou les deux). Par défaut, ces deux méthodes retournent `true`. Ces paramètres facilitent l’utilisation des outils Automatisation, comme les lecteurs d’écran, qui peuvent utiliser ces méthodes pour filtrer l’arborescence Automation. Si votre <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> méthode transfère la gestion des modèles à un homologue de sous-élément, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> la méthode de l’homologue de sous-élément peut retourner la valeur false pour masquer l’homologue de sous-élément de l’arborescence Automation. Par exemple, le défilement dans un <xref:System.Windows.Controls.ListBox> est géré par un <xref:System.Windows.Controls.ScrollViewer>, et l’homologue Automation <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> pour est retourné par <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> la méthode du <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> associé à <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Par conséquent, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> la méthode <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> `false` de<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> retourne, afin que n’apparaisse pas dans l’arborescence Automation.  
  
 Votre homologue Automation doit fournir des valeurs par défaut appropriées pour votre contrôle. Notez que le code XAML qui référence votre contrôle peut remplacer vos implémentations d’homologue des méthodes <xref:System.Windows.Automation.AutomationProperties> principales en incluant des attributs. Par exemple, le code XAML suivant crée un bouton qui comporte deux propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] personnalisées.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implémenter des fournisseurs de modèles  
 Les interfaces implémentées par un fournisseur personnalisé sont déclarées explicitement si l’élément propriétaire dérive <xref:System.Windows.Controls.Control>directement de. Par exemple, le code suivant déclare un homologue pour un <xref:System.Windows.Controls.Control> qui implémente une valeur de plage.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Si le contrôle propriétaire dérive d’un type spécifique de contrôle <xref:System.Windows.Controls.Primitives.RangeBase>, par exemple, l’homologue peut être dérivé d’une classe homologue dérivée équivalente. Dans ce cas, l’homologue dériverait de <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, qui fournit une implémentation de base de. <xref:System.Windows.Automation.Provider.IRangeValueProvider> Le code suivant illustre la déclaration de ce type d’homologue.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Pour obtenir un exemple d’implémentation, [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) consultez ou [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) code source qui implémente et consomme un contrôle personnalisé NumericUpDown.  
  
### <a name="raise-events"></a>Déclencher des événements  
 Les clients Automation peuvent s’abonner à des événements Automation. Les contrôles personnalisés doivent signaler les modifications apportées à <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> l’état du contrôle en appelant la méthode. De même, lorsqu’une valeur de propriété change, appelez <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> la méthode. Le code suivant montre comment obtenir l’objet homologue à partir du code de contrôle et appeler une méthode pour déclencher un événement. À des fins d’optimisation, le code détermine s’il existe des écouteurs pour ce type d’événement. Déclencher l’événement uniquement lorsqu’il y a des écouteurs évite les surcharges inutiles et permet au contrôle de rester réactif.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’UI Automation](../../ui-automation/ui-automation-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Contrôle personnalisé NumericUpDown (C#) sur GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Contrôle personnalisé NumericUpDown (Visual Basic) sur GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
