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
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187328"
---
# <a name="troubleshooting-hybrid-applications"></a>Dépannage des applications hybrides
<a name="introduction"></a>Ce sujet énumère certains problèmes courants qui peuvent se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] produire lors de la rédaction d’applications hybrides, qui utilisent à la fois et Windows Forms technologies.  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>Chevauchement de contrôles  
 Les contrôles peuvent ne pas se chevaucher comme escompté. Windows Forms utilise un HWND séparé pour chaque contrôle. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un HWND pour tout le contenu d’une page. Cette différence d’implémentation provoque des comportements de chevauchement inattendus.  
  
 Un contrôle Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé apparaît toujours [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au-dessus du contenu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]contenu hébergé dans <xref:System.Windows.Forms.Integration.ElementHost> un contrôle apparaît à <xref:System.Windows.Forms.Integration.ElementHost> l’ordre z du contrôle. Il est possible <xref:System.Windows.Forms.Integration.ElementHost> de chevaucher [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les contrôles, mais le contenu hébergé ne se combine pas ou n’interagit pas.  
  
<a name="child_property"></a>
## <a name="child-property"></a>Propriété enfant  
 Les <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> classes et les classes ne peuvent accueillir qu’un seul contrôle ou élément pour l’enfant. Pour héberger plusieurs contrôles ou éléments, vous devez utiliser un conteneur comme contenu enfant. Par exemple, vous pouvez ajouter le bouton <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> Formulaires Windows et les <xref:System.Windows.Forms.Integration.WindowsFormsHost> commandes de <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> la case à cocher à un contrôle, puis affecter le panneau à la propriété d’un contrôle. Cependant, vous ne pouvez pas ajouter le bouton <xref:System.Windows.Forms.Integration.WindowsFormsHost> et les commandes de la case à cocher séparément au même contrôle.  
  
<a name="scaling"></a>
## <a name="scaling"></a>Mise à l'échelle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]et Windows Forms ont différents modèles de mise à l’échelle. Certaines [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] transformations à l’échelle sont significatives pour les contrôles windows Forms, mais d’autres ne le sont pas. Par exemple, la mise à l’échelle d’un contrôle windows Forms à 0 fonctionnera, mais si vous essayez d’échelle le même contrôle à une valeur non nulle, la taille du contrôle reste 0. Pour plus d’informations, consultez [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>
## <a name="adapter"></a>Adaptateur  
 Il peut y avoir <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> confusion lorsque vous travaillez dans les classes et les classes, parce qu’elles comprennent un conteneur caché. Les <xref:System.Windows.Forms.Integration.WindowsFormsHost> deux <xref:System.Windows.Forms.Integration.ElementHost> et les classes ont un conteneur caché, appelé un *adaptateur*, qu’ils utilisent pour héberger du contenu. Pour <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément, l’adaptateur dérive de la <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> classe. Pour <xref:System.Windows.Forms.Integration.ElementHost> le contrôle, l’adaptateur dérive de l’élément. <xref:System.Windows.Controls.DockPanel> Quand vous voyez des références à l’adaptateur dans d’autres rubriques d’interopérabilité, c’est de ce conteneur qu’il est question.  
  
<a name="nesting"></a>
## <a name="nesting"></a>Imbrication  
 La nidification d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément à l’intérieur d’un contrôle n’est <xref:System.Windows.Forms.Integration.ElementHost> pas prise en charge. La nidification d’un <xref:System.Windows.Forms.Integration.ElementHost> contrôle à l’intérieur d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément n’est pas non plus prise en charge.  
  
<a name="focus"></a>
## <a name="focus"></a>Focus  
 Focus fonctionne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] différemment dans et Windows Forms, ce qui signifie que les problèmes de mise au point peuvent se produire dans une application hybride. Par exemple, si vous <xref:System.Windows.Forms.Integration.WindowsFormsHost> vous concentrez à l’intérieur d’un élément, et que <xref:System.Windows.Forms.Integration.WindowsFormsHost> vous minimisez et restaurez la page ou affichez une boîte de dialogue modal, concentrez-vous à l’intérieur de l’élément. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> a toujours la concentration, mais le contrôle à l’intérieur peut ne pas.  
  
 La validation des données est également affectée par le focus. Validation fonctionne <xref:System.Windows.Forms.Integration.WindowsFormsHost> dans un élément, mais il ne <xref:System.Windows.Forms.Integration.WindowsFormsHost> fonctionne pas que <xref:System.Windows.Forms.Integration.WindowsFormsHost> vous onglet hors de l’élément, ou entre deux éléments différents.  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>Mappage de propriétés  
 Certaines cartographies immobilières nécessitent une interprétation approfondie pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] combler les implémentations différentes entre les technologies et windows Forms. Les mappages de propriétés permettent à votre code de réagir aux changements de polices, de couleurs et d’autres propriétés. En général, les mappages de propriétés écoutent soit des événements *Property*Changed, soit des appels On*Property*Changed, et définissent des propriétés appropriées sur le contrôle enfant ou son adaptateur. Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>Propriétés de disposition sur le contenu hébergé  
 Lorsque <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> la <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> propriété ou la propriété est attribuée, plusieurs propriétés liées à la mise en page sur le contenu hébergé sont définies automatiquement. La modification de ces propriétés peut provoquer des comportements de disposition inattendus.  
  
 Votre contenu hébergé est amarré pour remplir le <xref:System.Windows.Forms.Integration.WindowsFormsHost> parent et <xref:System.Windows.Forms.Integration.ElementHost> le parent. Pour activer ce comportement de remplissage, plusieurs propriétés sont définies quand vous définissez la propriété enfant. Le tableau suivant répertorie <xref:System.Windows.Forms.Integration.ElementHost> les <xref:System.Windows.Forms.Integration.WindowsFormsHost> propriétés de contenu définies par les classes et les classes.  
  
|Classe hôte|Propriétés de contenu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Ne définissez pas ces propriétés directement sur le contenu hébergé. Pour plus d’informations, consultez [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>Applications de navigation  
 Les applications de navigation peuvent ne pas tenir à jour l’état utilisateur. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> recrée ses commandes lorsqu’il est utilisé dans une application de navigation. Recréer les contrôles de l’enfant se produit lorsque <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’utilisateur navigue loin de la page hébergeant l’élément, puis y retourne. Tout contenu qui a été tapé par l’utilisateur sera perdu.  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>Interopérabilité des boucles de messages  
 Lorsque vous travaillez avec les boucles de messages Windows Forms, les messages peuvent ne pas être traités comme prévu. La <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> méthode est <xref:System.Windows.Forms.Integration.WindowsFormsHost> appelée par le constructeur. Cette méthode ajoute un filtre de messages à la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ce filtre <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> appelle la <xref:System.Windows.Forms.Control?displayProperty=nameWithType> méthode si a été la cible du message et traduit /dispatches le message.  
  
 Si vous <xref:System.Windows.Window> affichez un dans <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>une boucle de message Windows <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Forms avec , vous ne pouvez pas taper quoi que ce soit à moins que vous appelez la méthode. La <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> méthode <xref:System.Windows.Window> prend un <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>et ajoute un , qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] redirige les messages liés aux clés à la boucle de message. Pour plus d’informations, consultez [Architecture d’entrée pour l’interopérabilité entre Windows Forms et WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>Opacité et superposition  
 La <xref:System.Windows.Interop.HwndHost> classe ne prend pas en charge la superposition. Cela signifie que <xref:System.Windows.UIElement.Opacity%2A> le <xref:System.Windows.Forms.Integration.WindowsFormsHost> réglage de la propriété sur l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’a aucun effet, et aucun mélange ne se produira avec d’autres fenêtres qui ont <xref:System.Windows.Window.AllowsTransparency%2A> mis à `true`.  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 Le fait de ne pas supprimer correctement les classes peut entraîner une fuite des ressources. Dans vos applications hybrides, <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> assurez-vous que les classes et les classes sont éliminées, ou vous pourriez fuir des ressources. Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> dispose de contrôles lorsque <xref:System.Windows.Forms.Form> son parent non modal ferme. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dispose <xref:System.Windows.Forms.Integration.WindowsFormsHost> d’éléments lorsque votre demande s’arrête. Il est possible <xref:System.Windows.Forms.Integration.WindowsFormsHost> d’afficher <xref:System.Windows.Window> un élément dans une boucle de message Windows Forms. Dans ce cas, votre code peut ne pas être averti que votre application s’arrête.  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>Activation des styles visuels  
 Les styles visuels Microsoft Windows XP sur un contrôle Windows Forms peuvent ne pas être activés. La <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> méthode est appelée dans le modèle d’une application Windows Forms. Bien que cette méthode ne soit pas appelée par défaut, si vous utilisez Visual Studio pour créer un projet, vous obtiendrez des styles visuels Microsoft Windows XP pour les contrôles, si la version 6.0 de Comctl32.dll est disponible. Vous devez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> appeler la méthode avant que les poignées soient créées sur le thread. Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>Contrôles sous licence  
 Les formulaires Windows sous licence contrôlent les informations de licence affichées dans une boîte de message à l’utilisateur peut provoquer un comportement inattendu pour une application hybride. Certains contrôles sous licence affichent une boîte de dialogue en réponse à la création de handle. Par exemple, un contrôle sous licence peut informer l’utilisateur qu’une licence est nécessaire ou que l’utilisateur n’a plus le droit qu’à trois utilisations du contrôle.  
  
 L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dérive <xref:System.Windows.Interop.HwndHost> de la classe, et la poignée <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> du contrôle de l’enfant est créée à l’intérieur de la méthode. La <xref:System.Windows.Interop.HwndHost> classe ne permet pas de <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> traiter les messages dans la méthode, mais l’affichage d’une boîte de dialogue provoque l’envoi de messages. Pour activer ce scénario <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> de licence, appelez la <xref:System.Windows.Forms.Integration.WindowsFormsHost> méthode sur le contrôle avant de l’attribuer comme l’enfant de l’élément.  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>Concepteur WPF  
 Vous pouvez concevoir votre contenu WPF en utilisant le WPF Designer for Visual Studio. Les sections suivantes énumèrent certains problèmes courants qui peuvent se produire lors de la rédaction d’applications hybrides avec le concepteur WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent est ignoré au moment du design  
 La <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> propriété pourrait ne pas fonctionner comme prévu au moment de la conception.  
  
 Si un contrôle WPF n’est pas sur un parent <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> visible, le temps d’exécution WPF ignore la valeur. La raison <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> pour laquelle <xref:System.Windows.Forms.Integration.ElementHost> cela pourrait être <xref:System.AppDomain>ignoré est parce que l’objet est créé dans un séparé . Toutefois, lorsque vous exécutez l’application, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> fonctionne comme prévu.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>La liste d’erreurs au moment du design apparaît quand le dossier obj est supprimé  
 Si vous supprimez le dossier obj, la liste d’erreurs au moment du design s’affiche.  
  
 Lorsque vous <xref:System.Windows.Forms.Integration.ElementHost>concevez à l’aide, le concepteur de formulaires Windows utilise des fichiers générés dans le dossier Debug ou Release dans le dossier obj de votre projet. Si vous supprimez ces fichiers, la liste d’erreurs au moment du design apparaît. Pour résoudre ce problème, regénérez votre projet. Pour plus d’informations, consultez [Erreurs au moment du design dans le Concepteur Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost et IME  
 Les contrôles WPF <xref:System.Windows.Forms.Integration.ElementHost> hébergés dans <xref:System.Windows.Forms.Control.ImeMode%2A> un actuellement ne prennent pas en charge la propriété. Les <xref:System.Windows.Forms.Control.ImeMode%2A> modifications seront ignorées par les contrôles hébergés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interopérabilité avec le Concepteur WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architecture d’entrée pour l’interopérabilité entre Windows Forms et WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Guide pratique pour activer des styles visuels dans une application hybride](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Erreurs au moment du design dans le Concepteur Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migration et interopérabilité](migration-and-interoperability.md)
