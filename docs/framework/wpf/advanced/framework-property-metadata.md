---
title: Métadonnées de propriété de framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186650"
---
# <a name="framework-property-metadata"></a>Métadonnées de propriété de framework
Des options de métadonnées de propriété de framework sont signalées pour les propriétés des éléments objet considérés comme étant au niveau du framework WPF dans l’architecture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. En général, la désignation au niveau du cadre WPF implique que les caractéristiques telles que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le rendu, la liaison des données et les raffinements du système de propriété sont traitées par les API de présentation et les exécutoires. Les métadonnées de propriété de framework sont interrogées par ces systèmes afin d’identifier les caractéristiques spécifiques aux fonctionnalités de propriétés d’un élément particulier.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous avez lu [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Vous devez également avoir lu [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>Informations communiquées par les métadonnées de propriété de framework  
 Les métadonnées de propriété de framework peuvent être réparties dans les catégories suivantes :  
  
- Signaler les propriétés de<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>mise <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>en page qui affectent un élément ( , , . Vous pouvez définir ces drapeaux dans des métadonnées si la propriété <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> affecte ces aspects respectifs, et vous implémentez également les méthodes de votre classe pour fournir un comportement de rendu spécifique et des informations au système de mise en page. En général, une telle implémentation vérifie la présence d’invalidations de propriété dans les propriétés de dépendance dont des propriétés de disposition avaient la valeur true dans les métadonnées de propriété, et seules ces invalidations font l’objet d’une demande de nouvelle passe de disposition.  
  
- Déclaration des propriétés de mise en<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>page qui affectent l’élément parent d’un élément ( , ). Quelques exemples où ces <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> drapeaux <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>sont définis par défaut sont et .  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Par défaut, les propriétés de dépendance n’héritent pas de valeurs. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>permet à la voie de l’héritage de se déplacer également dans un arbre visuel, ce qui est nécessaire pour certains scénarios de composition de contrôle.  
  
    > [!NOTE]
    > Le terme « hérite » dans le contexte des valeurs de propriété revêt une signification spécifique pour les propriétés de dépendance ; il signifie que les éléments enfants peuvent hériter de la valeur de propriété de dépendance réelle des éléments parents grâce à une fonctionnalité au niveau du framework WPF du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette notion est donc sans rapport direct avec le type de code managé et l’héritage de membres par le biais de types dérivés. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).  
  
- Signaler les caractéristiques de liaison des données (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>. Par défaut, les propriétés de dépendance du framework prennent en charge la liaison de données avec un comportement de liaison unidirectionnel. Vous pouvez désactiver la liaison de données s’il n’y avait aucun scénario pour cela que ce soit (parce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qu’ils sont destinés à être flexibles et extensibles, il n’y a pas beaucoup d’exemples de telles propriétés dans les API par défaut). Vous pouvez définir la liaison pour avoir un défaut bidirectionnel pour les<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> propriétés qui lient les comportements d’un contrôle parmi<xref:System.Windows.Controls.TextBox.Text%2A> ses composants (est un exemple) ou où la liaison bidirectionnel est le scénario commun et attendu pour les utilisateurs (est un exemple). Le changement des métadonnées associées à la liaison de données influence uniquement la valeur par défaut ; cette valeur par défaut peut toujours être changée pour chaque liaison individuelle. Pour plus d’informations sur les modes de liaison et la liaison en général, consultez [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Signaler si les propriétés doivent être revues<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>par des applications ou des services qui prennent en charge la revue ( ). Par défaut, la journalisation n’est pas activée pour les éléments généraux, mais l’est de manière sélective pour certains contrôles d’entrée d’utilisateur. Cette propriété est destinée à être lue par des services de journalisation, dont l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de journalisation, et est généralement définie sur des contrôles utilisateur, tels que des sélections d’utilisateur dans des listes qui doivent être rendues persistantes entre les étapes de navigation. Pour plus d’informations sur le journal, consultez [Vue d’ensemble de la navigation](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>Lecture de FrameworkPropertyMetadata  
 Chacune des propriétés liées ci-dessus sont les propriétés spécifiques que l’ajoute <xref:System.Windows.FrameworkPropertyMetadata> à sa classe <xref:System.Windows.UIPropertyMetadata>de base immédiate . Par défaut, toutes ces propriétés ont la valeur `false`. Une demande de métadonnées pour une propriété où la connaissance de la <xref:System.Windows.FrameworkPropertyMetadata>valeur de ces propriétés est importante devrait tenter de jeter les métadonnées retournées à , puis vérifier les valeurs des propriétés individuelles au besoin.  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>Spécification des métadonnées  
 Lorsque vous créez une nouvelle instance de métadonnées aux fins de l’application de métadonnées à <xref:System.Windows.PropertyMetadata> un nouvel enregistrement <xref:System.Windows.FrameworkPropertyMetadata>de propriété de dépendance, vous avez le choix de la classe de métadonnées à utiliser: la base ou une classe dérivée comme . En général, vous <xref:System.Windows.FrameworkPropertyMetadata>devez utiliser, en particulier si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre propriété a une interaction avec le système de propriété et des fonctions telles que la mise en page et la liaison des données. Une autre option pour des scénarios <xref:System.Windows.FrameworkPropertyMetadata> plus sophistiqués est de tirer de créer votre propre classe de rapports de métadonnées avec des informations supplémentaires portées dans ses membres. Ou vous <xref:System.Windows.PropertyMetadata> pouvez <xref:System.Windows.UIPropertyMetadata> utiliser ou communiquer le degré de support pour les fonctionnalités de votre implémentation.  
  
 Pour les<xref:System.Windows.DependencyProperty.AddOwner%2A> propriétés existantes (ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> appel), vous devez toujours passer outre avec le type de métadonnées utilisé par l’enregistrement d’origine.  
  
 Si vous créez <xref:System.Windows.FrameworkPropertyMetadata> un cas, il existe deux façons de remplir ces métadonnées avec des valeurs pour les propriétés spécifiques qui communiquent les caractéristiques de propriété-cadre:  
  
1. Utilisez <xref:System.Windows.FrameworkPropertyMetadata> la signature du `flags` constructeur qui permet un paramètre. Ce paramètre doit être rempli de <xref:System.Windows.FrameworkPropertyMetadataOptions> toutes les valeurs combinées souhaitées des indicateurs de recensement.  
  
2. Utilisez l’une des `flags` signatures sans paramètre, puis <xref:System.Windows.FrameworkPropertyMetadata> définissez chaque propriété Boolean rapport sur pour `true` chaque changement caractéristique souhaité. Si vous optez pour cette solution, vous devez définir ces propriétés avant la construction de tout élément possédant cette propriété de dépendance ; les propriétés booléennes sont en lecture-écriture afin d’autoriser ce comportement d’évitement du paramètre `flags` tout en complétant les métadonnées. Les métadonnées doivent toutefois être sealed avant l’utilisation de la propriété. Par conséquent, toute tentative de définition des propriétés après l’envoi d’une demande de métadonnées est une opération incorrecte.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>Comportement de fusion des métadonnées de propriété de framework  
 Quand vous substituez des métadonnées de propriété de framework, les différentes caractéristiques des métadonnées sont fusionnées ou remplacées.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>est fusionnée. Si vous ajoutez <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>un nouveau , ce rappel est stocké dans les métadonnées. Si vous ne <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> spécifiez pas <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> un dans le remplacement, la valeur de est promu comme une référence de l’ancêtre le plus proche qui l’a spécifié dans les métadonnées.  
  
- Le comportement réel <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> du système de propriété est que les implémentations pour tous les propriétaires de métadonnées dans la hiérarchie sont conservés et ajoutés à un tableau, avec l’ordre d’exécution par le système de propriété étant que les rappels de la classe la plus profondément dérivée sont invoqués en premier. Les rappels hérités ne sont exécutés qu’une seule fois et sont considérés comme s’ils appartenaient à la classe qui les a placés dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>est remplacé. Si vous ne <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> spécifiez pas <xref:System.Windows.PropertyMetadata.DefaultValue%2A> un dans le remplacement, la valeur de vient de l’ancêtre le plus proche qui l’a spécifié dans les métadonnées.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>les implémentations sont remplacées. Si vous ajoutez <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>un nouveau , ce rappel est stocké dans les métadonnées. Si vous ne <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> spécifiez pas <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> un dans le remplacement, la valeur de est promu comme une référence de l’ancêtre le plus proche qui l’a spécifié dans les métadonnées.  
  
- Le comportement du système <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> de propriété est que seules les métadonnées immédiates sont invoquées. Aucune référence <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> à d’autres implémentations dans la hiérarchie n’est conservée.  
  
- Les drapeaux <xref:System.Windows.FrameworkPropertyMetadataOptions> de l’énumération sont combinés comme une opération un peuwise OU.  Si vous <xref:System.Windows.FrameworkPropertyMetadataOptions>spécifiez, les options d’origine ne sont pas écrasées.  Pour modifier une option, définissez la propriété correspondante sur <xref:System.Windows.FrameworkPropertyMetadata>. Par exemple, si <xref:System.Windows.FrameworkPropertyMetadata> l’objet d’origine définit le <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> drapeau, vous pouvez changer cela en définissant <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> à `false`.  
  
 Ce comportement est <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>mis en œuvre par , et peut être remplacé sur les classes de métadonnées dérivées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
