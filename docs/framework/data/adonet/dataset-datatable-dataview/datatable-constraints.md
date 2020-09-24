---
title: Contraintes de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 1224518a9a16f48f770b6839317b9787da97377b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153272"
---
# <a name="datatable-constraints"></a>Contraintes de DataTable

Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données. Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée. Les contraintes sont appliquées lorsque la `System.Data.DataSet.EnforceConstraints` propriété de a la <xref:System.Data.DataSet> **valeur true**. Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>. Par défaut, les deux contraintes sont créées automatiquement lorsque vous créez une relation entre deux tables ou plus en ajoutant un <xref:System.Data.DataRelation> au **DataSet**. Toutefois, vous pouvez désactiver ce comportement en spécifiant **createConstraints**  =  **false** lors de la création de la relation.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  

 Un **ForeignKeyConstraint** applique des règles sur la façon dont les mises à jour et les suppressions des tables associées sont propagées. Par exemple, si une valeur dans une ligne d’une table est mise à jour ou supprimée et que cette même valeur est également utilisée dans une ou plusieurs tables associées, un **ForeignKeyConstraint** détermine ce qui se passe dans les tables associées.  
  
 Les <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> Propriétés et du **ForeignKeyConstraint** définissent l’action à entreprendre lorsque l’utilisateur tente de supprimer ou de mettre à jour une ligne dans une table associée. Le tableau suivant décrit les différents paramètres disponibles pour les propriétés **DeleteRule** et **UpdateRule** de **ForeignKeyConstraint**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Répercuté**|Supprime ou met à jour les lignes connexes.|  
|**SetNull**|Définissez les valeurs des lignes connexes sur **DBNull**.|  
|**SetDefault**|Définit les valeurs des lignes connexes sur la valeur par défaut.|  
|**Aucun**|N'effectue aucune action sur les lignes connexes. Il s’agit de la valeur par défaut.|  
  
 Un **ForeignKeyConstraint** peut restreindre, ainsi que propager, les modifications apportées aux colonnes associées. En fonction des propriétés définies pour le **ForeignKeyConstraint** d’une colonne, si la propriété **EnforceConstraints** du jeu de **données** a la **valeur true**, l’exécution de certaines opérations sur la ligne parente entraîne une exception. Par exemple, si la propriété **DeleteRule** de **ForeignKeyConstraint** a la valeur **None**, une ligne parente ne peut pas être supprimée si elle contient des lignes enfants.  
  
 Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes à l’aide du constructeur **ForeignKeyConstraint** . Transmettez l’objet **ForeignKeyConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**. Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d’un **ConstraintCollection** pour créer un **ForeignKeyConstraint**.  
  
 Lors de la création d’un **ForeignKeyConstraint**, vous pouvez passer les valeurs de **DeleteRule** et **UpdateRule** comme arguments au constructeur, ou vous pouvez les définir comme des propriétés comme dans l’exemple suivant (où **DeleteRule** a la valeur **None**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  

 Les modifications apportées aux lignes peuvent être acceptées à l’aide de la méthode **AcceptChanges** ou annulées à l’aide de la méthode **RejectChanges** du **DataSet**, du **DataTable**ou de **DataRow**. Lorsqu’un **jeu de données** contient des **ForeignKeyConstraints**, l’appel des méthodes **AcceptChanges** ou **RejectChanges** applique la méthode **AcceptRejectRule**. La propriété **AcceptRejectRule** de **ForeignKeyConstraint** détermine l’action qui sera entreprise sur les lignes enfants lorsque **AcceptChanges** ou **RejectChanges** est appelé sur la ligne parente.  
  
 Le tableau suivant répertorie les paramètres disponibles pour **AcceptRejectRule**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Répercuté**|Accepte ou rejette les modifications des lignes enfants.|  
|**Aucun**|N'effectue aucune action sur les lignes enfants. Il s’agit de la valeur par défaut.|  
  
### <a name="example"></a>Exemple  

 L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  

 L’objet **UniqueConstraint** , qui peut être assigné à une colonne unique ou à un tableau de colonnes dans un **DataTable**, garantit que toutes les données de la colonne ou des colonnes spécifiées sont uniques par ligne. Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes à l’aide du constructeur **UniqueConstraint** . Transmettez l’objet **UniqueConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**. Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d’un **ConstraintCollection** pour créer un **UniqueConstraint**. Lorsque vous créez un **UniqueConstraint** pour une ou plusieurs colonnes, vous pouvez éventuellement spécifier si la ou les colonnes sont une clé primaire.  
  
 Vous pouvez également créer une contrainte unique pour une colonne en attribuant la **valeur true**à la propriété **unique** de la colonne. Sinon, l’affectation de la **valeur false** à la propriété **unique** d’une seule colonne supprime toute contrainte unique qui peut exister. Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées. Si vous supprimez une colonne de la propriété **PrimaryKey** d’un **DataTable**, **UniqueConstraint** est supprimé.  
  
 L’exemple suivant crée un **UniqueConstraint** pour deux colonnes d’un **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]
    {custTable.Columns["CustomerID"],
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Définition de schéma de DataTable](datatable-schema-definition.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
