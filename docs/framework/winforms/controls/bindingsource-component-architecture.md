---
title: Architecture du composant BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364414"
---
# <a name="bindingsource-component-architecture"></a>Architecture du composant BindingSource
Avec le <xref:System.Windows.Forms.BindingSource> composant, vous pouvez lier universellement tous les contrôles de Windows Forms à des sources de données.  
  
 Le <xref:System.Windows.Forms.BindingSource> composant simplifie le processus de liaison des contrôles à une source de données et offre les avantages suivants par rapport à la liaison de données traditionnelle:  
  
- Active la liaison au moment du design aux objets métier.  
  
- Encapsule les <xref:System.Windows.Forms.CurrencyManager>fonctionnalitéset expose les événements au moment du Design. <xref:System.Windows.Forms.CurrencyManager>  
  
- Simplifie la création d’une liste qui <xref:System.ComponentModel.IBindingList> prend en charge l’interface en fournissant une notification de modification de liste pour les sources de données qui ne prennent pas en charge la notification de modification de liste en mode natif.  
  
- Fournit un point d’extensibilité pour <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> la méthode.  
  
- Fournit un niveau d’indirection entre la source de données et le contrôle. Cette indirection est importante lorsque la source de données peut changer au moment de l’exécution.  
  
- Interagit avec d’autres contrôles de Windows Forms liés aux données, en <xref:System.Windows.Forms.BindingNavigator> particulier les <xref:System.Windows.Forms.DataGridView> contrôles et.  
  
 Pour ces raisons, le <xref:System.Windows.Forms.BindingSource> composant est la meilleure façon de lier vos contrôles de Windows Forms à des sources de données.  
  
## <a name="bindingsource-features"></a>Fonctionnalités BindingSource  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit plusieurs fonctionnalités pour lier des contrôles à des données. Grâce à ces fonctionnalités, vous pouvez implémenter la plupart des scénarios de liaison de données avec presque aucun codage de votre part.  
  
 Pour <xref:System.Windows.Forms.BindingSource> ce faire, le composant fournit une interface cohérente permettant d’accéder à de nombreux types de sources de données différents. Cela signifie que vous utilisez la même procédure pour la liaison à n’importe quel type. Par exemple, vous pouvez attacher la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété à un <xref:System.Data.DataSet> objet ou à un objet métier et, dans les deux cas, vous utilisez le même ensemble de propriétés, de méthodes et d’événements pour manipuler la source de données.  
  
 L’interface cohérente fournie par <xref:System.Windows.Forms.BindingSource> le composant simplifie grandement le processus de liaison des données aux contrôles. Pour les types de sources de données qui fournissent une notification <xref:System.Windows.Forms.BindingSource> de modification, le composant communique automatiquement les modifications entre le contrôle et la source de données. Pour les types de source de données qui ne fournissent pas de notification de modification, des événements vous permettent de déclencher des notifications de modifications. La liste suivante répertorie les fonctionnalités prises en <xref:System.Windows.Forms.BindingSource> charge par le composant:  
  
- Indirection.  
  
- Gestion des devises.  
  
- Source de données sous forme de liste.  
  
- <xref:System.Windows.Forms.BindingSource>en tant que. <xref:System.ComponentModel.IBindingList>  
  
- Création d’élément personnalisé.  
  
- Création d’éléments transactionnels.  
  
- <xref:System.Collections.IEnumerable>supporter.  
  
- Prise en charge au moment du Design.  
  
- Méthodes <xref:System.Windows.Forms.ListBindingHelper> statiques.  
  
- Tri et filtrage avec l' <xref:System.ComponentModel.IBindingListView> interface.  
  
- Intégration à <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Adressage indirect  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit un niveau d’indirection entre un contrôle et une source de données. Au lieu de lier un contrôle directement à une source de données, vous liez le contrôle <xref:System.Windows.Forms.BindingSource>à un et vous attachez la source de <xref:System.Windows.Forms.BindingSource> données à <xref:System.Windows.Forms.BindingSource.DataSource%2A> la propriété du composant.  
  
 Avec ce niveau d’indirection, vous pouvez modifier la source de données sans réinitialiser la liaison de contrôle. Vous bénéficiez ainsi des fonctionnalités suivantes:  
  
- Vous pouvez attacher le <xref:System.Windows.Forms.BindingSource> à différentes sources de données tout en conservant les liaisons de contrôle actuelles.  
  
- Vous pouvez modifier des éléments dans la source de données et notifier les contrôles liés. Pour plus d'informations, voir [Procédure : Refléter les mises à jour de la source de données dans un contrôle](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)de Windows Forms avec le BindingSource.  
  
- Vous pouvez effectuer une liaison <xref:System.Type> à un à la place d’un objet en mémoire. Pour plus d'informations, voir [Procédure : Liez un contrôle Windows Forms à un type](how-to-bind-a-windows-forms-control-to-a-type.md). Vous pouvez ensuite effectuer une liaison à un objet au moment de l’exécution.  
  
### <a name="currency-management"></a>Gestion des devises  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente l' <xref:System.Windows.Forms.ICurrencyManagerProvider> interface pour gérer la gestion des devises pour vous. Avec l' <xref:System.Windows.Forms.ICurrencyManagerProvider> interface, vous pouvez également accéder au gestionnaire de devise pour un <xref:System.Windows.Forms.BindingSource>, en plus du gestionnaire de devise pour un <xref:System.Windows.Forms.BindingSource> autre lié au même <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 Le <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.CurrencyManager> composant<xref:System.Windows.Forms.CurrencyManager> encapsule les fonctionnalités et expose les propriétés et événements les plus courants. Le tableau suivant décrit certains des membres liés à la gestion des devises.  
  
 Propriété <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>  
 Obtient le gestionnaire de devise associé à <xref:System.Windows.Forms.BindingSource>.  
  
 Méthode <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>  
 Si une autre <xref:System.Windows.Forms.BindingSource> est liée au membre de données spécifié, obtient son gestionnaire de devise.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Current%2A>  
 Obtient l'élément actuel de la source de données.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Position%2A>  
 Obtient ou définit la position actuelle dans la liste sous-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.EndEdit%2A>  
 Applique des modifications en attente à la source de données sous-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>  
 Annule l'opération de modification actuelle.  
  
### <a name="data-source-as-a-list"></a>Source de données sous forme de liste  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente les <xref:System.ComponentModel.IBindingListView> interfaces <xref:System.ComponentModel.ITypedList> et. Avec cette implémentation, vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> composant lui-même comme source de données, sans stockage externe.  
  
 Lorsque le <xref:System.Windows.Forms.BindingSource> composant est attaché à une source de données, il expose la source de données sous forme de liste.  
  
 La <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété peut être définie sur plusieurs sources de données. Il s’agit notamment des types, des objets et des listes de types. La source de données résultante sera exposée sous la forme d’une liste. Le tableau suivant présente certaines des sources de données communes et l’évaluation de la liste résultante.  
  
|DataSource, propriété|Liste des résultats|  
|-------------------------|------------------|  
|Référence Null (`Nothing` en Visual Basic)|Vide <xref:System.ComponentModel.IBindingList> d’objets. L’ajout d’un élément affecte à la liste le type de l’élément ajouté.|  
|Référence null (`Nothing` en Visual Basic) avec <xref:System.Windows.Forms.BindingSource.DataMember%2A> Set|Non pris en charge; déclenche <xref:System.ArgumentException>.|  
|Type sans liste ou objet de type "T"|Vide <xref:System.ComponentModel.IBindingList> de type "T".|  
|Instance de tableau|<xref:System.ComponentModel.IBindingList> Contenant les éléments du tableau.|  
|<xref:System.Collections.IEnumerable>instancié|<xref:System.ComponentModel.IBindingList> Contenant les<xref:System.Collections.IEnumerable> éléments|  
|Instance List contenant le type "T"|<xref:System.ComponentModel.IBindingList> Instance contenant le type "T".|  
  
 En outre, <xref:System.Windows.Forms.BindingSource.DataSource%2A> peut être défini sur d’autres types de listes, <xref:System.ComponentModel.IListSource> tels <xref:System.ComponentModel.ITypedList>que et, <xref:System.Windows.Forms.BindingSource> et les gère de manière appropriée. Dans ce cas, le type contenu dans la liste doit avoir un constructeur sans paramètre.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource en tant que IBindingList  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit des membres pour accéder aux données sous-jacentes et les manipuler <xref:System.ComponentModel.IBindingList>sous forme de. Le tableau suivant décrit quelques-uns de ces membres.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.List%2A>|Obtient la liste qui résulte de l’évaluation des <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriétés ou. <xref:System.Windows.Forms.BindingSource.DataMember%2A>|  
|Méthode <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Ajoute un nouvel élément à la liste sous-jacente. S’applique aux sources de données qui <xref:System.ComponentModel.IBindingList> implémentent l’interface et autorisent l’ajout d' <xref:System.Windows.Forms.BindingSource.AllowNew%2A> éléments (autrement dit `true`, la propriété a la valeur).|  
  
### <a name="custom-item-creation"></a>Création d’élément personnalisé  
 Vous pouvez gérer l' <xref:System.Windows.Forms.BindingSource.AddingNew> événement pour fournir votre propre logique de création d’éléments. L' <xref:System.Windows.Forms.BindingSource.AddingNew> événement se produit avant l’ajout <xref:System.Windows.Forms.BindingSource>d’un nouvel objet au. Cet événement est déclenché après l' <xref:System.Windows.Forms.BindingSource.AddNew%2A> appel de la méthode, mais avant que le nouvel élément soit ajouté à la liste sous-jacente. En gérant cet événement, vous pouvez fournir un comportement de création d’élément personnalisé sans dériver de la <xref:System.Windows.Forms.BindingSource> classe. Pour plus d’informations, consultez [Guide pratique pour Personnaliser l’ajout d’éléments avec le](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)BindingSource Windows Forms.  
  
### <a name="transactional-item-creation"></a>Création d’éléments transactionnels  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente l' <xref:System.ComponentModel.ICancelAddNew> interface, qui permet la création d’éléments transactionnels. Une fois qu’un nouvel élément a été créé à l’aide d’un <xref:System.Windows.Forms.BindingSource.AddNew%2A>appel à, l’ajout peut être validé ou annulé des manières suivantes:  
  
- La <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> méthode valide l’ajout en attente de manière explicite.  
  
- L’exécution d’une autre opération de collecte, telle qu’une insertion, une suppression ou un déplacement, validera implicitement l’ajout en attente.  
  
- La <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> méthode annule l’ajout en attente si la méthode n’a pas déjà été validée.  
  
### <a name="ienumerable-support"></a>Prise en charge d’IEnumerable  
 Le <xref:System.Windows.Forms.BindingSource> composant permet de lier des <xref:System.Collections.IEnumerable> contrôles à des sources de données. Avec ce composant, vous pouvez effectuer une liaison à une source de données <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>telle que.  
  
 Quand une <xref:System.Collections.IEnumerable> source de données est assignée <xref:System.Windows.Forms.BindingSource> au composant <xref:System.Windows.Forms.BindingSource> , crée <xref:System.ComponentModel.IBindingList> un et ajoute le contenu de <xref:System.Collections.IEnumerable> la source de données à la liste.  
  
### <a name="design-time-support"></a>Prise en charge au moment du design  
 Certains types d’objets ne peuvent pas être créés au moment du design, tels que des objets créés à partir d’une classe de fabrique, ou des objets retournés par un service Web. Vous pouvez parfois être amené à lier vos contrôles à ces types au moment du design, même s’il n’y a pas d’objet dans la mémoire auquel vos contrôles peuvent être liés. Vous pouvez, par exemple, avoir besoin d’étiqueter les en-têtes <xref:System.Windows.Forms.DataGridView> de colonnes d’un contrôle avec les noms des propriétés publiques de votre type personnalisé.  
  
 Pour prendre en charge ce scénario <xref:System.Windows.Forms.BindingSource> , le composant prend en <xref:System.Type>charge la liaison à un. <xref:System.Type> Quand vous assignez un <xref:System.Windows.Forms.BindingSource.DataSource%2A> à la propriété <xref:System.Windows.Forms.BindingSource> , le composant crée <xref:System.ComponentModel.BindingList%601> un <xref:System.Type> vide d’éléments. Les contrôles que vous liez par la <xref:System.Windows.Forms.BindingSource> suite au composant seront avertis de la présence des propriétés ou du schéma de votre type au moment de la conception, ou au moment de l’exécution. Pour plus d'informations, voir [Procédure : Liez un contrôle Windows Forms à un type](how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Méthodes ListBindingHelper statiques  
 <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType> `DataSource` / `DataMember` Les types <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, et<xref:System.Windows.Forms.BindingSource> partagent tous une logique commune pour générer une liste à partir d’une paire. En outre, cette logique commune est exposée publiquement pour une utilisation par les auteurs de contrôle et d' `static` autres tiers dans les méthodes suivantes:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Tri et filtrage avec l’interface IBindingListView  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente l' <xref:System.ComponentModel.IBindingListView> interface, qui étend l' <xref:System.ComponentModel.IBindingList> interface. Le <xref:System.ComponentModel.IBindingList> permet le tri d’une seule <xref:System.ComponentModel.IBindingListView> colonne et le tri et le filtrage avancés. Avec <xref:System.ComponentModel.IBindingListView>, vous pouvez trier et filtrer les éléments de la source de données, si la source de données implémente également l’une de ces interfaces. Le <xref:System.Windows.Forms.BindingSource> composant ne fournit pas d’implémentation de référence de ces membres. Au lieu de cela, les appels sont transférés à la liste sous-jacente.  
  
 Le tableau suivant décrit les propriétés que vous utilisez pour le tri et le filtrage.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.Filter%2A>|Si la source de données est un <xref:System.ComponentModel.IBindingListView>, obtient ou définit l'expression utilisée pour filtrer les lignes affichées.|  
|Propriété <xref:System.Windows.Forms.BindingSource.Sort%2A>|Si la source de données est un <xref:System.ComponentModel.IBindingList>, obtient ou définit un nom de colonne utilisé pour le tri et les informations d'ordre de tri.<br /><br /> ou<br /><br /> Si la source de données est <xref:System.ComponentModel.IBindingListView> un et prend en charge le tri avancé, obtient plusieurs noms de colonnes utilisés pour le tri et l’ordre de tri.|  
  
### <a name="integration-with-bindingnavigator"></a>Intégration avec BindingNavigator  
 Vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> composant pour lier n’importe quel contrôle de Windows Forms à une source de <xref:System.Windows.Forms.BindingNavigator> données, mais le contrôle est conçu spécifiquement <xref:System.Windows.Forms.BindingSource> pour fonctionner avec le composant. Le <xref:System.Windows.Forms.BindingNavigator> contrôle fournit une interface utilisateur pour le contrôle <xref:System.Windows.Forms.BindingSource> de l’élément actuel du composant. Par défaut, le <xref:System.Windows.Forms.BindingNavigator> contrôle fournit des boutons qui correspondent aux méthodes de navigation sur <xref:System.Windows.Forms.BindingSource> le composant. Pour plus d'informations, voir [Procédure : Parcourez les données avec le](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)contrôle Windows Forms BindingNavigator.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Vue d'ensemble du composant BindingSource](bindingsource-component-overview.md)
- [BindingNavigator, contrôle](bindingnavigator-control-windows-forms.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Guide pratique : Lier un contrôle Windows Forms à un type](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Guide pratique : Refléter les mises à jour de la source de données dans un contrôle de Windows Forms avec le BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
