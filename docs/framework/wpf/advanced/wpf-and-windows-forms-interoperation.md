---
title: WPF et Windows Forms interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187148"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Interopérabilité WPF et Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]et Windows Forms présentent deux architectures différentes pour créer des interfaces d’application. L’espace <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> nom offre des classes qui permettent des scénarios d’interopération communs. Les deux classes clés qui mettent <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost>en œuvre des capacités d’interopération sont et . Cette rubrique décrit les scénarios d’interopérabilité qui sont pris en charge et ceux qui ne le sont pas.  
  
> [!NOTE]
> Le scénario de *contrôle hybride* est examiné plus en détail. Un contrôle hybride contient un contrôle d’une technologie qui est lui-même imbriqué dans un contrôle d’une autre technologie. On parle aussi d’*interopérabilité imbriquée*. Un *contrôle hybride à plusieurs niveaux* a plusieurs niveaux d’imbrication de contrôle hybride. Un exemple d’interopération imbriquée à plusieurs niveaux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est un contrôle des formulaires Windows qui contient un contrôle, qui contient un autre contrôle des formulaires Windows. Les contrôles hybrides à plusieurs niveaux ne sont pas pris en charge.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hébergement des contrôles Windows Forms dans WPF  
 Les scénarios d’interopération suivants [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont pris en charge lorsqu’un contrôle héberge un contrôle Windows Forms :  
  
- Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle peut héberger un ou plusieurs contrôles Windows Forms à l’aide de XAML.  
  
- Il peut héberger un ou plusieurs contrôles Windows Forms à l’aide de code.  
  
- Il peut héberger des contrôles de conteneurs Windows Forms qui contiennent d’autres contrôles de formulaires Windows.  
  
- Il peut héberger un formulaire [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de master/détail avec un master et des détails Windows Forms.  
  
- Il peut héberger un formulaire de master/détail avec un maître et des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] détails Windows Forms.  
  
- Il peut héberger un ou plusieurs contrôles ActiveX.  
  
- Il peut héberger un ou plusieurs contrôles composites.  
  
- Il peut héberger des contrôles hybrides à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Il peut héberger des contrôles hybrides à l’aide de code.  
  
### <a name="layout-support"></a>Prise en charge de la disposition  
 La liste suivante décrit les <xref:System.Windows.Forms.Integration.WindowsFormsHost> limites connues lorsque l’élément tente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’intégrer son contrôle hébergé des formulaires Windows dans le système de mise en page.  
  
- Dans certains cas, les contrôles des formulaires Windows ne peuvent pas être redimensionnés, ou ne peuvent être dimensionnés qu’à des dimensions spécifiques. Par exemple, un <xref:System.Windows.Forms.ComboBox> contrôle Windows Forms ne prend en charge qu’une seule hauteur, qui est définie par la taille de la police du contrôle. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] une disposition dynamique, qui suppose que les éléments <xref:System.Windows.Forms.ComboBox> peuvent s’étirer verticalement, un contrôle hébergé ne s’étendra pas comme prévu.  
  
- Les commandes de formulaires Windows ne peuvent pas être tournées ou biaisées. Par exemple, lorsque vous faites pivoter votre interface utilisateur de 90 degrés, les commandes hébergées de formulaires Windows maintiendront leur position verticale.  
  
- Dans la plupart des cas, les contrôles Windows Forms ne prennent pas en charge la mise à l’échelle proportionnelle. Les dimensions globales du contrôle sont mises à l’échelle, mais les contrôles enfants et les composants du contrôle risquent de ne pas être redimensionnés comme prévu. Cette limitation dépend de la façon dont chaque contrôle windows Forms prend en charge la mise à l’échelle.  
  
- Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous pouvez changer l’ordre de plan des éléments pour en contrôler la superposition. Un contrôle hébergé de formulaires Windows est dessiné dans un HWND séparé, ainsi il est toujours dessiné au-dessus des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments.  
  
- Windows Forms contrôle l’autoscalage basé sur la taille de la police. Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le changement de la taille de police ne redimensionne pas la disposition entière, mais peut entraîner le redimensionnement dynamique des éléments de façon individuelle.  
  
### <a name="ambient-properties"></a>Propriétés ambiantes  
 Certaines des propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ambiantes des contrôles ont des équivalents formulaires Windows. Ces propriétés ambiantes sont propagées aux commandes hébergées <xref:System.Windows.Forms.Integration.WindowsFormsHost> de formulaires Windows et exposées comme propriétés publiques sur le contrôle. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle traduit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chaque propriété ambiante dans son équivalent Windows Forms.  
  
 Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportement  
 Le tableau suivant décrit le comportement d’interopérabilité.  
  
|Comportement|Prise en charge|Non pris en charge|  
|--------------|---------------|-------------------|  
|Transparence|Le rendu de contrôle des formulaires Windows prend en charge la transparence. Le contexte du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle parent peut devenir l’arrière-plan des commandes hébergées de formulaires Windows.|Certains contrôles Windows Forms ne prennent pas en charge la transparence. Par exemple, <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ComboBox> les contrôles et les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ne seront pas transparents lorsqu’ils sont hébergés par .|  
|Tabulation|La commande d’onglets pour les contrôles Windows Forms hébergés est la même que lorsque ces contrôles sont hébergés dans une application basée sur windows Forms.<br /><br /> Le tabbing [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’un contrôle à un contrôle des formulaires Windows avec la clé TAB et les touches SHIFT-TAB fonctionne comme d’habitude.<br /><br /> Les formulaires Windows <xref:System.Windows.Forms.Control.TabStop%2A> qui `false` ont une valeur de propriété de ne reçoivent pas de mise au point lorsque l’utilisateur onglets à travers les contrôles.<br /><br /> - <xref:System.Windows.Forms.Integration.WindowsFormsHost> Chaque contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> a une valeur, <xref:System.Windows.Forms.Integration.WindowsFormsHost> qui détermine quand ce contrôle recevra la mise au point.<br />- Les commandes de formulaires Windows qui sont contenues à l’intérieur d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> conteneur suivent l’ordre spécifié par la <xref:System.Windows.Forms.Control.TabIndex%2A> propriété. L’utilisation de la tabulation à partir du dernier index de tabulation rend actif le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivant disponible. S’il n’existe aucun autre contrôle focalisant, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le tabbing retourne au premier contrôle des formulaires Windows dans l’ordre de l’onglet.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>les valeurs pour <xref:System.Windows.Forms.Integration.WindowsFormsHost> les contrôles à l’intérieur de <xref:System.Windows.Forms.Integration.WindowsFormsHost> la sont relatives aux contrôles Windows Forms frères et sœurs qui sont contenus dans le contrôle.<br />-   La tabulation respecte le comportement spécifique de chaque contrôle. Par exemple, appuyer sur <xref:System.Windows.Forms.TextBox> la clé <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> TAB dans `true` un contrôle qui a une valeur de propriété d’entre entrer un onglet dans la boîte de texte au lieu de déplacer la mise au point.|Non applicable.|  
|Navigation à l’aide des touches de direction|- La navigation avec <xref:System.Windows.Forms.Integration.WindowsFormsHost> des touches fléchées dans le contrôle est la même que dans un contrôle de conteneurs Windows Forms ordinaire: Les touches UP ARROW et LEFT ARROW sélectionnent le contrôle précédent, et les touches DOWN ARROW et RIGHT ARROW sélectionnent le contrôle suivant.<br />- Les touches UP ARROW et LEFT ARROW du <xref:System.Windows.Forms.Integration.WindowsFormsHost> premier contrôle contenu dans le contrôle effectuent la même action que le raccourci clavier SHIFT-TAB. S’il y [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> focalisable, la mise au point sort du contrôle. Ce comportement diffère du <xref:System.Windows.Forms.ContainerControl> comportement standard en ce qu’aucun emballage au dernier contrôle ne se produit. Si aucun autre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle focalisable n’existe, le focus retourne au dernier contrôle des formulaires Windows dans l’ordre d’onglet.<br />- Les touches DOWN ARROW et RIGHT ARROW du <xref:System.Windows.Forms.Integration.WindowsFormsHost> dernier contrôle contenu dans le contrôle effectuent la même action que la clé TAB. S’il y [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> focalisable, la mise au point sort du contrôle. Ce comportement diffère du <xref:System.Windows.Forms.ContainerControl> comportement standard en ce qu’aucun emballage au premier contrôle ne se produit. Si aucun autre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle focalisable n’existe, le focus retourne au premier contrôle des formulaires Windows dans l’ordre de l’onglet.|Non applicable.|  
|Accélérateurs|Les accélérateurs fonctionnent normalement, sauf indication contraire dans la colonne « Non pris en charge ».|Les accélérateurs en double entre les technologies ne fonctionnent pas comme des accélérateurs en double standard. Lorsqu’un accélérateur est dupliqué sur toutes les technologies, avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au moins un sur un contrôle windows Forms et l’autre sur un contrôle, le contrôle des formulaires Windows reçoit toujours l’accélérateur. Le focus ne bascule pas entre les contrôles quand l’accélérateur en double est utilisé.|  
|Touches de raccourci|Les touches de raccourci fonctionnent normalement, sauf indication contraire dans la colonne « Non pris en charge ».|- Windows Forms clés raccourci qui sont manipulés au stade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de prétraitement toujours prendre le pas sur les touches raccourci. Par exemple, si <xref:System.Windows.Forms.ToolStrip> vous avez un contrôle avec des touches de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] raccourci CTRL-S définies, et qu’il y a une commande liée à CTRL-S, le <xref:System.Windows.Forms.ToolStrip> gestionnaire de contrôle est toujours invoqué en premier, quelle que soit la mise au point.<br />- Windows Forms clés raccourci qui <xref:System.Windows.Forms.Control.KeyDown> sont traitées par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]l’événement sont traitées dernière en . Vous pouvez prévenir ce comportement en remplaçant la <xref:System.Windows.Forms.Control.IsInputKey%2A> méthode du <xref:System.Windows.Forms.Control.PreviewKeyDown> contrôle des formulaires Windows ou en manipulant l’événement. Retournez `true` <xref:System.Windows.Forms.Control.IsInputKey%2A> de la méthode ou <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> définissez `true` la <xref:System.Windows.Forms.Control.PreviewKeyDown> valeur de la propriété dans votre gestionnaire d’événement.|  
|AcceptsReturn, AcceptsTab et autre comportement spécifique d’un contrôle|Propriétés qui modifient le comportement du clavier par défaut fonctionnent <xref:System.Windows.Forms.Control.IsInputKey%2A> comme `true`d’habitude, en supposant que le contrôle des formulaires Windows remplace la méthode de retour .|Les contrôles Windows Forms qui modifient le comportement du clavier par défaut en manipulant l’événement <xref:System.Windows.Forms.Control.KeyDown> sont traités en dernier dans le contrôle de l’hôte. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Étant donné que ces contrôles sont traités en dernier, ils peuvent entraîner un comportement inattendu.|  
|Événements Enter et Leave|Lorsque l’accent n’est pas mis sur le contrôle de confinement, <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> les événements Enter and Leave sont soulevés comme d’habitude lorsque la mise au point change dans un seul contrôle.|Les événements Enter et Leave ne sont pas déclenchés quand les changements de focus suivants se produisent :<br /><br /> - De l’intérieur à l’extérieur d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle.<br />- De l’extérieur à l’intérieur d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle.<br />- En <xref:System.Windows.Forms.Integration.WindowsFormsHost> dehors d’un contrôle.<br />- D’un contrôle Windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> Forms hébergé <xref:System.Windows.Forms.Integration.ElementHost> dans un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>à un contrôle hébergé à l’intérieur de la même .|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les formulaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les technologies Windows supposent un modèle de concurrence à threads simples. Pendant le débogage, les appels aux objets de framework d’autres threads lèvent une exception pour appliquer cette exigence.|  
|Sécurité|Tous les scénarios d’interopérabilité nécessitent une confiance totale.|Aucun scénario d’interopérabilité n’est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d’accessibilité sont pris en charge. Les produits de technologie d’assistance fonctionnent correctement lorsqu’ils [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont utilisés pour des applications hybrides qui contiennent à la fois des formulaires Windows et des contrôles.|Non applicable.|  
|Presse-papiers|Toutes les opérations de Presse-papiers fonctionnent normalement, Cela comprend la coupe et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le coller entre les formulaires Windows et les contrôles.|Non applicable.|  
|Fonctionnalité glisser-déplacer|Toutes les opérations de glisser-déplacer fonctionnent normalement, Cela comprend les opérations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entre les formulaires Windows et les contrôles.|Non applicable.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hébergement des contrôles WPF dans Windows Forms  
 Les scénarios d’interopération suivants sont pris [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en charge lorsqu’un contrôle Windows Forms héberge un contrôle :  
  
- Hébergement d’un ou de plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de code.  
  
- Association d’une feuille de propriétés avec un ou plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés.  
  
- Hébergement d’une ou de plusieurs pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un formulaire.  
  
- Démarrage d’une fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hébergement d’un formulaire de master/détail avec un maître et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des détails Windows Forms.  
  
- Hébergement d’un formulaire [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de master/détail avec un master et Windows Forms détails.  
  
- Hébergement de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personnalisés.  
  
- Hébergement de contrôles hybrides.  
  
### <a name="ambient-properties"></a>Propriétés ambiantes  
 Certaines des propriétés ambiantes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des contrôles Windows Forms ont des équivalents. Ces propriétés ambiantes sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propagées aux commandes hébergées et exposées comme propriétés publiques sur le <xref:System.Windows.Forms.Integration.ElementHost> contrôle. Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle traduit chaque propriété ambiante Windows Forms à son [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] équivalent.  
  
 Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportement  
 Le tableau suivant décrit le comportement d’interopérabilité.  
  
|Comportement|Prise en charge|Non pris en charge|  
|--------------|---------------|-------------------|  
|Transparence|Le rendu d’un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la transparence. Le contexte du contrôle parent des formulaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows peut devenir l’arrière-plan des commandes hébergées.|Non applicable.|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les formulaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les technologies Windows supposent un modèle de concurrence à threads simples. Pendant le débogage, les appels aux objets de framework d’autres threads lèvent une exception pour appliquer cette exigence.|  
|Sécurité|Tous les scénarios d’interopérabilité nécessitent une confiance totale.|Aucun scénario d’interopérabilité n’est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d’accessibilité sont pris en charge. Les produits de technologie d’assistance fonctionnent correctement lorsqu’ils [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont utilisés pour des applications hybrides qui contiennent à la fois des formulaires Windows et des contrôles.|Non applicable.|  
|Presse-papiers|Toutes les opérations de Presse-papiers fonctionnent normalement, Cela comprend la coupe et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le coller entre les formulaires Windows et les contrôles.|Non applicable.|  
|Fonctionnalité glisser-déplacer|Toutes les opérations de glisser-déplacer fonctionnent normalement, Cela comprend les opérations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entre les formulaires Windows et les contrôles.|Non applicable.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
