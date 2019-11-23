---
title: Interfaces participant à la liaison de données
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 4e40f7ec1922cdf43e6a0b8f5734acaaeefbc514
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834587"
---
# <a name="interfaces-related-to-data-binding"></a>Interfaces participant à la liaison de données

Avec ADO.NET, vous pouvez créer de nombreuses structures de données différentes pour répondre aux besoins de liaison de votre application et des données que vous utilisez. Vous souhaiterez peut-être créer vos propres classes qui fourniront ou utiliseront des données dans les Windows Forms. Ces objets peuvent offrir différents niveaux de fonctionnalités et de complexité, de la liaison de données basique à la fourniture d’une prise en charge au moment du design, en passant par la vérification des erreurs, la notification des modifications ou même la prise en charge de la restauration structurée des modifications apportées aux données elles-mêmes.

## <a name="consumers-of-data-binding-interfaces"></a>Utilisateurs d’interfaces de liaison de données

Les sections suivantes décrivent deux groupes d’objets d’interface. Le premier groupe répertorie les interfaces implémentées sur les sources de données par les auteurs de sources de données. Ces interfaces sont conçues pour être utilisées par les consommateurs de sources de données, qui sont dans la plupart des cas des contrôles ou des composants Windows Forms. Le second groupe répertorie les interfaces conçues pour être utilisées par les auteurs de composants. Les auteurs de composants utilisent ces interfaces lorsqu’ils créent un composant prenant en charge la liaison de données pour une utilisation par le moteur de liaison de données Windows Forms. Vous pouvez implémenter ces interfaces dans les classes associées à votre formulaire pour activer la liaison de données. Chaque cas présente une classe qui implémente une interface permettant l’interaction avec les données. Les outils d’expérience de conception de données de Visual Studio Rapid Application Development (RAD) tirent déjà parti de cette fonctionnalité.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfaces pour implémentation par des auteurs de sources de données

Les interfaces suivantes sont conçues pour être utilisées par les contrôles Windows Forms :

- interface <xref:System.Collections.IList>

  Une classe qui implémente l’interface <xref:System.Collections.IList> peut être une <xref:System.Array>, <xref:System.Collections.ArrayList>ou <xref:System.Collections.CollectionBase>. Il s’agit de listes indexées d’éléments de type <xref:System.Object>. Ces listes doivent contenir des types homogènes, car le premier élément de l’index détermine le type. <xref:System.Collections.IList> n’est disponible pour la liaison qu’au moment de l’exécution.

  > [!NOTE]
  > Si vous souhaitez créer une liste d’objets métier pour la liaison avec Windows Forms, vous devez envisager d’utiliser l' <xref:System.ComponentModel.BindingList%601>. Le <xref:System.ComponentModel.BindingList%601> est une classe extensible qui implémente les interfaces principales requises pour la liaison de données bidirectionnelle Windows Forms.

- interface <xref:System.ComponentModel.IBindingList>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IBindingList> fournit un niveau de fonctionnalité de liaison de données bien supérieur. Cette implémentation fournit des fonctionnalités de tri de base et une notification des modifications, à la fois lorsque la liste des éléments change (par exemple, le champ Adresse du troisième élément d’une liste de clients change) et lorsque la liste elle-même change (par exemple, augmentation ou diminution du nombre d’éléments de la liste). La notification des modifications est importante si vous prévoyez de lier plusieurs contrôles aux mêmes données et si vous souhaitez que les modifications apportées aux données d’un contrôle se propagent à d’autres contrôles liés.

  > [!NOTE]
  > La notification de modification est activée pour l’interface <xref:System.ComponentModel.IBindingList> via la propriété <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> qui, lorsque `true`, déclenche un événement <xref:System.ComponentModel.IBindingList.ListChanged>, indiquant que la liste a été modifiée ou qu’un élément de la liste a été modifié.

  Le type de modification est décrit par la propriété <xref:System.ComponentModel.ListChangedType> du paramètre <xref:System.ComponentModel.ListChangedEventArgs>. Par conséquent, à chaque mise à jour du modèle de données, toutes les vues dépendantes, comme les autres contrôles liés à la même source de données, seront également mises à jour. Toutefois, les objets contenus dans la liste devront notifier la liste lorsqu’ils changent afin que la liste puisse déclencher l’événement <xref:System.ComponentModel.IBindingList.ListChanged>.

  > [!NOTE]
  > L' <xref:System.ComponentModel.BindingList%601> fournit une implémentation générique de l’interface <xref:System.ComponentModel.IBindingList>.

- interface <xref:System.ComponentModel.IBindingListView>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IBindingListView> fournit toutes les fonctionnalités d’une implémentation de <xref:System.ComponentModel.IBindingList>, ainsi que des fonctionnalités de filtrage et de tri avancé. Cette implémentation offre un filtrage basé sur les chaînes ainsi que le tri multicolonne avec des paires direction-descripteur de propriété.

- interface <xref:System.ComponentModel.IEditableObject>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IEditableObject> permet à un objet de contrôler le moment où les modifications apportées à cet objet sont rendues permanentes. Cette implémentation vous permet d’utiliser les méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, qui vous permettent de restaurer les modifications apportées à l’objet. Vous trouverez ci-dessous une brève explication du fonctionnement des méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, ainsi que de la façon dont elles fonctionnent conjointement les unes avec les autres pour permettre une restauration possible des modifications apportées aux données :

  - La méthode <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> signale le début d’une modification sur un objet. Un objet qui implémente cette interface doit stocker les mises à jour après l’appel de la méthode <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> de manière à ce que les mises à jour puissent être ignorées si la méthode <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> est appelée. Dans Windows Forms de liaison de données, vous pouvez appeler <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> plusieurs fois dans l’étendue d’une seule transaction de modification (par exemple, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Les implémentations de <xref:System.ComponentModel.IEditableObject> doivent suivre si <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> a déjà été appelé et ignorer les appels suivants à <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Étant donné que cette méthode peut être appelée plusieurs fois, il est important que les appels suivants à celle-ci soient non destructifs ; autrement dit, les appels de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> suivants ne peuvent pas détruire les mises à jour effectuées ou modifier les données qui ont été enregistrées lors du premier appel de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.

  - La méthode <xref:System.ComponentModel.IEditableObject.EndEdit%2A> envoie toutes les modifications depuis l’appel de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> dans l’objet sous-jacent, si l’objet est actuellement en mode édition.

  - La méthode <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> ignore toutes les modifications apportées à l’objet.

  Pour plus d’informations sur le fonctionnement des méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, consultez [enregistrer des données dans la base de données](/visualstudio/data-tools/save-data-back-to-the-database).

  Cette notion transactionnelle des fonctionnalités de données est utilisée par le contrôle <xref:System.Windows.Forms.DataGridView>.

- interface <xref:System.ComponentModel.ICancelAddNew>

  Une classe qui implémente l’interface <xref:System.ComponentModel.ICancelAddNew> implémente généralement l’interface <xref:System.ComponentModel.IBindingList> et vous permet de restaurer un ajout apporté à la source de données avec la méthode <xref:System.ComponentModel.IBindingList.AddNew%2A>. Si votre source de données implémente l’interface <xref:System.ComponentModel.IBindingList>, vous devez également l’implémenter dans l’interface <xref:System.ComponentModel.ICancelAddNew>.

- interface <xref:System.ComponentModel.IDataErrorInfo>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IDataErrorInfo> permet aux objets d’offrir des informations d’erreur personnalisées aux contrôles liés :

  - La propriété <xref:System.ComponentModel.IDataErrorInfo.Error%2A> retourne le texte général du message d’erreur (par exemple, « une erreur s’est produite »).

  - La propriété <xref:System.ComponentModel.IDataErrorInfo.Item%2A> retourne une chaîne avec le message d’erreur spécifique de la colonne (par exemple, « la valeur dans la colonne `State` n’est pas valide »).

- interface <xref:System.Collections.IEnumerable>

  Une classe qui implémente l’interface <xref:System.Collections.IEnumerable> est généralement consommée par ASP.NET. La prise en charge de Windows Forms pour cette interface est disponible uniquement via le composant <xref:System.Windows.Forms.BindingSource>.

  > [!NOTE]
  > Le composant <xref:System.Windows.Forms.BindingSource> copie tous les éléments <xref:System.Collections.IEnumerable> dans une liste distincte à des fins de liaison.

- interface <xref:System.ComponentModel.ITypedList>

  Une classe de collections qui implémente l’interface <xref:System.ComponentModel.ITypedList> offre la possibilité de contrôler l’ordre et l’ensemble des propriétés exposées au contrôle lié.

  > [!NOTE]
  > Lorsque vous implémentez la méthode <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> et que le tableau de <xref:System.ComponentModel.PropertyDescriptor> n’est pas null, la dernière entrée du tableau est le descripteur de propriété qui décrit la propriété de liste qui est une autre liste d’éléments.

- interface <xref:System.ComponentModel.ICustomTypeDescriptor>

  Une classe qui implémente l’interface <xref:System.ComponentModel.ICustomTypeDescriptor> fournit des informations dynamiques à propos de lui-même. Cette interface est similaire à <xref:System.ComponentModel.ITypedList>, mais elle est utilisée pour les objets plutôt que pour les listes. Cette interface est utilisée par <xref:System.Data.DataRowView> pour projeter le schéma des lignes sous-jacentes. Une implémentation simple de <xref:System.ComponentModel.ICustomTypeDescriptor> est fournie par la classe <xref:System.ComponentModel.CustomTypeDescriptor>.

  > [!NOTE]
  > Pour prendre en charge la liaison au moment du design aux types qui implémentent <xref:System.ComponentModel.ICustomTypeDescriptor>, le type doit également implémenter <xref:System.ComponentModel.IComponent> et exister en tant qu’instance sur le formulaire.

- interface <xref:System.ComponentModel.IListSource>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IListSource> active la liaison basée sur les listes sur les objets non listés. La méthode <xref:System.ComponentModel.IListSource.GetList%2A> de <xref:System.ComponentModel.IListSource> est utilisée pour retourner une liste pouvant être liée à partir d’un objet qui n’hérite pas de <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> est utilisé par la classe <xref:System.Data.DataSet>.

- interface <xref:System.ComponentModel.IRaiseItemChangedEvents>

  Une classe qui implémente l’interface <xref:System.ComponentModel.IRaiseItemChangedEvents> est une liste pouvant être liée qui implémente également l’interface <xref:System.ComponentModel.IBindingList>. Cette interface est utilisée pour indiquer si votre type déclenche <xref:System.ComponentModel.IBindingList.ListChanged> événements de type <xref:System.ComponentModel.ListChangedType.ItemChanged> par le biais de sa propriété <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>.

  > [!NOTE]
  > Vous devez implémenter le <xref:System.ComponentModel.IRaiseItemChangedEvents> si votre source de données fournit la conversion d’événement de la propriété à la liste décrite précédemment et interagit avec le composant <xref:System.Windows.Forms.BindingSource>. Dans le cas contraire, le <xref:System.Windows.Forms.BindingSource> effectuera également la propriété pour répertorier la conversion d’événements, ce qui ralentit les performances.

- interface <xref:System.ComponentModel.ISupportInitialize>

  Un composant qui implémente l’interface <xref:System.ComponentModel.ISupportInitialize> tire parti des optimisations par lots pour définir des propriétés et initialiser des propriétés codépendantes. Le <xref:System.ComponentModel.ISupportInitialize> contient deux méthodes :

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> signale que l’initialisation de l’objet démarre.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> signale la fin de l’initialisation de l’objet.

- interface <xref:System.ComponentModel.ISupportInitializeNotification>

  Un composant qui implémente l’interface <xref:System.ComponentModel.ISupportInitializeNotification> implémente également l’interface <xref:System.ComponentModel.ISupportInitialize>. Cette interface vous permet de notifier d’autres composants de <xref:System.ComponentModel.ISupportInitialize> que l’initialisation est terminée. L’interface <xref:System.ComponentModel.ISupportInitializeNotification> contient deux membres :

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> retourne une valeur `boolean` indiquant si le composant est initialisé.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> se produit lors de l’appel de <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>.

- interface <xref:System.ComponentModel.INotifyPropertyChanged>

  Une classe qui implémente cette interface est un type qui déclenche un événement lorsqu’une de ses valeurs de propriété change. Cette interface est conçue pour remplacer le modèle d’événement de modification pour chaque propriété d’un contrôle. Lorsqu’il est utilisé dans un <xref:System.ComponentModel.BindingList%601>, un objet métier doit implémenter l’interface <xref:System.ComponentModel.INotifyPropertyChanged> et le BindingList\`1 convertit <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événements en <xref:System.ComponentModel.BindingList%601.ListChanged> événements de type <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Pour que la notification de modification se produise dans une liaison entre un client lié et une source de données, votre type de source de données liée doit implémenter l’interface <xref:System.ComponentModel.INotifyPropertyChanged> (par défaut) ou vous pouvez fournir *propertyName*`Changed` événements pour le type lié, mais vous ne devez pas effectuer les deux.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfaces pour implémentation par des auteurs de composants

Les interfaces suivantes sont conçues pour une utilisation par le moteur de liaison de données Windows Forms :

- interface <xref:System.Windows.Forms.IBindableComponent>

  Une classe qui implémente cette interface est un composant qui n’est pas un contrôle et qui prend en charge la liaison de données. Cette classe retourne les liaisons de données et le contexte de liaison du composant via les propriétés <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> et <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> de cette interface.

  > [!NOTE]
  > Si votre composant hérite de <xref:System.Windows.Forms.Control>, il n’est pas nécessaire d’implémenter l’interface <xref:System.Windows.Forms.IBindableComponent>.

- interface <xref:System.Windows.Forms.ICurrencyManagerProvider>

  Une classe qui implémente l’interface <xref:System.Windows.Forms.ICurrencyManagerProvider> est un composant qui fournit son propre <xref:System.Windows.Forms.CurrencyManager> pour gérer les liaisons associées à ce composant particulier. L’accès à l' <xref:System.Windows.Forms.CurrencyManager> personnalisé est fourni par la propriété <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>.

  > [!NOTE]
  > Une classe qui hérite de <xref:System.Windows.Forms.Control> gère automatiquement les liaisons par le biais de sa propriété <xref:System.Windows.Forms.Control.BindingContext%2A>, de sorte que les cas dans lesquels vous devez implémenter les <xref:System.Windows.Forms.ICurrencyManagerProvider> sont relativement rares.

## <a name="see-also"></a>Voir aussi

- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
- [Guide pratique pour créer un contrôle à liaison simple dans un Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
