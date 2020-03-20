---
title: 'Optimisation des performances : liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186761"
---
# <a name="optimizing-performance-data-binding"></a>Optimisation des performances : liaison de données
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent pour les applications de présenter les données et d’interagir avec elles. Les éléments peuvent être liés aux données provenant d’une variété de sources de données sous la forme d’objets CLR et de XML.  
  
 Cette rubrique fournit des recommandations sur les performances de la liaison de données.  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>Comment les références de liaison de données sont résolues  
 Avant d’aborder les problèmes de performances de la liaison de données, il est utile d’explorer la façon dont le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] résout les références d’objet pour la liaison.  
  
 La source [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] d’une liaison de données peut être n’importe quel objet CLR. Vous pouvez vous lier aux propriétés, sous-propriétés ou indexateurs d’un objet CLR. Les références contraignantes sont résolues en utilisant <xref:System.ComponentModel.ICustomTypeDescriptor>soit Microsoft .NET Framework réflexion ou un . Voici trois méthodes permettant de résoudre les références d’objet pour la liaison.  
  
 La première méthode repose sur l’utilisation de la réflexion. Dans ce cas, l’objet <xref:System.Reflection.PropertyInfo> est utilisé pour découvrir les attributs de la propriété et donne accès aux métadonnées de propriété. Lors de <xref:System.ComponentModel.ICustomTypeDescriptor> l’utilisation de l’interface, le moteur de liaison de données utilise cette interface pour accéder aux valeurs de la propriété. L’interface <xref:System.ComponentModel.ICustomTypeDescriptor> est particulièrement utile dans les cas où l’objet n’a pas un ensemble statique de propriétés.  
  
 Les notifications de modification de propriété <xref:System.ComponentModel.INotifyPropertyChanged> peuvent être fournies soit en <xref:System.ComponentModel.TypeDescriptor>implémentant l’interface, soit en utilisant les notifications de modification associées au . Cependant, la stratégie préférée pour la mise <xref:System.ComponentModel.INotifyPropertyChanged>en œuvre des notifications de changement de propriété est d’utiliser .  
  
 Si l’objet source est un objet CLR et la [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propriété source est une propriété CLR, <xref:System.ComponentModel.TypeDescriptor>le moteur de liaison <xref:System.ComponentModel.PropertyDescriptor>de données doit d’abord utiliser la réflexion sur l’objet source pour obtenir le , puis requête pour un . Cette séquence d’opérations de réflexion peut s’avérer très fastidieuse du point de vue des performances.  
  
 La deuxième méthode de résolution des références d’objets <xref:System.ComponentModel.INotifyPropertyChanged> concerne un objet source CLR qui implémente l’interface, et une propriété source qui est une propriété CLR. Dans ce cas, le moteur de liaison de données applique la réflexion directement au type de source et obtient la propriété nécessaire. Ce n’est toujours pas la méthode optimale, mais elle est moins exigeante que la première méthode en termes de spécifications de la plage de travail.  
  
 La troisième méthode pour résoudre les références d’objet implique un objet source qui est une <xref:System.Windows.DependencyObject> propriété et une source qui est un <xref:System.Windows.DependencyProperty>. Dans ce cas, le moteur de liaison de données n’a pas besoin d’utiliser la réflexion. Au lieu de cela, le moteur de propriété et le moteur de liaison de données résolvent ensemble la référence de propriété de manière indépendante. Il s’agit de la méthode optimale pour résoudre les références d’objet utilisées pour la liaison de données.  
  
 Le tableau ci-dessous compare la <xref:System.Windows.Controls.TextBlock.Text%2A> vitesse des <xref:System.Windows.Controls.TextBlock> données liant la propriété de mille éléments à l’aide de ces trois méthodes.  
  
|**Liaison de la propriété Text d’un TextBlox**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|À la propriété d’un objet CLR|115|314|  
|À une propriété d’un objet CLR qui met en œuvre<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|À <xref:System.Windows.DependencyProperty> un <xref:System.Windows.DependencyObject>de .|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>Liaison à des objets CLR volumineux  
 Il y a un impact significatif sur les performances lorsque vous vous liez à un seul objet CLR avec des milliers de propriétés. Vous pouvez minimiser cet impact en divisant l’objet unique en plusieurs objets CLR avec moins de propriétés. Le tableau montre les temps de liaison et de rendu pour la liaison des données à un seul grand objet CLR par rapport à plusieurs objets plus petits.  
  
|**Liaison de données de 1 000 objets TextBlock**|**Temps de liaison (ms)**|**Temps de rendu -- liaison incluse (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Pour un objet CLR avec 1000 propriétés|950|1200|  
|À 1000 objets CLR avec une propriété|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>Liaison à un ItemsSource  
 Considérez un scénario dans lequel <xref:System.Collections.Generic.List%601> vous avez un objet CLR qui <xref:System.Windows.Controls.ListBox>détient une liste d’employés que vous souhaitez afficher dans un . Pour créer une correspondance entre ces deux objets, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vous lieriez votre liste d’employés à la propriété de la <xref:System.Windows.Controls.ListBox>. Or, il se trouve qu’un nouvel employé rejoint le groupe. Vous pourriez penser que pour insérer <xref:System.Windows.Controls.ListBox> cette nouvelle personne dans vos valeurs liées, vous ajouteriez simplement cette personne à votre liste d’employés et vous attendez à ce que ce changement soit reconnu automatiquement par le moteur de liaison de données. Cette hypothèse s’avérerait fausse; en réalité, le changement ne sera <xref:System.Windows.Controls.ListBox> pas reflété dans le automatiquement. C’est parce <xref:System.Collections.Generic.List%601> que l’objet CLR ne soulève pas automatiquement un événement modifié de collection. Afin d’obtenir <xref:System.Windows.Controls.ListBox> le de ramasser les changements, vous auriez à recréer votre <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> liste d’employés et de le remettre à la propriété de la <xref:System.Windows.Controls.ListBox>. Bien que cette solution fonctionne, elle a un fort impact sur les performances. Chaque fois que vous <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> réaffectez le <xref:System.Windows.Controls.ListBox> de à un nouvel objet, le premier jette ses éléments précédents et régénére toute sa liste. L’impact sur les performances <xref:System.Windows.Controls.ListBox> est amplifié <xref:System.Windows.DataTemplate>si vos cartes à un complexe .  
  
 Une solution très efficace à ce problème <xref:System.Collections.ObjectModel.ObservableCollection%601>est de faire de votre liste d’employés un . Un <xref:System.Collections.ObjectModel.ObservableCollection%601> objet soulève une notification de modification que le moteur de liaison de données peut recevoir. L’événement ajoute ou supprime <xref:System.Windows.Controls.ItemsControl> un élément d’un sans avoir besoin de régénérer la liste entière.  
  
 Le tableau ci-dessous montre le <xref:System.Windows.Controls.ListBox> temps qu’il faut pour mettre à jour le (avec la virtualisation de l’interface utilisateur désactivé) quand un élément est ajouté. Le nombre dans la première rangée représente le temps <xref:System.Collections.Generic.List%601> écoulé lorsque <xref:System.Windows.Controls.ListBox> l’objet CLR est lié à l’élément <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Le nombre dans la deuxième rangée représente le <xref:System.Collections.ObjectModel.ObservableCollection%601> temps écoulé <xref:System.Windows.Controls.ListBox> quand <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>un est lié à l’élément . Notez les économies <xref:System.Collections.ObjectModel.ObservableCollection%601> de temps importantes à l’aide de la stratégie de liaison de données.  
  
|**Liaison de données de la propriété ItemsSource**|**Temps de mise à jour pour 1 élément (ms)**|  
|--------------------------------------|---------------------------------------|  
|Vers un <xref:System.Collections.Generic.List%601> objet CLR|1 656|  
|À un<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Lier un objet IList à un objet ItemsControl non IEnumerable  
 Si vous avez le <xref:System.Collections.Generic.IList%601> choix <xref:System.Collections.IEnumerable> entre <xref:System.Windows.Controls.ItemsControl> la liaison <xref:System.Collections.Generic.IList%601> d’un ou d’un objet, choisissez l’objet. Liaison <xref:System.Collections.IEnumerable> à <xref:System.Windows.Controls.ItemsControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] une force pour <xref:System.Collections.Generic.IList%601> créer un objet d’emballage, ce qui signifie que vos performances sont affectées par les frais généraux inutiles d’un deuxième objet.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Ne convertissez pas des objets CLR en XML seulement à des fins de liaison de données.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vous permet de lier les données au contenu XML ; cependant, la liaison de données au contenu XML est plus lente que la liaison de données aux objets CLR. Ne convertissez pas les données des objets CLR en XML si le seul but est de la liaison des données.  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphisme 2D et acquisition d’images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d’application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Procédure pas à pas : mise en cache de données d’application dans une application WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
