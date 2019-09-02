---
title: Fusion de contenu de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: e5a8040a803fbc9b098fc1b56e0f5d837c4cdb94
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203363"
---
# <a name="merging-dataset-contents"></a>Fusion de contenu de DataSet

Vous pouvez utiliser la méthode <xref:System.Data.DataSet.Merge%2A> pour fusionner le contenu d'un tableau <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> dans un `DataSet` existant. La façon dont les nouvelles données sont fusionnées dans un `DataSet` existant dépend de plusieurs facteurs et options.

## <a name="primary-keys"></a>Clés primaires

Si la table qui reçoit les nouvelles données et informations de schéma suite à une fusion dispose d’une clé primaire, les nouvelles lignes des données entrantes sont mises en correspondance avec les lignes existantes ayant les mêmes valeurs de clé primaire <xref:System.Data.DataRowVersion.Original> que celles des données entrantes. Si les colonnes du schéma entrant correspondent à celles du schéma existant, les données des lignes existantes sont modifiées. Les colonnes qui ne correspondent pas au schéma existant sont soit ignorées soit ajoutées en fonction du paramètre <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A>. Les nouvelles lignes dont les valeurs de clé primaire ne correspondent à aucune ligne existante sont ajoutées à la table existante.

Si des lignes entrantes ou existantes présentent un état de ligne <xref:System.Data.DataRowState.Added>, leurs valeurs de clé primaire sont mises en correspondance à l'aide de la valeur de clé primaire <xref:System.Data.DataRowVersion.Current> de la ligne `Added` car il n'existe pas de version `Original` de ces lignes.

Si une table entrante et une table existante contiennent une colonne du même nom, mais dont le type de données diffère, une exception est levée et l'événement <xref:System.Data.DataSet.MergeFailed> du `DataSet` est déclenché. Si une table entrante et une table existante contiennent toutes deux des clés définies, mais si les clés primaires s'appliquent à des colonnes différentes, une exception est levée et l'événement `MergeFailed` du `DataSet` est déclenché.

Si aucune clé primaire n'est définie dans la table qui reçoit les nouvelles données suite à une fusion, les nouvelles lignes des données entrantes ne peuvent pas être mises en correspondance avec les lignes existantes de la table et sont alors ajoutées à la table existante.

## <a name="table-names-and-namespaces"></a>Noms de tables et espaces de noms

Une valeur de propriété <xref:System.Data.DataTable> peut être assignée à un objet <xref:System.Data.DataTable.Namespace%2A>. Lorsque des valeurs de propriété <xref:System.Data.DataTable.Namespace%2A> sont assignées, un <xref:System.Data.DataSet> peut contenir plusieurs objets <xref:System.Data.DataTable> avec la même valeur de propriété <xref:System.Data.DataTable.TableName%2A>. Au cours des opérations de fusion, les propriétés <xref:System.Data.DataTable.TableName%2A> et <xref:System.Data.DataTable.Namespace%2A> sont toutes deux utilisées pour identifier la cible d'une fusion. Si aucune propriété <xref:System.Data.DataTable.Namespace%2A> n’a été assignée, seule la propriété <xref:System.Data.DataTable.TableName%2A> est utilisée pour identifier la cible d’une fusion.

> [!NOTE]
> Ce comportement est modifié dans la version 2.0 du .NET Framework. Dans la version 1.1, les espaces de noms étaient pris en charge mais étaient ignorés au cours des opérations de fusion. C'est pourquoi, un objet <xref:System.Data.DataSet> qui utilise les valeurs de propriété <xref:System.Data.DataTable.Namespace%2A> aura des comportements différents selon la version du .NET Framework qui est exécutée. Prenons par exemple deux `DataSets` contenant des `DataTables` avec les mêmes valeurs de propriété <xref:System.Data.DataTable.TableName%2A> mais des valeurs de propriété <xref:System.Data.DataTable.Namespace%2A> différentes. Dans la version 1.1 du .NET Framework, les noms <xref:System.Data.DataTable.Namespace%2A> différents seront ignorés lors de la fusion de deux objets <xref:System.Data.DataSet>. Toutefois, à partir de la version 2.0, la fusion entraîne la création de deux `DataTables` dans le <xref:System.Data.DataSet> cible. Les `DataTables` d'origine ne seront pas affectés par la fusion.

## <a name="preservechanges"></a>PreserveChanges

Lorsque vous passez un tableau `DataSet`, `DataTable` ou `DataRow` à la méthode `Merge`, vous pouvez inclure des paramètres facultatifs pour indiquer s'il convient ou non de conserver les modifications dans le `DataSet` existant et comment gérer les nouveaux éléments de schéma situés dans les données entrantes. Le premier de ces paramètres après les données entrantes est un indicateur booléen, <xref:System.Data.LoadOption.PreserveChanges>, qui indique si les modifications seront ou non conservées dans le `DataSet` existant. Si l'indicateur `PreserveChanges` a la valeur `true`, les valeurs entrantes ne remplacent pas les valeurs existantes dans la version `Current` de la ligne existante. Si l'indicateur `PreserveChanges` a la valeur `false`, les valeurs entrantes remplacent les valeurs existantes dans la version `Current` de la ligne existante. Si l'indicateur `PreserveChanges` n'est pas spécifié, il a par défaut la valeur `false`. Pour plus d’informations sur les versions de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).

Lorsque `PreserveChanges` a la valeur `true`, les données de la ligne existante sont conservées dans la version <xref:System.Data.DataRowVersion.Current> de la ligne existante, alors que les données de la version <xref:System.Data.DataRowVersion.Original> de la ligne existante sont remplacées par les données de la version `Original` de la ligne entrante. La propriété <xref:System.Data.DataRow.RowState%2A> de la ligne existante prend la valeur <xref:System.Data.DataRowState.Modified>. Il existe toutefois certaines exceptions :

- Si le `RowState` de la ligne existante est `Deleted`, ce `RowState` reste `Deleted` et ne prend pas la valeur `Modified`. Dans ce cas, les données de la ligne entrante seront stockées dans la version `Original` de la ligne existante, remplaçant ainsi la version `Original` de la ligne existante (sauf si le `RowState` de la ligne entrante est `Added`).

- Si le `RowState` de la ligne entrante est `Added`, les données de la version `Original` de la ligne existante ne seront pas remplacées par les données de la ligne entrante car cette dernière n'a pas de version de ligne `Original`.

Lorsque `PreserveChanges` a la valeur `false`, les versions `Current` et `Original` de ligne existante sont remplacées par les données de la ligne entrante et le `RowState` de la ligne existante prend la valeur du `RowState` de la ligne entrante. Il existe toutefois certaines exceptions :

- Si le `RowState` de la ligne entrante est `Unchanged` et si le `RowState` de la ligne existante est `Modified`, `Deleted` ou `Added`, le `RowState` de la ligne existante prend la valeur `Modified`.

- Si le `RowState` de la ligne entrante est `Added` et si le `RowState` de la ligne existante est `Unchanged`, `Modified` ou `Deleted`, le `RowState` de la ligne existante prend la valeur `Modified`. De même, les données de la version `Original` de la ligne existante ne sont pas remplacées par les données de la ligne entrante car cette dernière n'a pas de version de ligne `Original`.

## <a name="missingschemaaction"></a>MissingSchemaAction

Vous pouvez utiliser le paramètre facultatif <xref:System.Data.MissingSchemaAction> de la méthode `Merge` pour spécifier comment `Merge` va gérer les éléments de schéma présents dans les données entrantes et qui ne font pas partie du `DataSet` existant.

Le tableau suivant décrit les options de `MissingSchemaAction`.

|Option MissingSchemaAction|Description|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Ajoute les nouvelles informations de schéma au `DataSet` et remplit les nouvelles colonnes avec les valeurs entrantes. Il s'agit de la valeur par défaut.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Ajoute les nouvelles informations de schéma et de clé primaire au `DataSet` et remplit les nouvelles colonnes avec les valeurs entrantes.|
|<xref:System.Data.MissingSchemaAction.Error>|Lève une exception si une incompatibilité au niveau des informations de schéma est détectée.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignore les nouvelles informations de schéma.|

## <a name="constraints"></a>Contraintes

Avec la méthode`Merge`, la vérification des contraintes ne s'effectue qu'une fois toutes les nouvelles données ajoutées au `DataSet` existant. Les contraintes sont alors appliquées aux valeurs actuelles du `DataSet`. Vous devez veiller à ce que votre code gère les exceptions levées en cas de violations des contraintes.

Prenons l'exemple d'une ligne `DataSet` existante d'un `Unchanged` dont la valeur de clé primaire est 1. Au cours d'une opération de fusion avec une ligne `Modified` entrante dont la valeur de clé primaire `Original` est 2 et la valeur de clé primaire `Current` est 1, la ligne existante et la ligne entrante ne sont pas mises en correspondance car les valeurs de clé primaire `Original` diffèrent. Cependant, lorsque la fusion est terminée et la vérification des contraintes effectuée, une exception est levée car les valeurs de clé primaire `Current` enfreignent la contrainte unique définie pour la colonne de clé primaire.

> [!NOTE]
> Lorsque des lignes sont insérées dans une table de base de données contenant une colonne à incrémentation automatique comme une colonne d’identité, la valeur de colonne d’identité retournée par l’insertion peut ne pas correspondre à la valeur du `DataSet`, ce qui conduit à l’ajout des lignes retournées et non à leur fusion. Pour plus d’informations, consultez récupération d’une [identité ou de valeurs NuméroAuto](../retrieving-identity-or-autonumber-values.md).

L’exemple de code suivant fusionne `DataSet` deux objets avec des schémas différents en `DataSet` un seul avec les schémas combinés des deux objets `DataSet` entrants.

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

L'exemple de code suivant prend un `DataSet` existant avec des mises à jour et passe ces mises à jour à un `DataAdapter` pour qu'elles soient traitées au niveau de la source de données. Les résultats sont ensuite fusionnés dans le `DataSet` d’origine. Après rejet des modifications ayant abouti à une erreur, les modifications fusionnées sont validées avec `AcceptChanges`.

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]

## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [États des lignes et versions des lignes](row-states-and-row-versions.md)
- [DataAdapters et DataReaders](../dataadapters-and-datareaders.md)
- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Récupération de valeurs d’identité ou de numérotation automatique](../retrieving-identity-or-autonumber-values.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
