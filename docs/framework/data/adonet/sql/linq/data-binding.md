---
title: Liaison de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: c7048d292bdf5c1372d5f8f174f7f0e84efa7593
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634714"
---
# <a name="data-binding"></a>Liaison de données

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge la liaison à des contrôles communs, tels que les contrôles Grid. Plus précisément, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit les modèles de base pour la liaison à une grille de données et le traitement de la liaison maître/détail, en ce qui concerne l’affichage et la mise à jour.

## <a name="underlying-principle"></a>Principe sous-jacent

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes LINQ en SQL pour une exécution sur une base de données. Les résultats sont des `IEnumerable` fortement typés. Étant donné que ces objets sont des objets Common Language Runtime (CLR) ordinaires, la liaison de données d'objet ordinaire peut être utilisée pour afficher les résultats. En revanche, les opérations de modification (insertions, mises à jour et suppressions) requièrent des étapes supplémentaires.

## <a name="operation"></a>Opération

La liaison implicite aux contrôles Windows Forms s’effectue en implémentant <xref:System.ComponentModel.IListSource>. Les <xref:System.Data.Linq.Table%601> génériques de sources de données C# (`Table<T>` dans ou `Table(Of T)` dans Visual Basic) et les `DataQuery` génériques ont été mis à jour pour implémenter <xref:System.ComponentModel.IListSource>. Les moteurs de liaison de données de l'interface utilisateur (UI) (Windows Forms et Windows Presentation Foundation) effectuent tous les deux un test pour vérifier si leur source de données implémente <xref:System.ComponentModel.IListSource>. Par conséquent, l’écriture d’une affectation directe d’une requête à une source de données d’un contrôle appelle implicitement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génération de collection, comme dans l’exemple suivant :

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Cela s'applique également à Windows Presentation Foundation :

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Les générations de collection sont implémentées par le <xref:System.Data.Linq.Table%601> générique et le `DataQuery` générique dans <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implémentation IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implémente <xref:System.ComponentModel.IListSource> à deux emplacements :

- La source de données est un <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] parcourt la table pour remplir un `DataBindingList` collection qui conserve une référence sur la table.

- La source de données est un <xref:System.Linq.IQueryable%601>. Il existe deux scénarios :

  - Si [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] trouve le <xref:System.Data.Linq.Table%601> sous-jacent à partir de l' <xref:System.Linq.IQueryable%601>, la source autorise l’édition et la situation est la même que dans le premier point à puce.

  - Si [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne parvient pas à trouver le <xref:System.Data.Linq.Table%601>sous-jacent, la source n’autorise pas l’édition (par exemple, `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] parcourt la requête pour remplir un `SortableBindingList`générique, qui est un <xref:System.ComponentModel.BindingList%601> simple qui implémente la fonctionnalité de tri pour les entités T pour une propriété donnée.

## <a name="specialized-collections"></a>Collections spécialisées

Pour de nombreuses fonctionnalités décrites précédemment dans ce document, <xref:System.ComponentModel.BindingList%601> a été spécialisé pour quelques classes différentes. Ces classes sont le `SortableBindingList` et le `DataBindingList` génériques. Les deux sont déclarés comme internes.

### <a name="generic-sortablebindinglist"></a>SortableBindingList générique

Cette classe hérite de <xref:System.ComponentModel.BindingList%601>et est une version triable de <xref:System.ComponentModel.BindingList%601>. Le tri est une solution en mémoire et ne contacte jamais la base de données elle-même. <xref:System.ComponentModel.BindingList%601> implémente <xref:System.ComponentModel.IBindingList>, mais ne prend pas en charge le tri par défaut. Toutefois, <xref:System.ComponentModel.BindingList%601> implémente <xref:System.ComponentModel.IBindingList> avec des méthodes de *base* virtuelles. Vous pouvez facilement substituer ces méthodes. Le `SortableBindingList` générique substitue <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A> et <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` est appelé par <xref:System.ComponentModel.IBindingList.ApplySort%2A> et trie la liste d'éléments T pour une propriété donnée.

Une exception est levée si la propriété n'appartient pas à T.

Pour obtenir le tri, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée une classe `SortableBindingList.PropertyComparer` générique qui hérite d’un <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> générique et implémente un comparateur par défaut pour un type T donné, un `PropertyDescriptor`et une direction. Cette classe crée dynamiquement un `Comparer` de T où T est le `PropertyType` de `PropertyDescriptor`. Puis le comparateur par défaut est récupéré du `Comparer` générique statique. Une instance par défaut est obtenue en utilisant la réflexion.

Le `SortableBindingList` générique est également la classe de base pour `DataBindingList`. Le `SortableBindingList` générique propose deux méthodes virtuelles pour interrompre ou continuer le suivi des ajouts/suppressions d'éléments. Ces deux méthodes peuvent être utilisées pour les fonctionnalités de base telles que le tri, mais seront réellement implémentées par les classes supérieures telles que le `DataBindingList` générique.

### <a name="generic-databindinglist"></a>DataBindingList générique

Cette classe hérite du `SortableBindingLIst` générique. Le `DataBindingList` générique garde une référence au `Table` générique sous-jacent de l'`IQueryable` générique utilisé pour remplir la première fois la collection. Le `DatabindingList` générique ajoute le suivi des ajouts/suppressions d'élément à la collection en substituant `InsertItem`() et `RemoveItem`(). Il implémente également la fonctionnalité récapitulative de suivi des interruptions/reprises pour rendre le suivi conditionnel. Avec cette fonctionnalité, le `DataBindingList` générique tire parti de toute l’utilisation polymorphe de la fonctionnalité de suivi des classes parentes.

## <a name="binding-to-entitysets"></a>Création d’une liaison à EntitySets

La création d’une liaison avec `EntitySet` est un cas spécial parce que `EntitySet` est déjà une collection qui implémente <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ajoute la prise en charge du tri et de l’annulation (<xref:System.ComponentModel.ICancelAddNew>). Une classe `EntitySet` utilise une liste interne pour stocker des entités. Cette liste est une collection de bas niveau basée sur un tableau générique, la classe `ItemList` générique.

### <a name="adding-a-sorting-feature"></a>Ajout d’une fonctionnalité de tri

Les tableaux proposent une méthode de tri (`Array.Sort()`) que vous pouvez utiliser avec un `Comparer` de T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise la classe `SortableBindingList.PropertyComparer` générique décrite précédemment dans cette rubrique pour obtenir ce `Comparer` et effectuer le tri en fonction de la propriété et de la direction. Une méthode `ApplySort` est ajoutée à l’`ItemList` générique pour appeler cette fonctionnalité.

Du côté du `EntitySet`, vous devez désormais déclarer la prise en charge du tri :

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> retourne `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> appelle `entities.ApplySort()`, puis `OnListChanged()`.

- Les propriétés <xref:System.ComponentModel.IBindingList.SortDirection%2A> et <xref:System.ComponentModel.IBindingList.SortProperty%2A> exposent la définition de tri actuelle, stockée dans les membres locaux.

Lorsque vous utilisez un System. Windows. Forms. BindingSource et liez un EntitySet\<tente > à System. Windows. Forms. BindingSource. DataSource, vous devez appeler EntitySet\<tente >. GetNewBindingList pour mettre à jour BindingSource. List.

Si vous utilisez un System. Windows. Forms. BindingSource et définissez la propriété BindingSource. DataMember, et que vous affectez à BindingSource. DataSource une classe qui a une propriété nommée dans le BindingSource. DataMember qui expose l’EntitySet\<tente >, vous n’avez pas besoin d’appeler EntitySet\<tente >. GetNewBindingList pour mettre à jour BindingSource. List, mais vous perdez la fonction de tri.

## <a name="caching"></a>Mise en cache

les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implémentent <xref:System.ComponentModel.IListSource.GetList%2A>. Lorsque la classe BindingSource Windows Forms rencontre cette interface, elle appelle GetList() trois fois pour une seule connexion. Pour contourner cette situation, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implémente un cache par instance pour stocker et retourne toujours la même collection générée.

## <a name="cancellation"></a>Annulation

<xref:System.ComponentModel.IBindingList> définit une méthode <xref:System.ComponentModel.IBindingList.AddNew%2A> utilisée par les contrôles pour créer un élément à partir d'une collection liée. Le contrôle `DataGridView` présente très bien cette fonctionnalité lorsque la dernière ligne visible contient une étoile dans son en-tête. L'étoile vous indique que vous pouvez ajouter un nouvel élément.

Outre cette fonctionnalité, une collection peut également implémenter <xref:System.ComponentModel.ICancelAddNew>. Cette fonctionnalité autorise les contrôles à annuler ou valider le fait que le nouvel élément modifié ait été validé ou pas.

<xref:System.ComponentModel.ICancelAddNew> est implémenté dans toutes les collections [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] liées aux données (`SortableBindingList` générique et `EntitySet` générique). Dans les deux implémentations, le code s'applique comme suit :

- Permet l’insertion des éléments, puis leur suppression de la collection.

- N’effectue pas le suivi des modifications tant que l’interface utilisateur ne valide pas l’édition.

- N'effectue pas le suivi des modifications tant que l'édition est annulée (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Autorise le suivi lorsque l’édition est validée (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Permet à la collection de se comporter normalement si le nouvel élément ne provient pas de <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Résolution des problèmes

Cette section appelle plusieurs éléments qui peuvent vous aider à dépanner les applications de liaison de données [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

- Vous devez utiliser des propriétés ; l'utilisation de champs uniquement n'est pas suffisante. C'est une exigence des Windows Forms.

- Par défaut, les types de bases de données `image`, `varbinary`et `timestamp` sont mappés au tableau d’octets. Comme `ToString()` n'est pas pris en charge dans ce scénario, ces objets ne peuvent pas être affichés.

- Un membre de classe mappé à une clé primaire a un accesseur Set, mais [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge le changement d’identité d’objet. Par conséquent, la clé primaire/unique utilisée dans le mappage ne peut pas être mise à jour dans la base de données. Une modification dans la grille provoque une exception lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Si une entité est liée dans deux grilles distinctes (par exemple, une grille principale et une grille de détail), une opération `Delete` dans la grille principale n'est pas propagée à la grille de détail.

## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
