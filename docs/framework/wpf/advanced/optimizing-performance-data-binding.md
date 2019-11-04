---
title: 'Optimisation des performances : liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 31fdc3c31c8792fea5f3e71dedb7370ebd63c98e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458548"
---
# <a name="optimizing-performance-data-binding"></a>Optimisation des performances : liaison de données
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent pour les applications de présenter les données et d’interagir avec elles. Les éléments peuvent être liés à des données provenant de diverses sources de données sous la forme d’objets CLR et de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Cette rubrique fournit des recommandations sur les performances de la liaison de données.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Comment les références de liaison de données sont résolues  
 Avant d’aborder les problèmes de performances de la liaison de données, il est utile d’explorer la façon dont le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] résout les références d’objet pour la liaison.  
  
 La source d’une liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut être n’importe quel objet CLR. Vous pouvez lier des propriétés, des sous-propriétés ou des indexeurs d’un objet CLR. Les références de liaison sont résolues à l’aide de la réflexion Microsoft .NET Framework ou d’une <xref:System.ComponentModel.ICustomTypeDescriptor>. Voici trois méthodes permettant de résoudre les références d’objet pour la liaison.  
  
 La première méthode repose sur l’utilisation de la réflexion. Dans ce cas, l’objet <xref:System.Reflection.PropertyInfo> est utilisé pour découvrir les attributs de la propriété et fournit l’accès aux métadonnées de propriété. Lors de l’utilisation de l’interface <xref:System.ComponentModel.ICustomTypeDescriptor>, le moteur de liaison de données utilise cette interface pour accéder aux valeurs de propriété. L’interface <xref:System.ComponentModel.ICustomTypeDescriptor> est particulièrement utile dans les cas où l’objet n’a pas d’ensemble statique de propriétés.  
  
 Les notifications de modification de propriété peuvent être fournies soit en implémentant l’interface <xref:System.ComponentModel.INotifyPropertyChanged>, soit en utilisant les notifications de modification associées à l' <xref:System.ComponentModel.TypeDescriptor>. Toutefois, la stratégie par défaut pour l’implémentation des notifications de modification de propriété consiste à utiliser <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Si l’objet source est un objet CLR et que la propriété source est une propriété CLR, le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] doit d’abord utiliser la réflexion sur l’objet source pour obtenir le <xref:System.ComponentModel.TypeDescriptor>, puis interroger un <xref:System.ComponentModel.PropertyDescriptor>. Cette séquence d’opérations de réflexion peut s’avérer très fastidieuse du point de vue des performances.  
  
 La deuxième méthode de résolution des références d’objet implique un objet CLR source qui implémente l’interface <xref:System.ComponentModel.INotifyPropertyChanged> et une propriété source qui est une propriété CLR. Dans ce cas, le moteur de liaison de données applique la réflexion directement au type de source et obtient la propriété nécessaire. Ce n’est toujours pas la méthode optimale, mais elle est moins exigeante que la première méthode en termes de spécifications de la plage de travail.  
  
 La troisième méthode pour résoudre les références d’objet implique un objet source qui est un <xref:System.Windows.DependencyObject> et une propriété source qui est un <xref:System.Windows.DependencyProperty>. Dans ce cas, le moteur de liaison de données n’a pas besoin d’utiliser la réflexion. Au lieu de cela, le moteur de propriété et le moteur de liaison de données résolvent ensemble la référence de propriété de manière indépendante. Il s’agit de la méthode optimale pour résoudre les références d’objet utilisées pour la liaison de données.  
  
 Le tableau ci-dessous compare la vitesse de liaison de données à la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de 1000 <xref:System.Windows.Controls.TextBlock> éléments à l’aide de ces trois méthodes.  
  
|**Liaison de la propriété Text d’un TextBlox**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|À une propriété d’un objet CLR|115|314|  
|À une propriété d’un objet CLR qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|À un <xref:System.Windows.DependencyProperty> d’un <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Liaison à des objets CLR volumineux  
 Il y a un impact significatif sur les performances lorsque vous liez des données à un objet CLR unique avec des milliers de propriétés. Vous pouvez réduire cet impact en divisant l’objet unique en plusieurs objets CLR avec moins de propriétés. Le tableau indique les temps de liaison et de rendu pour la liaison de données à un seul objet CLR de grande taille par rapport à plusieurs objets plus petits.  
  
|**Liaison de données de 1 000 objets TextBlock**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|À un objet CLR avec des propriétés 1000|950|1200|  
|Pour 1000 objets CLR avec une propriété|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Liaison à un ItemsSource  
 Imaginez un scénario dans lequel vous avez un objet CLR <xref:System.Collections.Generic.List%601> qui contient une liste d’employés que vous souhaitez afficher dans une <xref:System.Windows.Controls.ListBox>. Pour créer une correspondance entre ces deux objets, vous devez lier votre liste d’employés à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> du <xref:System.Windows.Controls.ListBox>. Or, il se trouve qu’un nouvel employé rejoint le groupe. Vous pensez peut-être que pour insérer cette nouvelle personne dans vos valeurs de <xref:System.Windows.Controls.ListBox> liées, il vous suffit d’ajouter cette personne à votre liste d’employés et de vous attendre à ce que cette modification soit reconnue automatiquement par le moteur de liaison de données. Cette hypothèse s’est avérée fausse. en réalité, la modification ne sera pas reflétée automatiquement dans la <xref:System.Windows.Controls.ListBox>. Cela est dû au fait que l’objet <xref:System.Collections.Generic.List%601> CLR ne déclenche pas automatiquement un événement de modification de collection. Pour que les <xref:System.Windows.Controls.ListBox> récupèrent les modifications, vous devez recréer votre liste d’employés et la rattacher à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de l' <xref:System.Windows.Controls.ListBox>. Bien que cette solution fonctionne, elle a un fort impact sur les performances. Chaque fois que vous réaffectez la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ListBox> à un nouvel objet, le <xref:System.Windows.Controls.ListBox> rejette d’abord ses éléments précédents et régénère la liste entière. L’impact sur les performances est accru si votre <xref:System.Windows.Controls.ListBox> est mappée à un <xref:System.Windows.DataTemplate>complexe.  
  
 Une solution très efficace à ce problème consiste à faire de votre employé une liste de <xref:System.Collections.ObjectModel.ObservableCollection%601>. Un objet <xref:System.Collections.ObjectModel.ObservableCollection%601> déclenche une notification de modification que le moteur de liaison de données peut recevoir. L’événement ajoute ou supprime un élément d’un <xref:System.Windows.Controls.ItemsControl> sans qu’il soit nécessaire de régénérer la liste entière.  
  
 Le tableau ci-dessous indique le temps nécessaire pour mettre à jour le <xref:System.Windows.Controls.ListBox> (avec la virtualisation de l’interface utilisateur désactivée) lorsqu’un élément est ajouté. Le nombre de la première ligne représente le temps écoulé lorsque l’objet <xref:System.Collections.Generic.List%601> CLR est lié au <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>de <xref:System.Windows.Controls.ListBox> élément. Le nombre de la deuxième ligne représente le temps écoulé quand un <xref:System.Collections.ObjectModel.ObservableCollection%601> est lié au <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>de l’élément de <xref:System.Windows.Controls.ListBox>. Notez les gains de temps significatifs à l’aide de la stratégie de liaison de données <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
|**Liaison de données de la propriété ItemsSource**|**Temps de mise à jour pour 1 élément (ms)**|  
|--------------------------------------|---------------------------------------|  
|À un objet de <xref:System.Collections.Generic.List%601> CLR|1 656|  
|À une <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Lier un objet IList à un objet ItemsControl non IEnumerable  
 Si vous avez le choix entre la liaison d’un <xref:System.Collections.Generic.IList%601> ou d’un <xref:System.Collections.IEnumerable> à un objet <xref:System.Windows.Controls.ItemsControl>, choisissez l’objet <xref:System.Collections.Generic.IList%601>. La liaison de <xref:System.Collections.IEnumerable> à un <xref:System.Windows.Controls.ItemsControl> force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à créer un wrapper <xref:System.Collections.Generic.IList%601> objet, ce qui signifie que vos performances sont affectées par la surcharge inutile d’un deuxième objet.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Ne convertissez pas des objets CLR en XML seulement à des fins de liaison de données.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de lier des données à [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] contenu ; Toutefois, la liaison de données à [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] contenu est plus lente que la liaison de données aux objets CLR. Ne convertissez pas les données d’objet CLR en XML si le seul objectif est de lier les données.  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Procédure pas à pas : mise en cache de données d’application dans une application WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
