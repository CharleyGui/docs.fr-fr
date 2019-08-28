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
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046370"
---
# <a name="interfaces-related-to-data-binding"></a>Interfaces participant à la liaison de données

Avec ADO.NET, vous pouvez créer de nombreuses structures de données différentes pour répondre aux besoins de liaison de votre application et des données que vous utilisez. Vous souhaiterez peut-être créer vos propres classes qui fourniront ou utiliseront des données dans les Windows Forms. Ces objets peuvent offrir différents niveaux de fonctionnalités et de complexité, de la liaison de données basique à la fourniture d’une prise en charge au moment du design, en passant par la vérification des erreurs, la notification des modifications ou même la prise en charge de la restauration structurée des modifications apportées aux données elles-mêmes.

## <a name="consumers-of-data-binding-interfaces"></a>Utilisateurs d’interfaces de liaison de données

Les sections suivantes décrivent deux groupes d’objets d’interface. Le premier groupe répertorie les interfaces implémentées sur les sources de données par les auteurs de sources de données. Ces interfaces sont conçues pour être utilisées par les consommateurs de sources de données, qui sont dans la plupart des cas des contrôles ou des composants Windows Forms. Le second groupe répertorie les interfaces conçues pour être utilisées par les auteurs de composants. Les auteurs de composants utilisent ces interfaces lorsqu’ils créent un composant prenant en charge la liaison de données pour une utilisation par le moteur de liaison de données Windows Forms. Vous pouvez implémenter ces interfaces dans les classes associées à votre formulaire pour activer la liaison de données. Chaque cas présente une classe qui implémente une interface permettant l’interaction avec les données. Les outils d’expérience de conception de données de Visual Studio Rapid Application Development (RAD) tirent déjà parti de cette fonctionnalité.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfaces pour implémentation par des auteurs de sources de données

Les interfaces suivantes sont conçues pour être utilisées par les contrôles Windows Forms :

- <xref:System.Collections.IList>interface

  Une classe qui implémente l' <xref:System.Collections.IList> interface peut <xref:System.Array>être, <xref:System.Collections.ArrayList>ou <xref:System.Collections.CollectionBase>. Il s’agit de listes indexées d’éléments <xref:System.Object>de type. Ces listes doivent contenir des types homogènes, car le premier élément de l’index détermine le type. <xref:System.Collections.IList>peut être uniquement disponible pour la liaison au moment de l’exécution.

  > [!NOTE]
  > Si vous souhaitez créer une liste d’objets métier pour la liaison avec Windows Forms, vous devez envisager d’utiliser <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Est une classe extensible qui implémente les interfaces principales requises pour la liaison de données bidirectionnelle Windows Forms.

- <xref:System.ComponentModel.IBindingList>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IBindingList> interface fournit un niveau de fonctionnalité de liaison de données bien plus élevé. Cette implémentation fournit des fonctionnalités de tri de base et une notification des modifications, à la fois lorsque la liste des éléments change (par exemple, le champ Adresse du troisième élément d’une liste de clients change) et lorsque la liste elle-même change (par exemple, augmentation ou diminution du nombre d’éléments de la liste). La notification des modifications est importante si vous prévoyez de lier plusieurs contrôles aux mêmes données et si vous souhaitez que les modifications apportées aux données d’un contrôle se propagent à d’autres contrôles liés.

  > [!NOTE]
  > La notification de modification est activée <xref:System.ComponentModel.IBindingList> pour l’interface <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> via la propriété qui `true`, lorsque, <xref:System.ComponentModel.IBindingList.ListChanged> déclenche un événement, indiquant que la liste a été modifiée ou qu’un élément de la liste a été modifié.

  Le type de modification est décrit par la <xref:System.ComponentModel.ListChangedType> propriété <xref:System.ComponentModel.ListChangedEventArgs> du paramètre. Par conséquent, à chaque mise à jour du modèle de données, toutes les vues dépendantes, comme les autres contrôles liés à la même source de données, seront également mises à jour. Toutefois, les objets contenus dans la liste devront notifier la liste lorsqu’ils changent afin que la liste puisse déclencher l' <xref:System.ComponentModel.IBindingList.ListChanged> événement.

  > [!NOTE]
  > Fournit une implémentation générique de l' <xref:System.ComponentModel.IBindingList> interface. <xref:System.ComponentModel.BindingList%601>

- <xref:System.ComponentModel.IBindingListView>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IBindingListView> interface fournit toutes les fonctionnalités d’une implémentation de <xref:System.ComponentModel.IBindingList>, ainsi que des fonctionnalités de filtrage et de tri avancé. Cette implémentation offre un filtrage basé sur les chaînes ainsi que le tri multicolonne avec des paires direction-descripteur de propriété.

- <xref:System.ComponentModel.IEditableObject>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IEditableObject> interface permet à un objet de contrôler le moment où les modifications apportées à cet objet sont rendues permanentes. Cette implémentation vous permet d’utiliser <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>les <xref:System.ComponentModel.IEditableObject.EndEdit%2A>méthodes, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> et, qui vous permettent de restaurer les modifications apportées à l’objet. Voici une brève explication du fonctionnement des <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> méthodes, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>et et de la façon dont elles fonctionnent conjointement les unes avec les autres pour permettre une restauration possible des modifications apportées aux données:

  - La <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> méthode signale le début d’une modification sur un objet. Un objet qui implémente cette interface doit stocker toutes les mises à jour après l’appel <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> de la méthode de telle sorte que les mises à jour puissent être ignorées si la <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> méthode est appelée. Dans Windows Forms de liaison de données, vous <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> pouvez appeler plusieurs fois dans l’étendue d’une seule transaction de modification ( <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>par <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>exemple <xref:System.ComponentModel.IEditableObject.EndEdit%2A>,,,). Les implémentations <xref:System.ComponentModel.IEditableObject> de doivent suivre si <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> a déjà été appelé et ignorer les appels suivants à <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Étant donné que cette méthode peut être appelée plusieurs fois, il est important que les appels suivants à celle-ci soient non destructifs; autrement dit, les <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> appels suivants ne peuvent pas détruire les mises à jour apportées ou modifier les données qui ont été enregistrées <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> lors du premier appel.

  - La <xref:System.ComponentModel.IEditableObject.EndEdit%2A> méthode exécute un push des modifications <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> apportées depuis que a été appelé dans l’objet sous-jacent, si l’objet est actuellement en mode édition.

  - La <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> méthode ignore toutes les modifications apportées à l’objet.

  Pour plus d’informations sur le <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>fonctionnement <xref:System.ComponentModel.IEditableObject.EndEdit%2A>des méthodes <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> , et, consultez [enregistrer des données dans la base de données](/visualstudio/data-tools/save-data-back-to-the-database).

  Cette notion transactionnelle des fonctionnalités de données est utilisée par le <xref:System.Windows.Forms.DataGridView> contrôle.

- <xref:System.ComponentModel.ICancelAddNew>interface

  Une classe qui implémente l' <xref:System.ComponentModel.ICancelAddNew> interface implémente généralement l' <xref:System.ComponentModel.IBindingList> interface et vous permet de restaurer un ajout effectué à la source de données avec la <xref:System.ComponentModel.IBindingList.AddNew%2A> méthode. Si votre source de données implémente <xref:System.ComponentModel.IBindingList> l’interface, vous devez également l' <xref:System.ComponentModel.ICancelAddNew> implémenter.

- <xref:System.ComponentModel.IDataErrorInfo>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IDataErrorInfo> interface permet aux objets d’offrir des informations d’erreur personnalisées aux contrôles liés:

  - La <xref:System.ComponentModel.IDataErrorInfo.Error%2A> propriété retourne le texte général du message d’erreur (par exemple, «une erreur s’est produite»).

  - La <xref:System.ComponentModel.IDataErrorInfo.Item%2A> propriété retourne une chaîne avec le message d’erreur spécifique de la colonne (par exemple, «la valeur dans `State` la colonne n’est pas valide»).

- <xref:System.Collections.IEnumerable>interface

  Une classe qui implémente l' <xref:System.Collections.IEnumerable> interface est généralement consommée par ASP.net. La prise en charge de Windows Forms pour cette interface est <xref:System.Windows.Forms.BindingSource> disponible uniquement via le composant.

  > [!NOTE]
  > Le <xref:System.Windows.Forms.BindingSource> composant copie tous <xref:System.Collections.IEnumerable> les éléments dans une liste distincte à des fins de liaison.

- <xref:System.ComponentModel.ITypedList>interface

  Une classe de collections qui implémente <xref:System.ComponentModel.ITypedList> l’interface donne la possibilité de contrôler l’ordre et l’ensemble des propriétés exposées au contrôle lié.

  > [!NOTE]
  > Lorsque vous implémentez <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> la méthode et que <xref:System.ComponentModel.PropertyDescriptor> le tableau n’a pas la valeur null, la dernière entrée du tableau est le descripteur de propriété qui décrit la propriété de liste qui est une autre liste d’éléments.

- <xref:System.ComponentModel.ICustomTypeDescriptor>interface

  Une classe qui implémente l' <xref:System.ComponentModel.ICustomTypeDescriptor> interface fournit des informations dynamiques à propos de lui-même. Cette interface est similaire à <xref:System.ComponentModel.ITypedList> , mais elle est utilisée pour les objets plutôt que pour les listes. Cette interface est utilisée par <xref:System.Data.DataRowView> pour projeter le schéma des lignes sous-jacentes. Une implémentation simple de <xref:System.ComponentModel.ICustomTypeDescriptor> est fournie par la <xref:System.ComponentModel.CustomTypeDescriptor> classe.

  > [!NOTE]
  > Pour prendre en charge la liaison au moment du design <xref:System.ComponentModel.ICustomTypeDescriptor>aux types qui implémentent, <xref:System.ComponentModel.IComponent> le type doit également implémenter et exister en tant qu’instance sur le formulaire.

- <xref:System.ComponentModel.IListSource>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IListSource> interface active la liaison basée sur la liste sur les objets non listés. La <xref:System.ComponentModel.IListSource.GetList%2A> méthode de <xref:System.ComponentModel.IListSource> est utilisée pour retourner une liste pouvant être liée à partir d’un objet qui n' <xref:System.Collections.IList>hérite pas de. <xref:System.ComponentModel.IListSource>est utilisé par la <xref:System.Data.DataSet> classe.

- <xref:System.ComponentModel.IRaiseItemChangedEvents>interface

  Une classe qui implémente l' <xref:System.ComponentModel.IRaiseItemChangedEvents> interface est une liste pouvant être liée qui implémente également <xref:System.ComponentModel.IBindingList> l’interface. Cette interface est utilisée pour indiquer si votre type déclenche <xref:System.ComponentModel.IBindingList.ListChanged> des événements de <xref:System.ComponentModel.ListChangedType.ItemChanged> type par <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> le biais de sa propriété.

  > [!NOTE]
  > Vous devez implémenter <xref:System.ComponentModel.IRaiseItemChangedEvents> le si votre source de données fournit la conversion d’événement de la propriété à la liste décrite précédemment <xref:System.Windows.Forms.BindingSource> et interagit avec le composant. Dans le cas <xref:System.Windows.Forms.BindingSource> contraire, le exécute également la propriété pour répertorier la conversion d’événements, ce qui ralentit les performances.

- <xref:System.ComponentModel.ISupportInitialize>interface

  Un composant qui implémente l' <xref:System.ComponentModel.ISupportInitialize> interface tire parti des optimisations par lots pour définir des propriétés et initialiser des propriétés codépendantes. Le <xref:System.ComponentModel.ISupportInitialize> contient deux méthodes:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>signale que l’initialisation de l’objet démarre.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>signale que l’initialisation de l’objet se termine.

- <xref:System.ComponentModel.ISupportInitializeNotification>interface

  Un composant qui implémente l' <xref:System.ComponentModel.ISupportInitializeNotification> interface implémente également l' <xref:System.ComponentModel.ISupportInitialize> interface. Cette interface vous permet de notifier <xref:System.ComponentModel.ISupportInitialize> d’autres composants que l’initialisation est terminée. L' <xref:System.ComponentModel.ISupportInitializeNotification> interface contient deux membres:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>retourne une `boolean` valeur indiquant si le composant est initialisé.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized>se produit <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> lorsque est appelé.

- <xref:System.ComponentModel.INotifyPropertyChanged>interface

  Une classe qui implémente cette interface est un type qui déclenche un événement lorsqu’une de ses valeurs de propriété change. Cette interface est conçue pour remplacer le modèle d’événement de modification pour chaque propriété d’un contrôle. Lorsqu’il est utilisé <xref:System.ComponentModel.BindingList%601>dans un, un objet métier doit <xref:System.ComponentModel.INotifyPropertyChanged> implémenter l’interface\`et le BindingList <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 1 convertira les événements <xref:System.ComponentModel.ListChangedType.ItemChanged>en <xref:System.ComponentModel.BindingList%601.ListChanged> événements de type.

  > [!NOTE]
  > Pour que la notification de modification se produise dans une liaison entre un client lié et une source de données, votre type de source <xref:System.ComponentModel.INotifyPropertyChanged> de données liée doit implémenter l’interface (par défaut) ou vous pouvez fournir des événements *PropertyName* `Changed` pour le type lié, mais vous ne devez pas faire les deux.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfaces pour implémentation par des auteurs de composants

Les interfaces suivantes sont conçues pour une utilisation par le moteur de liaison de données Windows Forms :

- <xref:System.Windows.Forms.IBindableComponent>interface

  Une classe qui implémente cette interface est un composant qui n’est pas un contrôle et qui prend en charge la liaison de données. Cette classe retourne les liaisons de données et le contexte de liaison du composant via <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> les <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> propriétés et de cette interface.

  > [!NOTE]
  > Si votre composant hérite de <xref:System.Windows.Forms.Control>, il n’est pas nécessaire d’implémenter l' <xref:System.Windows.Forms.IBindableComponent> interface.

- <xref:System.Windows.Forms.ICurrencyManagerProvider>interface

  Une classe qui implémente l' <xref:System.Windows.Forms.ICurrencyManagerProvider> interface est un composant qui fournit son propre <xref:System.Windows.Forms.CurrencyManager> pour gérer les liaisons associées à ce composant particulier. L’accès au personnalisé <xref:System.Windows.Forms.CurrencyManager> est fourni par la <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> propriété.

  > [!NOTE]
  > Une classe qui hérite de <xref:System.Windows.Forms.Control> gère les liaisons automatiquement par le <xref:System.Windows.Forms.Control.BindingContext%2A> biais de sa propriété, de sorte que les cas où <xref:System.Windows.Forms.ICurrencyManagerProvider> vous devez implémenter le sont assez rares.

## <a name="see-also"></a>Voir aussi

- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
- [Guide pratique : Créer un contrôle à liaison simple dans un Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
