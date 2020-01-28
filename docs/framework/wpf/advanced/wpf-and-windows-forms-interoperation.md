---
title: WPF et Windows Forms Interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 2dc2ea10ce8f723a0ee34c4774253e1357ba6afa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735118"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Interopérabilité WPF et Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] présentent deux architectures différentes pour créer des interfaces d’application. L’espace de noms <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> fournit des classes qui permettent des scénarios d’interopérabilité courants. Les deux classes clés qui implémentent les fonctionnalités d’interopérabilité sont <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost>. Cette rubrique décrit les scénarios d’interopérabilité qui sont pris en charge et ceux qui ne le sont pas.  
  
> [!NOTE]
> Le scénario de *contrôle hybride* est examiné plus en détail. Un contrôle hybride contient un contrôle d’une technologie qui est lui-même imbriqué dans un contrôle d’une autre technologie. On parle aussi d’*interopérabilité imbriquée*. Un *contrôle hybride à plusieurs niveaux* a plusieurs niveaux d’imbrication de contrôle hybride. Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contenant un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui contient à son tour un autre contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est un exemple d’interopérabilité imbriquée à plusieurs niveaux. Les contrôles hybrides à plusieurs niveaux ne sont pas pris en charge.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hébergement des contrôles Windows Forms dans WPF  
 Les scénarios d’interopérabilité suivants sont pris en charge lorsqu’un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberge un contrôle Windows Forms :  
  
- Le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut héberger un ou plusieurs contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide de XAML.  
  
- Il peut héberger un ou plusieurs contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide de code.  
  
- Il peut héberger des contrôles conteneurs [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui contiennent d’autres contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
- Il peut héberger un formulaire maître/détail avec un maître [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des détails [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
- Il peut héberger un formulaire maître/détail avec un maître [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des détails [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Il peut héberger un ou plusieurs contrôles ActiveX.  
  
- Il peut héberger un ou plusieurs contrôles composites.  
  
- Il peut héberger des contrôles hybrides à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Il peut héberger des contrôles hybrides à l’aide de code.  
  
### <a name="layout-support"></a>Prise en charge de la disposition  
 La liste suivante décrit les limitations connues lorsque l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> tente d’intégrer son contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Dans certains cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas être redimensionnés, ou peuvent l’être uniquement à des dimensions particulières. Par exemple, un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> ne prend en charge qu’une seule hauteur, définie par la taille de police du contrôle. Dans une disposition dynamique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui suppose que les éléments peuvent être étirés verticalement, un contrôle <xref:System.Windows.Forms.ComboBox> hébergé ne s’étire pas comme prévu.  
  
- Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas faire l’objet d’une rotation ou d’une inclinaison. Par exemple, si vous faites pivoter une interface utilisateur de 90 degrés, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés restent dans leur position droite.  
  
- Dans la plupart des cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la mise à l’échelle proportionnelle. Les dimensions globales du contrôle sont mises à l’échelle, mais les contrôles enfants et les composants du contrôle risquent de ne pas être redimensionnés comme prévu. Cette limitation dépend de la prise en charge de la mise à l’échelle de chaque contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
- Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous pouvez changer l’ordre de plan des éléments pour en contrôler la superposition. Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est dessiné dans un HWND séparé. Ainsi, il s’affiche toujours par-dessus les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prennent en charge la mise à l’échelle automatique par rapport à la taille de police. Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le changement de la taille de police ne redimensionne pas la disposition entière, mais peut entraîner le redimensionnement dynamique des éléments de façon individuelle.  
  
### <a name="ambient-properties"></a>Propriétés ambiantes  
 Certaines propriétés ambiantes des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont des équivalents [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Ces propriétés ambiantes sont propagées aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés et exposées comme propriétés publiques sur le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> convertit chaque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriété ambiante en son équivalent [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportement  
 Le tableau suivant décrit le comportement d’interopérabilité.  
  
|Comportement|pris en charge|Non pris en charge|  
|--------------|---------------|-------------------|  
|Transparence|Le rendu d’un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prend en charge la transparence. L’arrière-plan du contrôle parent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut devenir l’arrière-plan de contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés.|Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la transparence. Par exemple, les contrôles <xref:System.Windows.Forms.TextBox> et <xref:System.Windows.Forms.ComboBox> ne sont pas transparents lorsqu’ils sont hébergés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Tabulation|L’ordre de tabulation des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés est le même que celui des contrôles hébergés dans une application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> La tabulation d’un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide de la touche Tab et des touches Maj+Tab fonctionne normalement.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles qui ont une valeur de propriété <xref:System.Windows.Forms.Control.TabStop%2A> de `false` ne reçoivent pas le focus lorsque l’utilisateur passe d’un onglet à l’autres contrôles.<br /><br /> -Chaque contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> a une valeur de <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>, qui détermine quand ce <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle recevra le focus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles contenus dans un <xref:System.Windows.Forms.Integration.WindowsFormsHost> conteneur suivent l’ordre spécifié par la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>. L’utilisation de la tabulation à partir du dernier index de tabulation rend actif le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivant disponible. S’il n’y a pas d’autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant être actif, la tabulation retourne au premier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l’ordre de tabulation.<br />-   valeurs <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> pour les contrôles à l’intérieur du <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont relatives aux contrôles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] frères qui sont contenus dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-   La tabulation respecte le comportement spécifique de chaque contrôle. Par exemple, le fait d’appuyer sur la touche TAB dans un contrôle <xref:System.Windows.Forms.TextBox> qui a une valeur de propriété <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> de `true` entre un onglet dans la zone de texte au lieu de déplacer le focus.|Non applicable.|  
|Navigation à l’aide des touches de direction|-La navigation à l’aide des touches de direction dans le contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> est identique à celle d’un contrôle de conteneur ordinaire [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] : les touches haut et gauche permettent de sélectionner le contrôle précédent, et les touches de direction bas et droite sélectionnent le contrôle suivant.<br />-Les touches haut et gauche du premier contrôle contenu dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> effectuent la même action que le raccourci clavier MAJ + TAB. S’il existe un focus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle, le focus se déplace à l’extérieur du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ce comportement diffère du comportement de <xref:System.Windows.Forms.ContainerControl> standard dans le fait qu’aucun renvoi au dernier contrôle ne se produit. S’il n’y a pas d’autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant être actif, le focus retourne au dernier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l’ordre de tabulation.<br />-Les touches bas et droite du dernier contrôle contenu dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> effectuent la même action que la touche TAB. S’il existe un focus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle, le focus se déplace à l’extérieur du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ce comportement diffère du comportement de <xref:System.Windows.Forms.ContainerControl> standard dans le fait qu’aucun renvoi au premier contrôle ne se produit. S’il n’y a pas d’autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant être actif, le focus retourne au premier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l’ordre de tabulation.|Non applicable.|  
|Accélérateurs|Les accélérateurs fonctionnent normalement, sauf indication contraire dans la colonne « Non pris en charge ».|Les accélérateurs en double entre les technologies ne fonctionnent pas comme des accélérateurs en double standard. Si un accélérateur est dupliqué entre des technologies, avec au moins un accélérateur sur un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et un autre sur un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] reçoit toujours l’accélérateur. Le focus ne bascule pas entre les contrôles quand l’accélérateur en double est utilisé.|  
|Touches de raccourci|Les touches de raccourci fonctionnent normalement, sauf indication contraire dans la colonne « Non pris en charge ».|-   Les touches de raccourci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] gérées lors de la phase de prétraitement ont toujours priorité sur les touches de raccourci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, si vous avez défini un contrôle de <xref:System.Windows.Forms.ToolStrip> avec les touches de raccourci CTRL + S et qu’une commande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est liée à CTRL + S, le gestionnaire de contrôle <xref:System.Windows.Forms.ToolStrip> est toujours appelé en premier, quel que soit le focus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] touches de raccourci gérées par l’événement <xref:System.Windows.Forms.Control.KeyDown> sont traitées en dernier dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vous pouvez empêcher ce comportement en substituant la méthode de <xref:System.Windows.Forms.Control.IsInputKey%2A> du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou en gérant l’événement <xref:System.Windows.Forms.Control.PreviewKeyDown>. Retournez `true` à partir de la méthode <xref:System.Windows.Forms.Control.IsInputKey%2A> ou définissez la valeur de la propriété <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> sur `true` dans votre gestionnaire d’événements <xref:System.Windows.Forms.Control.PreviewKeyDown>.|  
|AcceptsReturn, AcceptsTab et autre comportement spécifique d’un contrôle|Les propriétés qui modifient le comportement du clavier par défaut fonctionnent comme d’habitude, en supposant que le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substitue la méthode <xref:System.Windows.Forms.Control.IsInputKey%2A> pour retourner `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles qui modifient le comportement du clavier par défaut en gérant l’événement <xref:System.Windows.Forms.Control.KeyDown> sont traités en dernier dans le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de l’hôte. Étant donné que ces contrôles sont traités en dernier, ils peuvent entraîner un comportement inattendu.|  
|Événements Enter et Leave|Lorsque le focus n’est pas dirigé vers le contrôle contenant <xref:System.Windows.Forms.Integration.ElementHost>, les événements Enter et Leave sont déclenchés comme d’habitude lorsque le focus est modifié dans un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> unique.|Les événements Enter et Leave ne sont pas déclenchés quand les changements de focus suivants se produisent :<br /><br /> -De l’intérieur vers l’extérieur d’un contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-De l’extérieur vers l’intérieur d’un contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-À l’extérieur d’un contrôle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-À partir d’un contrôle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> hébergé dans le même <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supposent l’utilisation d’un modèle concurrentiel à thread unique. Pendant le débogage, les appels aux objets de framework d’autres threads lèvent une exception pour appliquer cette exigence.|  
|Sécurité|Tous les scénarios d’interopérabilité nécessitent une confiance totale.|Aucun scénario d’interopérabilité n’est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d’accessibilité sont pris en charge. Les produits de technologie d’assistance fonctionnent correctement s’ils sont utilisés pour des applications hybrides qui contiennent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Presse-papiers|Toutes les opérations de Presse-papiers fonctionnent normalement, y compris les opérations de couper-coller entre des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Fonctionnalité glisser-déplacer|Toutes les opérations de glisser-déplacer fonctionnent normalement, y compris celles entre des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hébergement des contrôles WPF dans Windows Forms  
 Les scénarios d’interopérabilité suivants sont pris en charge lorsqu’un contrôle Windows Forms héberge un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
- Hébergement d’un ou de plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de code.  
  
- Association d’une feuille de propriétés avec un ou plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés.  
  
- Hébergement d’une ou de plusieurs pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un formulaire.  
  
- Démarrage d’une fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hébergement d’un formulaire maître/détail avec un maître [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des détails [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hébergement d’un formulaire maître/détail avec un maître [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des détails [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
- Hébergement de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personnalisés.  
  
- Hébergement de contrôles hybrides.  
  
### <a name="ambient-properties"></a>Propriétés ambiantes  
 Certaines propriétés ambiantes des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ont des équivalents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces propriétés ambiantes sont propagées aux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés et exposées comme propriétés publiques sur le contrôle <xref:System.Windows.Forms.Integration.ElementHost>. Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> convertit chaque [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriété ambiante en son équivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportement  
 Le tableau suivant décrit le comportement d’interopérabilité.  
  
|Comportement|pris en charge|Non pris en charge|  
|--------------|---------------|-------------------|  
|Transparence|Le rendu d’un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la transparence. L’arrière-plan du contrôle parent [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] peut devenir l’arrière-plan de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés.|Non applicable.|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supposent l’utilisation d’un modèle concurrentiel à thread unique. Pendant le débogage, les appels aux objets de framework d’autres threads lèvent une exception pour appliquer cette exigence.|  
|Sécurité|Tous les scénarios d’interopérabilité nécessitent une confiance totale.|Aucun scénario d’interopérabilité n’est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d’accessibilité sont pris en charge. Les produits de technologie d’assistance fonctionnent correctement s’ils sont utilisés pour des applications hybrides qui contiennent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Presse-papiers|Toutes les opérations de Presse-papiers fonctionnent normalement, y compris les opérations de couper-coller entre des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Fonctionnalité glisser-déplacer|Toutes les opérations de glisser-déplacer fonctionnent normalement, y compris celles entre des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
