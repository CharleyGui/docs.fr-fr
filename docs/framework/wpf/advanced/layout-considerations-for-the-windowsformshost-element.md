---
title: Considérations sur la disposition de l'élément WindowsFormsHost
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 9f97639447284b792d52cf4aa25b81f584d7291a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787903"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Considérations sur la disposition de l'élément WindowsFormsHost
Cette rubrique décrit comment l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> interagit avec le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms prennent en charge une logique différente, mais similaire, pour le dimensionnement et le positionnement des éléments sur un formulaire ou une page. Lorsque vous créez une interface utilisateur hybride qui héberge des contrôles Windows Forms dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> intègre les deux schémas de disposition.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Différences de disposition entre WPF et Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise une disposition indépendante de la résolution. Toutes les dimensions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] disposition sont spécifiées à l’aide *de pixels indépendants du périphérique*. Un pixel indépendant du périphérique est d’une taille et une résolution indépendantes de 90-sixième, ce qui vous permet d’obtenir des résultats similaires, que vous soyez un moniteur 72 PPP ou une imprimante 19 200 ppp.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est également basé sur une *disposition dynamique*. Cela signifie qu’un élément de l’interface utilisateur se réorganise sur un formulaire ou une page en fonction de son contenu, de son conteneur de disposition parent et de la taille d’écran disponible. La disposition dynamique facilite la localisation en ajustant automatiquement la taille et la position des éléments d’interface utilisateur lorsque les chaînes qu’ils contiennent changent de longueur.  
  
 La disposition dans Windows Forms dépend du périphérique et est plus susceptible d’être statique. En règle générale, les contrôles Windows Forms sont positionnés de manière absolue sur un formulaire à l’aide des dimensions spécifiées en pixels matériels. Toutefois, Windows Forms prend en charge certaines fonctionnalités de disposition dynamique, comme indiqué dans le tableau suivant.  
  
|Fonctionnalité de disposition|Description|  
|--------------------|-----------------|  
|Redimensionnement automatique|Certaines Windows Forms contrôles se redimensionnent pour afficher correctement leur contenu. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](../../winforms/controls/autosize-property-overview.md).|  
|Ancrage et ancrage|Les contrôles Windows Forms prennent en charge le positionnement et le dimensionnement en fonction du conteneur parent. Pour plus d'informations, consultez les rubriques <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Échelle automatique|Les contrôles de conteneur se redimensionnent eux-mêmes et leurs enfants en fonction de la résolution du périphérique de sortie ou de la taille, en pixels, de la police de conteneur par défaut. Pour plus d’informations, consultez [mise à l’échelle automatique dans Windows Forms](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Conteneurs de disposition|Les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> réorganisent leurs contrôles enfants et leur taille en fonction de leur contenu.|  
  
## <a name="layout-limitations"></a>Limitations de la disposition  
 En général, les contrôles de Windows Forms ne peuvent pas être mis à l’échelle et transformés dans la mesure du possible dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La liste suivante décrit les limitations connues lorsque l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> tente d’intégrer son contrôle Windows Forms hébergé dans le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Dans certains cas, les contrôles Windows Forms ne peuvent pas être redimensionnés ou ne peuvent être dimensionnés que sur des dimensions spécifiques. Par exemple, un contrôle Windows Forms <xref:System.Windows.Forms.ComboBox> ne prend en charge qu’une seule hauteur, définie par la taille de police du contrôle. Dans une disposition dynamique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où les éléments peuvent être étirés verticalement, un contrôle <xref:System.Windows.Forms.ComboBox> hébergé ne s’étire pas comme prévu.  
  
- Vous ne pouvez pas faire pivoter ou incliner les contrôles Windows Forms. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> déclenche l’événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> si vous appliquez une transformation d’inclinaison ou de rotation. Si vous ne gérez pas l’événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, un <xref:System.InvalidOperationException> est déclenché.  
  
- Dans la plupart des cas, les contrôles Windows Forms ne prennent pas en charge la mise à l’échelle proportionnelle. Les dimensions globales du contrôle sont mises à l’échelle, mais les contrôles enfants et les composants du contrôle risquent de ne pas être redimensionnés comme prévu. Cette limitation dépend de la manière dont chaque contrôle de Windows Forms prend en charge la mise à l’échelle. En outre, vous ne pouvez pas mettre à l’échelle Windows Forms contrôles à une taille de 0 pixel.  
  
- Les contrôles Windows Forms prennent en charge la mise à l’échelle automatique, dans laquelle le formulaire se redimensionne automatiquement et ses contrôles en fonction de la taille de police. Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le changement de la taille de police ne redimensionne pas la disposition entière, mais peut entraîner le redimensionnement dynamique des éléments de façon individuelle.  
  
### <a name="z-order"></a>Ordre de plan  
 Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous pouvez changer l’ordre de plan des éléments pour en contrôler la superposition. Un contrôle Windows Forms hébergé est dessiné dans un HWND distinct ; il est donc toujours dessiné par-dessus les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Un contrôle Windows Forms hébergé est également dessiné en plus de tout élément <xref:System.Windows.Documents.Adorner>.  
  
## <a name="layout-behavior"></a>Comportement de disposition  
 Les sections suivantes décrivent des aspects spécifiques du comportement de disposition lors de l’hébergement de contrôles Windows Forms dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Mise à l’échelle, conversion d’unités et indépendance des appareils  
 Chaque fois que l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> effectue des opérations impliquant des dimensions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et Windows Forms, deux systèmes de coordonnées sont impliqués : les pixels indépendants du périphérique pour les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les pixels matériels pour Windows Forms. Par conséquent, vous devez appliquer les conversions d’unité et de mise à l’échelle appropriées pour obtenir une disposition cohérente.  
  
 La conversion entre les systèmes de coordonnées dépend de la résolution de l’appareil en cours et des transformations de disposition ou de rendu appliquées à l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> ou à ses ancêtres.  
  
 Si le périphérique de sortie est 96 ppp et qu’aucune mise à l’échelle n’a été appliquée à l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, un pixel indépendant du périphérique est égal à un pixel matériel.  
  
 Tous les autres cas nécessitent la mise à l’échelle du système de coordonnées. Le contrôle hébergé n’est pas redimensionné. Au lieu de cela, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> tente de mettre à l’échelle le contrôle hébergé et tous ses contrôles enfants. Étant donné que Windows Forms ne prend pas entièrement en charge la mise à l’échelle, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est mis à l’échelle au degré pris en charge par les contrôles particuliers.  
  
 Substituez la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> pour fournir un comportement de mise à l’échelle personnalisé pour le contrôle Windows Forms hébergé.  
  
 En plus de la mise à l’échelle, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> gère les cas d’arrondi et de dépassement de capacité comme décrit dans le tableau suivant.  
  
|Problème de conversion|Description|  
|----------------------|-----------------|  
|Arrondi|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dimensions de pixel indépendantes du périphérique sont spécifiées comme `double`et Windows Forms dimensions de pixel matériel sont spécifiées comme `int`. Dans les cas où les dimensions basées sur `double`sont converties en dimensions `int`es, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise l’arrondi standard, de sorte que les valeurs fractionnaires inférieures à 0,5 soient arrondies à 0.|  
|Dépassement|Lorsque l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> convertit `double` valeurs en `int` valeurs, le dépassement de capacité est possible. Les valeurs supérieures à <xref:System.Int32.MaxValue> sont définies sur <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Propriétés relatives à la disposition  
 Les propriétés qui contrôlent le comportement de disposition dans les contrôles Windows Forms et les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont mappées de manière appropriée par l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Pour plus d’informations, consultez [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Modifications de disposition dans le contrôle hébergé  
 Les modifications de disposition dans le contrôle de Windows Forms hébergé sont propagées vers [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour déclencher des mises à jour de disposition. La méthode <xref:System.Windows.UIElement.InvalidateMeasure%2A> sur <xref:System.Windows.Forms.Integration.WindowsFormsHost> garantit que les modifications de disposition dans le contrôle hébergé entraînent l’exécution du moteur de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="continuously-sized-windows-forms-controls"></a>Contrôles de Windows Forms dimensionnés en continu  
 Les contrôles Windows Forms qui prennent en charge la mise à l’échelle continue interagissent entièrement avec le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> comme d’habitude pour dimensionner et réorganiser le contrôle Windows Forms hébergé.  
  
### <a name="sizing-algorithm"></a>Algorithme de dimensionnement  
 L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise la procédure suivante pour dimensionner le contrôle hébergé :  
  
1. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> substitue les méthodes de <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et de <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  
  
2. Pour déterminer la taille du contrôle hébergé, la méthode <xref:System.Windows.FrameworkElement.MeasureOverride%2A> appelle la méthode <xref:System.Windows.Forms.Control.GetPreferredSize%2A> du contrôle hébergé avec une contrainte convertie à partir de la contrainte transmise à la méthode <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
3. La méthode <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> tente de définir le contrôle hébergé sur la contrainte de taille donnée.  
  
4. Si la propriété <xref:System.Windows.Forms.Control.Size%2A> du contrôle hébergé correspond à la contrainte spécifiée, le contrôle hébergé est dimensionné à la contrainte.  
  
 Si la propriété <xref:System.Windows.Forms.Control.Size%2A> ne correspond pas à la contrainte spécifiée, le contrôle hébergé ne prend pas en charge le dimensionnement continu. Par exemple, le contrôle <xref:System.Windows.Forms.MonthCalendar> autorise uniquement des tailles discrètes. Les tailles autorisées pour ce contrôle se composent d’entiers (représentant le nombre de mois) à la fois pour la hauteur et la largeur. Dans ce cas, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> se comporte comme suit :  
  
- Si la propriété <xref:System.Windows.Forms.Control.Size%2A> retourne une taille supérieure à la contrainte spécifiée, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> découpe le contrôle hébergé. La hauteur et la largeur sont gérées séparément, de sorte que le contrôle hébergé peut être coupé dans les deux sens.  
  
- Si la propriété <xref:System.Windows.Forms.Control.Size%2A> retourne une taille inférieure à la contrainte spécifiée, <xref:System.Windows.Forms.Integration.WindowsFormsHost> accepte cette valeur de taille et retourne la valeur au système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Procédure pas à pas : organisation des contrôles Windows Forms dans WPF](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Organiser des contrôles de Windows Forms dans WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Migration et interopérabilité](migration-and-interoperability.md)
