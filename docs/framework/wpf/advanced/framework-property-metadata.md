---
title: Métadonnées de propriété de framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964217"
---
# <a name="framework-property-metadata"></a>Métadonnées de propriété de framework
Des options de métadonnées de propriété de framework sont signalées pour les propriétés des éléments objet considérés comme étant au niveau du framework WPF dans l’architecture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. En général, la désignation au niveau de l’infrastructure WPF implique que des fonctionnalités telles que le rendu, la liaison de données et les améliorations du système de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés sont gérées par les exécutables et les API de présentation. Les métadonnées de propriété de framework sont interrogées par ces systèmes afin d’identifier les caractéristiques spécifiques aux fonctionnalités de propriétés d’un élément particulier.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous avez lu [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Vous devez également avoir lu [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Informations communiquées par les métadonnées de propriété de framework  
 Les métadonnées de propriété de framework peuvent être réparties dans les catégories suivantes :  
  
- Signalement des propriétés de disposition qui affectent<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>un <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>élément <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>(,,). Vous pouvez définir ces indicateurs dans les métadonnées si la propriété affecte ces aspects respectifs, et si vous implémentez également les <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthodes dans votre classe pour fournir un comportement de rendu spécifique et des informations à la disposition. requise. En général, une telle implémentation vérifie la présence d’invalidations de propriété dans les propriétés de dépendance dont des propriétés de disposition avaient la valeur true dans les métadonnées de propriété, et seules ces invalidations font l’objet d’une demande de nouvelle passe de disposition.  
  
- Signalement des propriétés de disposition qui affectent l’élément parent d'<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>un <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>élément (,). Voici quelques exemples où ces indicateurs sont définis par défaut <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> : <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>et.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Par défaut, les propriétés de dépendance n’héritent pas de valeurs. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>permet à la voie d’héritage de se déplacer également dans une arborescence d’éléments visuels, ce qui est nécessaire pour certains scénarios de composition de contrôle.  
  
    > [!NOTE]
    > Le terme « hérite » dans le contexte des valeurs de propriété revêt une signification spécifique pour les propriétés de dépendance ; il signifie que les éléments enfants peuvent hériter de la valeur de propriété de dépendance réelle des éléments parents grâce à une fonctionnalité au niveau du framework WPF du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette notion est donc sans rapport direct avec le type de code managé et l’héritage de membres par le biais de types dérivés. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).  
  
- Caractéristiques de la liaison de<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>données <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>de rapports (,). Par défaut, les propriétés de dépendance du framework prennent en charge la liaison de données avec un comportement de liaison unidirectionnel. Vous pouvez désactiver la liaison de données s’il n’y avait aucun scénario (parce qu’elles sont conçues pour être flexibles et extensibles, il n’existe pas de nombreux exemples [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de ces propriétés dans les API par défaut). Vous pouvez définir une liaison avec une valeur par défaut bidirectionnelle pour les propriétés qui lient les comportements d’un contrôle parmi ses composants<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> (est un exemple) ou où la liaison bidirectionnelle est le scénario courant et attendu pour<xref:System.Windows.Controls.TextBox.Text%2A> les utilisateurs (est un exemple). Le changement des métadonnées associées à la liaison de données influence uniquement la valeur par défaut ; cette valeur par défaut peut toujours être changée pour chaque liaison individuelle. Pour plus d’informations sur les modes de liaison et la liaison en général, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).  
  
- Rapport indiquant si les propriétés doivent être journalisées par les applications ou les services qui<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>prennent en charge la journalisation (). Par défaut, la journalisation n’est pas activée pour les éléments généraux, mais l’est de manière sélective pour certains contrôles d’entrée d’utilisateur. Cette propriété est destinée à être lue par des services de journalisation, dont l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de journalisation, et est généralement définie sur des contrôles utilisateur, tels que des sélections d’utilisateur dans des listes qui doivent être rendues persistantes entre les étapes de navigation. Pour plus d’informations sur le journal, consultez [Vue d’ensemble de la navigation](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Lecture de FrameworkPropertyMetadata  
 Chacune des propriétés liées ci-dessus sont les propriétés spécifiques que <xref:System.Windows.FrameworkPropertyMetadata> le ajoute à sa classe <xref:System.Windows.UIPropertyMetadata>de base immédiate. Par défaut, toutes ces propriétés ont la valeur `false`. Une demande de métadonnées pour une propriété où la valeur de ces propriétés est importante doit tenter d’effectuer un cast des <xref:System.Windows.FrameworkPropertyMetadata>métadonnées retournées en, puis vérifier les valeurs des propriétés individuelles selon les besoins.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Spécification des métadonnées  
 Quand vous créez une nouvelle instance de métadonnées à des fins d’application de métadonnées à une nouvelle inscription de propriété de dépendance, vous avez le choix de la <xref:System.Windows.PropertyMetadata> classe de métadonnées à utiliser <xref:System.Windows.FrameworkPropertyMetadata>: la base ou une classe dérivée telle que. En général, vous devez utiliser <xref:System.Windows.FrameworkPropertyMetadata>, en particulier si votre propriété a une interaction avec le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de propriétés et des fonctions telles que la disposition et la liaison de données. Une autre option pour les scénarios plus sophistiqués consiste <xref:System.Windows.FrameworkPropertyMetadata> à dériver de pour créer votre propre classe de création de rapports de métadonnées avec des informations supplémentaires dans ses membres. Vous pouvez également utiliser <xref:System.Windows.PropertyMetadata> ou <xref:System.Windows.UIPropertyMetadata> pour communiquer le degré de prise en charge des fonctionnalités de votre implémentation.  
  
 Pour les propriétés existantes<xref:System.Windows.DependencyProperty.AddOwner%2A> ( <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> ou Call), vous devez toujours remplacer par le type de métadonnées utilisé par l’inscription d’origine.  
  
 Si vous créez une <xref:System.Windows.FrameworkPropertyMetadata> instance de, il existe deux façons de remplir ces métadonnées avec des valeurs pour les propriétés spécifiques qui communiquent les caractéristiques de la propriété de l’infrastructure:  
  
1. Utilisez la <xref:System.Windows.FrameworkPropertyMetadata> signature de constructeur qui autorise `flags` un paramètre. Ce paramètre doit être rempli avec toutes les valeurs combinées souhaitées des indicateurs d' <xref:System.Windows.FrameworkPropertyMetadataOptions> énumération.  
  
2. Utilisez l’une des signatures sans `flags` paramètre, puis affectez <xref:System.Windows.FrameworkPropertyMetadata> à `true` chaque propriété booléenne de création de rapports la valeur pour chaque modification de caractéristique souhaitée. Si vous optez pour cette solution, vous devez définir ces propriétés avant la construction de tout élément possédant cette propriété de dépendance ; les propriétés booléennes sont en lecture-écriture afin d’autoriser ce comportement d’évitement du paramètre `flags` tout en complétant les métadonnées. Les métadonnées doivent toutefois être sealed avant l’utilisation de la propriété. Par conséquent, toute tentative de définition des propriétés après l’envoi d’une demande de métadonnées est une opération incorrecte.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Comportement de fusion des métadonnées de propriété de framework  
 Quand vous substituez des métadonnées de propriété de framework, les différentes caractéristiques des métadonnées sont fusionnées ou remplacées.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>est fusionné. Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, ce rappel est stocké dans les métadonnées. Si vous ne spécifiez <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> pas de dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est promue en tant que référence à partir de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- Le comportement réel du système de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> propriétés pour est que les implémentations pour tous les propriétaires de métadonnées dans la hiérarchie sont conservées et ajoutées à une table, l’ordre d’exécution du système de propriétés étant que les rappels de la classe la plus dérivée sont appelée en premier. Les rappels hérités ne sont exécutés qu’une seule fois et sont considérés comme s’ils appartenaient à la classe qui les a placés dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>est remplacé. Si vous ne spécifiez pas <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> de dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.DefaultValue%2A> provient de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>les implémentations sont remplacées. Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, ce rappel est stocké dans les métadonnées. Si vous ne spécifiez <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> pas de dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> est promue en tant que référence à partir de l’ancêtre le plus proche qui l’a spécifiée dans les métadonnées.  
  
- Le comportement du système de propriétés est que <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> seul le dans les métadonnées immédiates est appelé. Aucune référence à d' <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> autres implémentations dans la hiérarchie n’est conservée.  
  
- Les indicateurs d' <xref:System.Windows.FrameworkPropertyMetadataOptions> énumération sont combinés comme une opération or au niveau du bit.  Si vous spécifiez <xref:System.Windows.FrameworkPropertyMetadataOptions>, les options d’origine ne sont pas remplacées.  Pour modifier une option, définissez la propriété correspondante sur <xref:System.Windows.FrameworkPropertyMetadata>. Par exemple, si l’objet <xref:System.Windows.FrameworkPropertyMetadata> d’origine définit <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> l’indicateur, vous pouvez le modifier en <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> affectant à `false`la valeur.  
  
 Ce comportement est implémenté par <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>et peut être substitué sur les classes de métadonnées dérivées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
