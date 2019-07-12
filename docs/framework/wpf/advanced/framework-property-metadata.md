---
title: Métadonnées de propriété de framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 81c1941ffd95afb01dcb6ebda2634832a91cd876
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859847"
---
# <a name="framework-property-metadata"></a>Métadonnées de propriété de framework
Des options de métadonnées de propriété de framework sont signalées pour les propriétés des éléments objet considérés comme étant au niveau du framework WPF dans l’architecture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. En général la désignation de niveau infrastructure WPF implique de fonctionnalités telles que le rendu, la liaison de données, et la propriété ajustements du système par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] présentation API et les fichiers exécutables. Les métadonnées de propriété de framework sont interrogées par ces systèmes afin d’identifier les caractéristiques spécifiques aux fonctionnalités de propriétés d’un élément particulier.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous avez lu [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Vous devez également avoir lu [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Informations communiquées par les métadonnées de propriété de framework  
 Les métadonnées de propriété de framework peuvent être réparties dans les catégories suivantes :  
  
- Signalement des propriétés de disposition qui affectent un élément (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Vous pouvez définir ces indicateurs dans les métadonnées si la propriété affecte ces aspects respectifs, et si vous implémentez également la <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthodes dans votre classe pour fournir le comportement de rendu spécifique et des informations à la disposition système. En général, une telle implémentation vérifie la présence d’invalidations de propriété dans les propriétés de dépendance dont des propriétés de disposition avaient la valeur true dans les métadonnées de propriété, et seules ces invalidations font l’objet d’une demande de nouvelle passe de disposition.  
  
- Les propriétés de disposition qui affectent l’élément parent d’un élément (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Voici quelques exemples où ces indicateurs sont définis par défaut <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> et <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Par défaut, les propriétés de dépendance n’héritent pas de valeurs. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> permet à la voie d’héritage de se déplacer également dans une arborescence d’éléments visuels, ce qui est nécessaire pour certains scénarios de composition de contrôle.  
  
    > [!NOTE]
    >  Le terme « hérite » dans le contexte des valeurs de propriété revêt une signification spécifique pour les propriétés de dépendance ; il signifie que les éléments enfants peuvent hériter de la valeur de propriété de dépendance réelle des éléments parents grâce à une fonctionnalité au niveau du framework WPF du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette notion est donc sans rapport direct avec le type de code managé et l’héritage de membres par le biais de types dérivés. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).  
  
- Caractéristiques de liaison de données (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Par défaut, les propriétés de dépendance du framework prennent en charge la liaison de données avec un comportement de liaison unidirectionnel. Vous pouvez désactiver la liaison de données s’il n’y avait aucun scénario que ce soit (car ils sont destinés à être flexibles et extensibles, de nombreux exemples de telles propriétés dans la valeur par défaut ne sont pas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API). Vous pouvez définir une liaison bidirectionnelle par défaut pour les propriétés qui lient les comportements d’un contrôle parmi ses composants (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> est un exemple) ou lorsque la liaison bidirectionnelle est le scénario attendu et courants pour les utilisateurs (<xref:System.Windows.Controls.TextBox.Text%2A> est un exemple). Le changement des métadonnées associées à la liaison de données influence uniquement la valeur par défaut ; cette valeur par défaut peut toujours être changée pour chaque liaison individuelle. Pour plus d’informations sur les modes de liaison et la liaison en général, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).  
  
- Création de rapports si les propriétés doivent être journalisées par les applications ou services qui prennent en charge la journalisation (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Par défaut, la journalisation n’est pas activée pour les éléments généraux, mais l’est de manière sélective pour certains contrôles d’entrée d’utilisateur. Cette propriété est destinée à être lue par des services de journalisation, dont l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de journalisation, et est généralement définie sur des contrôles utilisateur, tels que des sélections d’utilisateur dans des listes qui doivent être rendues persistantes entre les étapes de navigation. Pour plus d’informations sur le journal, consultez [Vue d’ensemble de la navigation](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Lecture de FrameworkPropertyMetadata  
 Chacune des propriétés liées ci-dessus sont les propriétés spécifiques qui le <xref:System.Windows.FrameworkPropertyMetadata> ajoute à sa classe de base immédiate <xref:System.Windows.UIPropertyMetadata>. Par défaut, toutes ces propriétés ont la valeur `false`. Une demande de métadonnées pour une propriété lorsqu’il est important de connaître la valeur de ces propriétés doit tenter d’effectuer un cast des métadonnées retournées à <xref:System.Windows.FrameworkPropertyMetadata>, puis vérifiez les valeurs des propriétés individuelles en fonction des besoins.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Spécification des métadonnées  
 Lorsque vous créez une nouvelle instance de métadonnées à des fins d’appliquer des métadonnées à une nouvelle inscription de propriété de dépendance, vous avez le choix de la classe de métadonnées à utiliser : la base de <xref:System.Windows.PropertyMetadata> ou une classe dérivée de telles que <xref:System.Windows.FrameworkPropertyMetadata>. En général, vous devez utiliser <xref:System.Windows.FrameworkPropertyMetadata>, particulièrement si votre propriété interagit avec le système de propriétés et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctions telles que la disposition et la liaison de données. Une autre option pour des scénarios plus sophistiqués consiste à dériver à partir de <xref:System.Windows.FrameworkPropertyMetadata> pour créer vos propres métadonnées classe avec des informations supplémentaires de rapport contenues dans ses membres. Vous pouvez également utiliser <xref:System.Windows.PropertyMetadata> ou <xref:System.Windows.UIPropertyMetadata> pour communiquer le degré de prise en charge des fonctionnalités de votre implémentation.  
  
 Pour les propriétés existantes (<xref:System.Windows.DependencyProperty.AddOwner%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> appeler), vous devez toujours remplacer avec le type de métadonnées utilisé par l’inscription d’origine.  
  
 Si vous créez un <xref:System.Windows.FrameworkPropertyMetadata> d’une instance, il existe deux manières de remplir ces métadonnées avec des valeurs pour les propriétés spécifiques qui communiquent les caractéristiques de propriété de framework :  
  
1. Utilisez le <xref:System.Windows.FrameworkPropertyMetadata> signature de constructeur qui autorise un `flags` paramètre. Ce paramètre doit être rempli avec souhaité de toutes les valeurs combinées de le <xref:System.Windows.FrameworkPropertyMetadataOptions> indicateurs d’énumération.  
  
2. Utilisez une des signatures sans un `flags` paramètre, puis définissez chaque propriété booléenne de création de rapports sur <xref:System.Windows.FrameworkPropertyMetadata> à `true` pour chaque modification de caractéristique souhaitée. Si vous optez pour cette solution, vous devez définir ces propriétés avant la construction de tout élément possédant cette propriété de dépendance ; les propriétés booléennes sont en lecture-écriture afin d’autoriser ce comportement d’évitement du paramètre `flags` tout en complétant les métadonnées. Les métadonnées doivent toutefois être sealed avant l’utilisation de la propriété. Par conséquent, toute tentative de définition des propriétés après l’envoi d’une demande de métadonnées est une opération incorrecte.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Comportement de fusion des métadonnées de propriété de framework  
 Quand vous substituez des métadonnées de propriété de framework, les différentes caractéristiques des métadonnées sont fusionnées ou remplacées.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est fusionné. Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, ce rappel est stocké dans les métadonnées. Si vous ne spécifiez pas un <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est promue en tant que référence à partir de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- Le comportement réel propriétés système pour <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est que les implémentations pour tous les propriétaires de métadonnées dans la hiérarchie sont conservées et ajoutées à une table, avec l’ordre d’exécution par le système de propriétés étant que les rappels de la classe la plus dérivée sont appelé en premier. Les rappels hérités ne sont exécutés qu’une seule fois et sont considérés comme s’ils appartenaient à la classe qui les a placés dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> est remplacé. Si vous ne spécifiez pas un <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.DefaultValue%2A> provient de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> les implémentations sont remplacées. Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, ce rappel est stocké dans les métadonnées. Si vous ne spécifiez pas un <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> est promue en tant que référence à partir de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- Le comportement de système de propriétés est que seules les <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> dans les métadonnées immédiates est appelé. Aucune référence à d’autres <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implémentations dans la hiérarchie sont conservées.  
  
- Les indicateurs de <xref:System.Windows.FrameworkPropertyMetadataOptions> énumération sont combinés en une opération OR au niveau du bit.  Si vous spécifiez <xref:System.Windows.FrameworkPropertyMetadataOptions>, les options d’origine ne sont pas remplacées.  Pour modifier une option, définissez la propriété correspondante sur <xref:System.Windows.FrameworkPropertyMetadata>. Par exemple, si la version d’origine <xref:System.Windows.FrameworkPropertyMetadata> jeux d’objets la <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> indicateur, vous pouvez changer cela en définissant <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> à `false`.  
  
 Ce comportement est implémenté par <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>et peut être substitué sur des classes de métadonnées dérivées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
