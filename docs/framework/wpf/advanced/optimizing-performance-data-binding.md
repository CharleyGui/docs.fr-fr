---
title: 'Optimisation des performances: Liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401458"
---
# <a name="optimizing-performance-data-binding"></a>Optimisation des performances: Liaison de données
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent pour les applications de présenter les données et d’interagir avec elles. Les éléments peuvent être liés à des données provenant de diverses sources de données sous la forme d’objets [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]CLR et.  
  
 Cette rubrique fournit des recommandations sur les performances de la liaison de données.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Comment les références de liaison de données sont résolues  
 Avant d’aborder les problèmes de performances de la liaison de données, il est utile d’explorer la façon dont le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] résout les références d’objet pour la liaison.  
  
 La source d’une [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] liaison de données peut être n’importe quel objet CLR. Vous pouvez lier des propriétés, des sous-propriétés ou des indexeurs d’un objet CLR. Les références de liaison sont résolues à l’aide de la réflexion <xref:System.ComponentModel.ICustomTypeDescriptor>Microsoft .NET Framework ou d’un. Voici trois méthodes permettant de résoudre les références d’objet pour la liaison.  
  
 La première méthode repose sur l’utilisation de la réflexion. Dans ce cas, l' <xref:System.Reflection.PropertyInfo> objet est utilisé pour découvrir les attributs de la propriété et fournit l’accès aux métadonnées de propriété. Lors de l' <xref:System.ComponentModel.ICustomTypeDescriptor> utilisation de l’interface, le moteur de liaison de données utilise cette interface pour accéder aux valeurs de propriété. L' <xref:System.ComponentModel.ICustomTypeDescriptor> interface est particulièrement utile dans les cas où l’objet n’a pas d’ensemble statique de propriétés.  
  
 Les notifications de modification de propriété peuvent être fournies <xref:System.ComponentModel.INotifyPropertyChanged> en implémentant l’interface ou en utilisant les notifications de modification associées au. <xref:System.ComponentModel.TypeDescriptor> Toutefois, la stratégie par défaut pour l’implémentation des notifications de <xref:System.ComponentModel.INotifyPropertyChanged>modification de propriété consiste à utiliser.  
  
 Si l’objet source est un objet CLR et que la propriété source est une propriété CLR, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] le moteur de liaison de données doit d’abord utiliser la réflexion sur l’objet <xref:System.ComponentModel.TypeDescriptor>source pour obtenir le, <xref:System.ComponentModel.PropertyDescriptor>puis interroger pour obtenir. Cette séquence d’opérations de réflexion peut s’avérer très fastidieuse du point de vue des performances.  
  
 La deuxième méthode de résolution des références d’objet implique un objet CLR source qui implémente <xref:System.ComponentModel.INotifyPropertyChanged> l’interface et une propriété source qui est une propriété CLR. Dans ce cas, le moteur de liaison de données applique la réflexion directement au type de source et obtient la propriété nécessaire. Ce n’est toujours pas la méthode optimale, mais elle est moins exigeante que la première méthode en termes de spécifications de la plage de travail.  
  
 La troisième méthode de résolution des références d’objet implique un objet source qui est <xref:System.Windows.DependencyObject> un et une propriété source qui est <xref:System.Windows.DependencyProperty>un. Dans ce cas, le moteur de liaison de données n’a pas besoin d’utiliser la réflexion. Au lieu de cela, le moteur de propriété et le moteur de liaison de données résolvent ensemble la référence de propriété de manière indépendante. Il s’agit de la méthode optimale pour résoudre les références d’objet utilisées pour la liaison de données.  
  
 Le tableau ci-dessous compare la vitesse de liaison <xref:System.Windows.Controls.TextBlock.Text%2A> de données à <xref:System.Windows.Controls.TextBlock> la propriété des éléments 1000 à l’aide de ces trois méthodes.  
  
|**Liaison de la propriété Text d’un TextBlox**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|À une propriété d’un objet CLR|115|314|  
|À une propriété d’un objet CLR qui implémente<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|À un <xref:System.Windows.DependencyProperty> d’un <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Liaison à des objets CLR volumineux  
 Il y a un impact significatif sur les performances lorsque vous liez des données à un objet CLR unique avec des milliers de propriétés. Vous pouvez réduire cet impact en divisant l’objet unique en plusieurs objets CLR avec moins de propriétés. Le tableau indique les temps de liaison et de rendu pour la liaison de données à un seul objet CLR de grande taille par rapport à plusieurs objets plus petits.  
  
|**Liaison de données de 1 000 objets TextBlock**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|À un objet CLR avec des propriétés 1000|950|1 200|  
|Pour 1000 objets CLR avec une propriété|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Liaison à un ItemsSource  
 Imaginez un scénario dans lequel vous disposez d’un <xref:System.Collections.Generic.List%601> objet CLR qui contient une liste d’employés que vous souhaitez afficher dans un <xref:System.Windows.Controls.ListBox>. Pour créer une correspondance entre ces deux objets, vous devez lier votre liste d’employés à <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la propriété <xref:System.Windows.Controls.ListBox>de. Or, il se trouve qu’un nouvel employé rejoint le groupe. Vous pouvez penser que pour insérer cette nouvelle personne dans vos valeurs liées <xref:System.Windows.Controls.ListBox> , il vous suffit d’ajouter cette personne à votre liste d’employés et de vous attendre à ce que cette modification soit reconnue automatiquement par le moteur de liaison de données. Cette hypothèse s’est avérée fausse. en réalité, la modification ne sera pas reflétée <xref:System.Windows.Controls.ListBox> automatiquement. Cela est dû au fait <xref:System.Collections.Generic.List%601> que l’objet CLR ne déclenche pas automatiquement un événement de modification de collection. Afin d’obtenir le <xref:System.Windows.Controls.ListBox> pour récupérer les modifications, vous devez recréer votre liste d’employés et la rattacher à la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété du <xref:System.Windows.Controls.ListBox>. Bien que cette solution fonctionne, elle a un fort impact sur les performances. Chaque fois que vous réaffectez <xref:System.Windows.Controls.ListBox> le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de à un nouvel objet <xref:System.Windows.Controls.ListBox> , le premier rejette ses éléments précédents et régénère la liste entière. L’impact sur les performances est accru si <xref:System.Windows.Controls.ListBox> votre mappe à un <xref:System.Windows.DataTemplate>complexe.  
  
 Une solution très efficace à ce problème consiste à faire de votre employé une <xref:System.Collections.ObjectModel.ObservableCollection%601>liste. Un <xref:System.Collections.ObjectModel.ObservableCollection%601> objet déclenche une notification de modification que le moteur de liaison de données peut recevoir. L’événement ajoute ou supprime un élément d’un <xref:System.Windows.Controls.ItemsControl> sans qu’il soit nécessaire de régénérer l’intégralité de la liste.  
  
 Le tableau ci-dessous indique le temps nécessaire à la <xref:System.Windows.Controls.ListBox> mise à jour du (avec la virtualisation de l’interface utilisateur désactivée) lorsqu’un élément est ajouté. Le nombre de la première ligne représente le temps écoulé lorsque l’objet CLR <xref:System.Collections.Generic.List%601> est lié à <xref:System.Windows.Controls.ListBox> l’élément de <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Le nombre de la deuxième ligne représente le temps écoulé quand un <xref:System.Collections.ObjectModel.ObservableCollection%601> est lié au de <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>l' <xref:System.Windows.Controls.ListBox> élément. Notez les gains de temps significatifs <xref:System.Collections.ObjectModel.ObservableCollection%601> à l’aide de la stratégie de liaison de données.  
  
|**Liaison de données de la propriété ItemsSource**|**Temps de mise à jour pour 1 élément (ms)**|  
|--------------------------------------|---------------------------------------|  
|À un objet <xref:System.Collections.Generic.List%601> CLR|1 656|  
|À un<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Lier un objet IList à un objet ItemsControl non IEnumerable  
 Si vous avez le choix entre lier un <xref:System.Collections.Generic.IList%601> ou un <xref:System.Collections.IEnumerable> à un <xref:System.Windows.Controls.ItemsControl> objet, choisissez l' <xref:System.Collections.Generic.IList%601> objet. La <xref:System.Collections.IEnumerable> liaison à <xref:System.Windows.Controls.ItemsControl> une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] force pour créer un <xref:System.Collections.Generic.IList%601> objet wrapper, ce qui signifie que vos performances sont affectées par la surcharge inutile d’un deuxième objet.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Ne convertissez pas des objets CLR en XML seulement à des fins de liaison de données.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vous permet de lier des données [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] à du contenu; Toutefois, la [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] liaison de données au contenu est plus lente que la liaison de données aux objets CLR. Ne convertissez pas les données d’objet CLR en XML si le seul objectif est de lier les données.  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Procédure pas à pas : Mise en cache des données d’application dans une application WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
