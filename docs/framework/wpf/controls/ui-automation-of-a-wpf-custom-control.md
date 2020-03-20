---
title: Automatisation de l’interface utilisateur d’un contrôle personnalisé
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
ms.openlocfilehash: 9c33d0e5da70820041ba2a2881082d9f7d179fc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187506"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>UI Automation d'un contrôle personnalisé WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] fournit une interface unique et généralisée que les clients Automation peuvent utiliser pour examiner ou utiliser les interfaces utilisateur de diverses plateformes et infrastructures. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] active à la fois le code d’assurance qualité (test) et les applications d’accessibilité, par exemple les lecteurs d’écran, pour examiner les éléments de l’interface utilisateur et simuler la manière dont les utilisateurs interagissent avec ces éléments à partir d’un autre code. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] pour toutes les plateformes, consultez la rubrique d’accessibilité.  
  
 Cette rubrique explique comment implémenter un fournisseur UI Automation côté serveur pour un contrôle personnalisé qui s’exécute dans une application WPF. WPF prend en charge [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] à travers une arborescence d’objets Automation homologues qui présente en parallèle l’arborescence des éléments de l’interface utilisateur. Le code de test et les applications qui fournissent des fonctionnalités d’accessibilité peuvent utiliser des objets homologues Automation, soit directement (pour le code in-process), soit travers l’interface généralisée fournie par [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>Classes homologues Automation  
 WPF contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] le soutien à travers <xref:System.Windows.Automation.Peers.AutomationPeer>un arbre de classes de pairs qui dérivent de . Par convention, les noms de classes homologues commencent par le nom de la classe de contrôle et se terminent par « AutomationPeer ». Par exemple, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> est la <xref:System.Windows.Controls.Button> classe de pairs pour la classe de contrôle. Les classes de pairs [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sont à peu près équivalentes aux types de contrôle, mais sont spécifiques aux éléments WPF. Le code Automation qui accède aux applications WPF via l’interface [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] n’utilise pas directement les homologues Automation, mais le code Automation dans le même espace de processus peut utiliser directement les homologues Automation.  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>Classes homologues Automation intégrées  
 Des éléments implémentent une classe homologue Automation s’ils acceptent l’activité de l’utilisateur dans l’interface, ou s’ils contiennent les informations dont ont besoin les utilisateurs d’applications de lecteur d’écran. Tous les éléments visuels WPF n’ont pas d’homologues Automation. Exemples de classes qui <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>mettent <xref:System.Windows.Controls.Label>en œuvre des pairs d’automatisation sont , , et . Des exemples de classes qui ne mettent <xref:System.Windows.Controls.Decorator>pas <xref:System.Windows.Controls.Border>en œuvre <xref:System.Windows.Controls.Panel>des <xref:System.Windows.Controls.Grid> pairs <xref:System.Windows.Controls.Canvas>d’automatisation sont des classes qui dérivent de , telles que , et des classes basées sur , tels que et .  
  
 La <xref:System.Windows.Controls.Control> classe de base n’a pas de classe de pairs correspondante. Si vous avez besoin d’une classe de <xref:System.Windows.Controls.Control>pairs pour correspondre à un <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>contrôle personnalisé qui dérive de , vous devriez tirer la classe de pairs personnalisé de .  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>Considérations relatives à la sécurité des homologues dérivés  
 Les homologues Automation doivent s’exécuter dans un environnement de confiance partielle. Le code dans l’assembly UIAutomationClient n’est pas configuré pour s’exécuter dans un environnement de confiance partielle et le code homologue Automation ne doit pas référencer cet assembly. Au lieu de cela, vous devez utiliser les classes de l’assembly UIAutomationTypes. Par exemple, vous <xref:System.Windows.Automation.AutomationElementIdentifiers> devez utiliser la classe à partir de l’assemblage <xref:System.Windows.Automation.AutomationElement> UIAutomationTypes, qui correspond à la classe dans l’assemblage UIAutomationClient. La démarche la plus sûre consiste à référencer l’assembly UIAutomationTypes dans le code homologue Automation.  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>Navigation homologue  
 Après avoir localisé un pair d’automatisation, le code en cours <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> peut <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> naviguer dans l’arbre de pairs en appelant l’objet et les méthodes. La navigation entre les éléments WPF dans un contrôle <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> est soutenue par la mise en œuvre de la méthode par le pair. Le système UI Automation appelle cette méthode pour générer une arborescence de sous-éléments contenus dans un contrôle ; par exemple, des éléments de liste dans une zone de liste. La <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> méthode par défaut traverse l’arbre visuel des éléments pour construire l’arbre des pairs d’automatisation. Les contrôles personnalisés contournent cette méthode pour exposer les éléments enfants aux clients Automation, en retournant les homologues Automation des éléments qui acheminent des informations ou qui permettent une interaction avec l’utilisateur.  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>Personnalisations dans un homologue dérivé  
 Toutes les classes <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> qui dérivent <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>et contiennent la méthode virtuelle protégée. WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> appelle pour obtenir l’objet pair d’automatisation pour chaque contrôle. Le code Automation peut utiliser l’homologue pour obtenir des informations sur les caractéristiques et les fonctionnalités d’un contrôle et pour simuler une utilisation interactive. Un contrôle personnalisé qui prend <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> en charge l’automatisation doit <xref:System.Windows.Automation.Peers.AutomationPeer>remplacer et retourner une instance d’une classe qui dérive de . Par exemple, si un contrôle <xref:System.Windows.Controls.Primitives.ButtonBase> personnalisé dérive de la <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> classe, <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>alors l’objet retourné par doit dériver de .  
  
 Lorsque vous implémentez un contrôle personnalisé, vous devez substituer les méthodes « Core » à partir de la classe homologue Automation de base qui décrivent le comportement unique et spécifique à votre contrôle personnalisé.  
  
### <a name="override-oncreateautomationpeer"></a>Substituer la méthode OnCreateAutomationPeer  
 Remplacer la <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> méthode de votre contrôle personnalisé afin qu’il renvoie votre <xref:System.Windows.Automation.Peers.AutomationPeer>objet fournisseur, qui doit dériver directement ou indirectement de .  
  
### <a name="override-getpattern"></a>Substituer la méthode GetPattern  
 Les homologues Automation simplifient certains aspects de l’implémentation des fournisseurs [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] côté serveur, fournisseurs, mais les homologues Automation d’un contrôle personnalisé doivent encore gérer les interfaces de modèle. Comme les fournisseurs non-WPF, les pairs prennent en <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> charge les modèles <xref:System.Windows.Automation.Provider.IInvokeProvider>de contrôle en fournissant des implémentations d’interfaces dans l’espace de nom, tels que . Les interfaces de modèle de contrôle peuvent être implémentées par l’homologue lui-même ou par un autre objet. La mise en <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> œuvre par le pair des retours de l’objet qui prend en charge le modèle spécifié. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]code appelle <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> la méthode et <xref:System.Windows.Automation.Peers.PatternInterface> spécifie une valeur de recensement. Votre remplacement <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> de devrait retourner l’objet qui implémente le modèle spécifié. Si votre contrôle n’a pas une mise en œuvre personnalisée <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> d’un modèle, vous pouvez appeler la mise en œuvre du type de base pour récupérer sa mise en œuvre ou nulle si le modèle n’est pas pris en charge pour ce type de contrôle. Par exemple, un contrôle NumericUpDown personnalisé peut être défini [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] à une <xref:System.Windows.Automation.Provider.IRangeValueProvider> valeur dans une plage, de sorte que son homologue implémenterait l’interface. L’exemple suivant montre comment <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> la méthode du pair <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> est remplacée pour répondre à une valeur.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Une <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> méthode peut également spécifier un sous-cadre en tant que fournisseur de motifs. Le code suivant <xref:System.Windows.Controls.ItemsControl> montre comment transfère la <xref:System.Windows.Controls.ScrollViewer> manipulation des modèles de défilement au pair de son contrôle interne.  
  
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
  
 Pour spécifier un sous-ensemble pour la manipulation des motifs, <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> ce code <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> obtient l’objet de sous-ensemble, crée un pair en utilisant la méthode, définit la propriété du nouveau pair au pair actuel, et renvoie le nouveau pair. Le <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> réglage sur un sous-cadre empêche le sous-cadre d’apparaître dans l’arbre de pair d’automatisation <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>et désigne tous les événements soulevés par le sous-cadre comme provenant du contrôle spécifié dans . Le <xref:System.Windows.Controls.ScrollViewer> contrôle n’apparaît pas dans l’arbre d’automatisation, et les <xref:System.Windows.Controls.ItemsControl> événements de défilement qu’il génère semblent provenir de l’objet.  
  
### <a name="override-core-methods"></a>Substituer les méthodes « Core »  
 Le code Automation obtient des informations sur votre contrôle en appelant des méthodes publiques de la classe homologue. Pour fournir des informations sur votre contrôle, substituez chaque méthode dont le nom se termine par « Core » lorsque l’implémentation de votre contrôle diffère de celle fournie par la classe homologue Automation de base. À tout le moins, <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> votre <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> contrôle doit implémenter les méthodes et les méthodes, comme le montre l’exemple suivant.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Votre mise <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> en œuvre <xref:System.Windows.Automation.ControlType> décrit votre contrôle en retournant une valeur. Bien que <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>vous puissiez revenir, vous devez retourner l’un des types de contrôle les plus spécifiques s’il décrit avec précision votre contrôle. Une valeur <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> de retour de nécessite [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]un [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] travail supplémentaire pour le fournisseur de mettre en œuvre, et les produits clients sont incapables d’anticiper la structure de contrôle, l’interaction clavier, et les modèles de contrôle possibles.  
  
 Implémentez les <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> méthodes et <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> les méthodes pour indiquer si votre contrôle contient du contenu de données ou remplit un rôle interactif dans l’interface utilisateur (ou les deux). Par défaut, ces deux méthodes retournent `true`. Ces paramètres facilitent l’utilisation des outils Automatisation, comme les lecteurs d’écran, qui peuvent utiliser ces méthodes pour filtrer l’arborescence Automation. Si <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> votre méthode transfère la manipulation de modèle à <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> un pair de sous-ensemble, la méthode du pair de sous-ensemble peut retourner fausse pour cacher le pair de sous-ensemble de l’arbre d’automatisation. Par exemple, le <xref:System.Windows.Controls.ListBox> défilement dans <xref:System.Windows.Controls.ScrollViewer>un est manipulé <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> par un <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> , <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> et le pair <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>d’automatisation pour est retourné par la méthode de la qui est associée à la . Par conséquent, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> la <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> `false`méthode des <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> retours , de sorte que le n’apparaît pas dans l’arbre d’automatisation.  
  
 Votre homologue Automation doit fournir des valeurs par défaut appropriées pour votre contrôle. Notez que XAML qui fait référence à votre contrôle <xref:System.Windows.Automation.AutomationProperties> peut remplacer vos implémentations par les pairs des méthodes de base en incluant des attributs. Par exemple, le code XAML suivant crée un bouton qui comporte deux propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] personnalisées.  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implémenter des fournisseurs de modèles  
 Les interfaces mises en œuvre par un fournisseur personnalisé <xref:System.Windows.Controls.Control>sont explicitement déclarées si l’élément propriétaire dérive directement de . Par exemple, le code suivant déclare <xref:System.Windows.Controls.Control> un pair pour un qui implémente une valeur de plage.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Si le contrôle de possession provient d’un <xref:System.Windows.Controls.Primitives.RangeBase>type spécifique de contrôle tel que , le pair peut être dérivé d’une classe équivalente de pairs dérivés. Dans ce cas, le <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>pair dériverait de <xref:System.Windows.Automation.Provider.IRangeValueProvider>, qui fournit une mise en œuvre de base de . Le code suivant illustre la déclaration de ce type d’homologue.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Par exemple, consultez le code source [C ou](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) qui implémente et consomme un contrôle personnalisé NumericUpDown.  
  
### <a name="raise-events"></a>Déclencher des événements  
 Les clients Automation peuvent s’abonner à des événements Automation. Les contrôles personnalisés doivent signaler <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> les modifications apportées à l’état de contrôle en appelant la méthode. De même, lorsqu’une valeur <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> de propriété change, appelez la méthode. Le code suivant montre comment obtenir l’objet homologue à partir du code de contrôle et appeler une méthode pour déclencher un événement. À des fins d’optimisation, le code détermine s’il existe des écouteurs pour ce type d’événement. Déclencher l’événement uniquement lorsqu’il y a des écouteurs évite les surcharges inutiles et permet au contrôle de rester réactif.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'UI Automation](../../ui-automation/ui-automation-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Contrôle personnalisé NumericUpDown sur GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Contrôle personnalisé NumericUpDown (Visual Basic) sur GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
