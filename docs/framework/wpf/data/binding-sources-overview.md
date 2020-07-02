---
title: Vue d'ensemble des sources de liaison
description: Découvrez les types d’objets que vous pouvez utiliser comme source de liaison pour vos applications dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 11d19d904e632ca2c7c7795946d350d078c38e70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619622"
---
# <a name="binding-sources-overview"></a>Vue d'ensemble des sources de liaison
Dans la liaison de données, l’objet de source de liaison fait référence à l’objet à partir duquel vous obtenez des données. Cette rubrique décrit les types d’objets que vous pouvez utiliser comme source de liaison.

<a name="binding_sources"></a>
## <a name="binding-source-types"></a>Types de source de liaison
 La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge les types de source de liaison suivants :

|Source de liaison|Description|
|--------------------|-----------------|
|objets common language runtime (CLR)|Vous pouvez lier des propriétés publiques, des sous-propriétés, ainsi que des indexeurs, de n’importe quel objet common language runtime (CLR). Le moteur de liaison utilise la réflexion CLR pour récupérer les valeurs des propriétés. Les objets qui implémentent <xref:System.ComponentModel.ICustomTypeDescriptor> ou ont un inscrit <xref:System.ComponentModel.TypeDescriptionProvider> fonctionnent également avec le moteur de liaison.<br /><br /> Pour plus d’informations sur la façon d’implémenter une classe qui peut servir de source de liaison, consultez la page [Implémentation d’une classe pour la source de liaison](#classes) plus loin dans cette rubrique.|
|objets dynamiques|Vous pouvez lier aux propriétés et indexeurs disponibles d’un objet qui implémente l' <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Si vous pouvez accéder au membre dans le code, vous pouvez lier celui-ci. Par exemple, si un objet dynamique vous permet d’accéder à un membre dans le code via `someObjet.AProperty`, vous pouvez le lier en affectant le chemin de liaison `AProperty`.|
|Objets ADO.NET|Vous pouvez lier des objets ADO.NET, tels que <xref:System.Data.DataTable> . Le ADO.NET <xref:System.Data.DataView> implémente l' <xref:System.ComponentModel.IBindingList> interface, qui fournit des notifications de modification que le moteur de liaison écoute.|
|Objets XML|Vous pouvez lier et exécuter `XPath` des requêtes sur un <xref:System.Xml.XmlNode> , <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlElement> . Un moyen pratique d’accéder aux données XML qui est la source de liaison dans le balisage consiste à utiliser un <xref:System.Windows.Data.XmlDataProvider> objet. Pour plus d’informations, consultez [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Vous pouvez également effectuer une liaison à une <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> à une liaison avec les résultats de requêtes exécutées sur des objets de ces types à l’aide de LINQ to XML. Un moyen pratique d’utiliser LINQ to XML pour accéder aux données XML qui est la source de liaison dans le balisage consiste à utiliser un <xref:System.Windows.Data.ObjectDataProvider> objet. Pour plus d’informations, consultez [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|
|Objets <xref:System.Windows.DependencyObject>|Vous pouvez lier aux propriétés de dépendance de n’importe quel <xref:System.Windows.DependencyObject> . Pour obtenir un exemple, consultez [Lier les propriétés de deux contrôles](how-to-bind-the-properties-of-two-controls.md).|

<a name="classes"></a>
## <a name="implementing-a-class-for-the-binding-source"></a>Implémentation d’une classe pour la source de liaison
 Vous pouvez créer vos propres sources de liaison. Cette section décrit les éléments que vous devez connaître si vous implémentez une classe pour servir de source de liaison.

### <a name="providing-change-notifications"></a>Fournir des notifications de modification
 Si vous utilisez une <xref:System.Windows.Data.BindingMode.OneWay> liaison ou <xref:System.Windows.Data.BindingMode.TwoWay> (car vous souhaitez que votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se met à jour lorsque les propriétés de la source de liaison changent dynamiquement), vous devez implémenter un mécanisme de notification de modification de propriété approprié. Le mécanisme recommandé est que le CLR ou la classe dynamique implémente l' <xref:System.ComponentModel.INotifyPropertyChanged> interface. Pour plus d’informations, consultez [Implémenter la notification des modifications de propriétés](how-to-implement-property-change-notification.md).

 Si vous créez un objet CLR qui n’implémente pas <xref:System.ComponentModel.INotifyPropertyChanged> , vous devez disposer de votre propre système de notification pour vous assurer que les données utilisées dans une liaison restent à jour. Vous pouvez fournir des notifications de modification en prenant en charge le modèle `PropertyChanged` pour chaque propriété pour laquelle vous souhaitez obtenir des notifications de modification. Pour prendre en charge ce modèle, vous définissez un événement *PropertyName*Changed pour chaque propriété, où *PropertyName* est le nom de la propriété. Vous déclenchez l’événement chaque fois que la propriété est modifiée.

 Si votre source de liaison implémente un de ces mécanismes de notification, les mises à jour de la cible sont effectuées automatiquement. Si, pour une raison quelconque, votre source de liaison ne fournit pas les notifications de modification de propriété appropriées, vous avez la possibilité d’utiliser la <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> méthode pour mettre à jour la propriété cible explicitement.

### <a name="other-characteristics"></a>Autres caractéristiques
 La liste suivante fournit d’autres points importants à noter :

- Si vous souhaitez créer l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , la classe doit avoir un constructeur sans paramètre. Dans certains langages .NET, tels que C#, le constructeur sans paramètre peut être créé pour vous.

- Les propriétés que vous utilisez comme propriétés de source de liaison pour une liaison doivent être des propriétés publiques de votre classe. Les propriétés d’interface explicitement définies ne sont pas accessibles pour la liaison, tout comme les propriétés protégées, privées, internes ou virtuelles qui n’ont aucune implémentation de base.

- Vous ne pouvez pas lier des champs publics.

- Le type de la propriété déclarée dans votre classe est le type qui est passé à la liaison. Toutefois, le type utilisé par la liaison varie en fonction du type de propriété de cible de liaison, et non de la propriété de source de liaison. S’il existe une différence de type, vous souhaiterez écrire un convertisseur pour gérer la manière dont votre propriété personnalisée est initialement passée à la liaison. Pour plus d’informations, consultez <xref:System.Windows.Data.IValueConverter>.

<a name="objects"></a>
## <a name="using-entire-objects-as-a-binding-source"></a>Utilisation d’objets entiers comme source de liaison
 Vous pouvez utiliser un objet entier comme source de liaison. Vous pouvez spécifier une source de liaison à l’aide de la <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.FrameworkElement.DataContext%2A> propriété ou, puis fournir une déclaration de liaison vide : `{Binding}` . Les scénarios dans lesquels cela est utile incluent la liaison aux objets qui sont de type chaîne, la liaison à des objets ayant plusieurs propriétés qui vous intéressent ou une liaison à des objets de collection. Pour obtenir un exemple de liaison à un objet de collection entier, consultez [Utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

 Notez que vous devrez peut-être appliquer une logique personnalisée afin que les données soient significatives pour votre propriété cible liée aux données. La logique personnalisée peut se présenter sous la forme d’un convertisseur personnalisé (si la conversion de type par défaut n’existe pas) ou de <xref:System.Windows.DataTemplate> . Pour plus d’informations sur les convertisseurs, consultez la section Conversion de données de [Vue d'ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md). Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](data-templating-overview.md)des modèles de données.

<a name="collections"></a>
## <a name="using-collection-objects-as-a-binding-source"></a>Utilisation d’objets de collection comme source de liaison
 Souvent, l’objet que vous souhaitez utiliser comme source de liaison est une collection d’objets personnalisés. Chaque objet sert de source pour une instance d’une liaison répétée. Par exemple, vous pouvez avoir une collection `CustomerOrders` qui se compose d’objets `CustomerOrder` où votre application effectue une itération sur la collection pour déterminer le nombre de commandes et les données contenues dans chacune d’entre elles.

 Vous pouvez énumérer n’importe quelle collection qui implémente l' <xref:System.Collections.IEnumerable> interface. Toutefois, pour configurer des liaisons dynamiques afin que les insertions ou les suppressions dans la collection mettent à jour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatiquement, la collection doit implémenter l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Cette interface expose un événement qui doit être déclenché chaque fois que la collection sous-jacente est modifiée.

 La <xref:System.Collections.ObjectModel.ObservableCollection%601> classe est une implémentation intégrée d’une collection de données qui expose l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Les objets de données individuels dans la collection doivent satisfaire les spécifications décrites dans les sections précédentes. Pour obtenir un exemple, consultez [Créer et effectuer une liaison à un ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Avant d’implémenter votre propre collection, envisagez <xref:System.Collections.ObjectModel.ObservableCollection%601> d’utiliser ou une des classes de collection existantes, telles que <xref:System.Collections.Generic.List%601> , <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.ComponentModel.BindingList%601> , parmi de nombreuses autres.

 WPF ne lie jamais directement à la collection. Si vous spécifiez une collection comme source de liaison, WPF lie plutôt à la vue par défaut de la collection. Pour plus d’informations sur les vues par défaut, consultez [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).

 Si vous avez un scénario avancé et que vous souhaitez implémenter votre propre collection, envisagez d’utiliser l' <xref:System.Collections.IList> interface. <xref:System.Collections.IList>fournit une collection non générique d’objets accessibles individuellement par index, ce qui peut améliorer les performances.

<a name="permissions"></a>
## <a name="permission-requirements-in-data-binding"></a>Conditions d’autorisation dans la liaison de données
 Lors de la liaison de données, vous devez considérer le niveau de confiance de l’application. Le tableau suivant récapitule les types de propriété qui peuvent être liés dans une application qui s’exécute en mode confiance totale ou confiance partielle :

|Type de propriété<br /><br /> (tous les modificateurs d’accès)|Propriété d’objet dynamique|Propriété d’objet dynamique|Propriété CLR|Propriété CLR|Propriété de dépendance|Propriété de dépendance|
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|
|**Niveau de confiance**|**Confiance totale**|**Confiance partielle**|**Confiance totale**|**Confiance partielle**|**Confiance totale**|**Confiance partielle**|
|Classe publique|Oui|Oui|Oui|Oui|Oui|Oui|
|Classe non publique|Oui|Non|Oui|Non|Oui|Oui|

 Ce tableau décrit les points importants suivants à propos des exigences relatives à l’autorisation dans la liaison de données :

- Pour les propriétés CLR, la liaison de données fonctionne tant que le moteur de liaison est en mesure d’accéder à la propriété de source de liaison à l’aide de la réflexion. Sinon, le moteur de liaison émet un avertissement indiquant que la propriété ne peut pas être trouvée et utilise la valeur de secours ou la valeur par défaut, si elle est disponible.

- Vous pouvez lier des propriétés sur les objets dynamiques qui sont définies au moment de la compilation ou de l’exécution.

- Vous pouvez toujours lier aux propriétés de dépendance.

 L’exigence d’autorisation pour la liaison XML est similaire. Dans un bac à sable (sandbox) de confiance partielle, <xref:System.Windows.Data.XmlDataProvider> échoue lorsqu’il ne dispose pas des autorisations nécessaires pour accéder aux données spécifiées.

 Les objets avec un type anonyme sont internes. Vous pouvez lier des propriétés de types anonymes uniquement lors de l’exécution en confiance totale. Pour plus d’informations sur les types anonymes, consultez [Types anonymes (Guide de programmation C#)](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) ou [Types anonymes (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (pour Visual Basic).

 Pour plus d’informations sur la sécurité de confiance partielle, consultez [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Spécifier la source de liaison](how-to-specify-the-binding-source.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Optimiser les performances de liaison de données](../advanced/optimizing-performance-data-binding.md)
