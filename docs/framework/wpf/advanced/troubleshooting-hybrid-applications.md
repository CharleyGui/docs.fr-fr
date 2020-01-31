---
title: Dépannage des applications hybrides
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 7af110b9b00b080bf40bc9ee4b85aa293940bbc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794262"
---
# <a name="troubleshooting-hybrid-applications"></a>Dépannage des applications hybrides
<a name="introduction"></a>Cette rubrique répertorie certains problèmes courants qui peuvent se produire lors de la création d’applications hybrides qui utilisent à la fois [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms technologies.  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Chevauchement de contrôles  
 Les contrôles peuvent ne pas se chevaucher comme escompté. Windows Forms utilise un HWND distinct pour chaque contrôle. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un HWND pour tout le contenu d’une page. Cette différence d’implémentation provoque des comportements de chevauchement inattendus.  
  
 Un contrôle Windows Forms hébergé dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaît toujours au-dessus du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu hébergé dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost> s’affiche dans l’ordre de plan du contrôle <xref:System.Windows.Forms.Integration.ElementHost>. Il est possible de se chevaucher <xref:System.Windows.Forms.Integration.ElementHost> contrôles, mais le contenu du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé ne combine pas ou n’interagit pas.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Propriété enfant  
 Les classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> peuvent héberger un seul élément ou contrôle enfant. Pour héberger plusieurs contrôles ou éléments, vous devez utiliser un conteneur comme contenu enfant. Par exemple, vous pouvez ajouter Windows Forms contrôles Button et case à cocher à un contrôle <xref:System.Windows.Forms.Panel?displayProperty=nameWithType>, puis affecter le panneau à la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> d’un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Toutefois, vous ne pouvez pas ajouter les contrôles Button et case à cocher séparément au même contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Mise à l'échelle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms ont des modèles de mise à l’échelle différents. Certaines transformations de mise à l’échelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont significatives pour les contrôles de Windows Forms, contrairement à d’autres. Par exemple, la mise à l’échelle d’un contrôle Windows Forms sur 0 fonctionnera, mais si vous essayez de redimensionner le même contrôle sur une valeur différente de zéro, la taille du contrôle reste 0. Pour plus d’informations, consultez [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adaptateur  
 Il peut y avoir une confusion lors de l’utilisation des classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost>, car elles incluent un conteneur masqué. Les classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> ont un conteneur masqué, appelé *adaptateur*, qu’ils utilisent pour héberger du contenu. Pour l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, l’adaptateur dérive de la classe <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>. Pour le contrôle <xref:System.Windows.Forms.Integration.ElementHost>, l’adaptateur dérive de l’élément <xref:System.Windows.Controls.DockPanel>. Quand vous voyez des références à l’adaptateur dans d’autres rubriques d’interopérabilité, c’est de ce conteneur qu’il est question.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Imbrication  
 L’imbrication d’un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> à l’intérieur d’un contrôle <xref:System.Windows.Forms.Integration.ElementHost> n’est pas prise en charge. L’imbrication d’un contrôle <xref:System.Windows.Forms.Integration.ElementHost> à l’intérieur d’un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n’est pas non plus prise en charge.  
  
<a name="focus"></a>   
## <a name="focus"></a>Focus  
 Le focus fonctionne différemment dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms, ce qui signifie que des problèmes de focus peuvent se produire dans une application hybride. Par exemple, si vous avez le focus à l’intérieur d’un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> et que vous réduisez et restaurez la page ou que vous affichez une boîte de dialogue modale, vous risquez de perdre le focus à l’intérieur de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> a encore le focus, mais le contrôle qu’il contient peut ne pas l’être.  
  
 La validation des données est également affectée par le focus. La validation fonctionne dans un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, mais elle ne fonctionne pas lorsque vous utilisez la touche Tab pour sortir de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> ou entre deux éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> différents.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mappage de propriétés  
 Certains mappages de propriétés requièrent une interprétation complète pour relier des implémentations différentes entre les technologies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms. Les mappages de propriétés permettent à votre code de réagir aux changements de polices, de couleurs et d’autres propriétés. En général, les mappages de propriétés écoutent soit des événements *Property*Changed, soit des appels On*Property*Changed, et définissent des propriétés appropriées sur le contrôle enfant ou son adaptateur. Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Propriétés de disposition sur le contenu hébergé  
 Lorsque la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> est affectée, plusieurs propriétés relatives à la disposition sur le contenu hébergé sont définies automatiquement. La modification de ces propriétés peut provoquer des comportements de disposition inattendus.  
  
 Votre contenu hébergé est ancré pour remplir le <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> parent. Pour activer ce comportement de remplissage, plusieurs propriétés sont définies quand vous définissez la propriété enfant. Le tableau suivant répertorie les propriétés de contenu définies par les classes <xref:System.Windows.Forms.Integration.ElementHost> et <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
|Classe hôte|Propriétés de contenu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Ne définissez pas ces propriétés directement sur le contenu hébergé. Pour plus d’informations, consultez [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Applications de navigation  
 Les applications de navigation peuvent ne pas tenir à jour l’état utilisateur. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> recrée ses contrôles lorsqu’il est utilisé dans une application de navigation. La recréation de contrôles enfants se produit lorsque l’utilisateur quitte la page qui héberge l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, puis y retourne. Tout contenu qui a été tapé par l’utilisateur sera perdu.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Interopérabilité des boucles de messages  
 Lors de l’utilisation de Windows Forms boucles de messages, les messages peuvent ne pas être traités comme prévu. La méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> est appelée par le constructeur <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Cette méthode ajoute un filtre de messages à la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ce filtre appelle la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> si un <xref:System.Windows.Forms.Control?displayProperty=nameWithType> était la cible du message et traduit/distribue le message.  
  
 Si vous affichez un <xref:System.Windows.Window> dans une boucle de messages Windows Forms avec <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, vous ne pouvez rien taper sauf si vous appelez la méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>. La méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> prend un <xref:System.Windows.Window> et ajoute un <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, qui redirige les messages liés aux clés vers la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez [Architecture d’entrée pour l’interopérabilité entre Windows Forms et WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Opacité et superposition  
 La classe <xref:System.Windows.Interop.HwndHost> ne prend pas en charge la superposition. Cela signifie que la définition de la propriété <xref:System.Windows.UIElement.Opacity%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n’a aucun effet, et aucune fusion n’a lieu avec d’autres fenêtres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui ont <xref:System.Windows.Window.AllowsTransparency%2A> ayant la valeur `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Suppression  
 Le fait de ne pas supprimer correctement les classes peut entraîner une fuite des ressources. Dans vos applications hybrides, assurez-vous que les classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> sont supprimées, ou que vous pouvez provoquer des fuites de ressources. Windows Forms supprime <xref:System.Windows.Forms.Integration.ElementHost> contrôles quand son parent <xref:System.Windows.Forms.Form> non modal se ferme. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supprime les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> lorsque votre application s’arrête. Il est possible d’afficher un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dans un <xref:System.Windows.Window> dans une boucle de message Windows Forms. Dans ce cas, votre code peut ne pas être averti que votre application s’arrête.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Activation des styles visuels  
 Les styles visuels Microsoft Windows XP sur un contrôle de Windows Forms ne sont peut-être pas activés. La méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> est appelée dans le modèle pour une application Windows Forms. Bien que cette méthode ne soit pas appelée par défaut, si vous utilisez Visual Studio pour créer un projet, vous obtiendrez les styles visuels Microsoft Windows XP pour les contrôles, si la version 6,0 de Comctl32. dll est disponible. Vous devez appeler la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> avant que les handles soient créés sur le thread. Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Contrôles sous licence  
 Les contrôles de Windows Forms sous licence qui affichent des informations de licence dans une boîte de message à l’utilisateur peuvent entraîner un comportement inattendu pour une application hybride. Certains contrôles sous licence affichent une boîte de dialogue en réponse à la création de handle. Par exemple, un contrôle sous licence peut informer l’utilisateur qu’une licence est nécessaire ou que l’utilisateur n’a plus le droit qu’à trois utilisations du contrôle.  
  
 L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dérive de la classe <xref:System.Windows.Interop.HwndHost> et le handle du contrôle enfant est créé à l’intérieur de la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>. La classe <xref:System.Windows.Interop.HwndHost> n’autorise pas le traitement des messages dans la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>, mais l’affichage d’une boîte de dialogue entraîne l’envoi des messages. Pour activer ce scénario de licence, appelez la méthode <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> sur le contrôle avant de l’assigner en tant qu’enfant de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>Concepteur WPF  
 Vous pouvez concevoir votre contenu WPF à l’aide du Concepteur WPF pour Visual Studio. Les sections suivantes répertorient certains problèmes courants qui peuvent se produire lors de la création d’applications hybrides avec le Concepteur WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent est ignoré au moment du design  
 La propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> peut ne pas fonctionner comme prévu au moment du Design.  
  
 Si un contrôle WPF n’est pas sur un parent visible, le runtime WPF ignore la valeur <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>. La raison pour laquelle <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> peut être ignorée est due au fait que <xref:System.Windows.Forms.Integration.ElementHost> objet est créé dans une <xref:System.AppDomain>distincte. Toutefois, lorsque vous exécutez l’application, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> fonctionne comme prévu.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>La liste d’erreurs au moment du design apparaît quand le dossier obj est supprimé  
 Si vous supprimez le dossier obj, la liste d’erreurs au moment du design s’affiche.  
  
 Lorsque vous concevez à l’aide de <xref:System.Windows.Forms.Integration.ElementHost>, le Concepteur Windows Forms utilise des fichiers générés dans le dossier Debug ou Release dans le dossier obj de votre projet. Si vous supprimez ces fichiers, la liste d’erreurs au moment du design apparaît. Pour résoudre ce problème, regénérez votre projet. Pour plus d’informations, consultez [Erreurs au moment du design dans le Concepteur Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost et IME  
 Les contrôles WPF hébergés dans un <xref:System.Windows.Forms.Integration.ElementHost> ne prennent pas en charge la propriété <xref:System.Windows.Forms.Control.ImeMode%2A>. Les modifications apportées à <xref:System.Windows.Forms.Control.ImeMode%2A> seront ignorées par les contrôles hébergés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interopérabilité dans le Concepteur WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architecture d’entrée pour l’interopérabilité entre Windows Forms et WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Guide pratique pour activer des styles visuels dans une application hybride](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Erreurs au moment du design dans le Concepteur Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migration et interopérabilité](migration-and-interoperability.md)
