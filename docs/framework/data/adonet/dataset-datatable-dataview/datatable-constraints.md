---
title: Contraintes de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151284"
---
# <a name="datatable-constraints"></a>Contraintes de DataTable
Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données. Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée. Les contraintes sont `System.Data.DataSet.EnforceConstraints` appliquées <xref:System.Data.DataSet> lorsque la propriété de la est **vraie**. Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>. Par défaut, les deux contraintes sont créées automatiquement lorsque vous <xref:System.Data.DataRelation> créez une relation entre deux tables ou plus en ajoutant un à la **DataSet**. Cependant, vous pouvez désactiver ce comportement en spécifiant **createConstraints** = **faux** lors de la création de la relation.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 Un **ForeignKeyConstraint** applique les règles sur la façon dont les mises à jour et les suppressions aux tables connexes sont propagées. Par exemple, si une valeur dans une rangée d’une table est mise à jour ou supprimée, et que cette même valeur est également utilisée dans une ou plusieurs tables connexes, un **ForeignKeyConstraint** détermine ce qui se passe dans les tableaux connexes.  
  
 Les <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriétés et les propriétés du **ForeignKeyConstraint** définissent l’action à prendre lorsque l’utilisateur tente de supprimer ou de mettre à jour une ligne dans un tableau connexe. Le tableau suivant décrit les différents paramètres disponibles pour les propriétés **DeleteRule** et **UpdateRule** de la **ForeignKeyConstraint**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Cascade**|Supprime ou met à jour les lignes connexes.|  
|**SetNull**|Définir des valeurs dans les lignes connexes à **DBNull**.|  
|**SetDefault SetDefault**|Définit les valeurs des lignes connexes sur la valeur par défaut.|  
|**Aucun**|N'effectue aucune action sur les lignes connexes. Il s’agit de la valeur par défaut.|  
  
 Un **ForeignKeyConstraint** peut restreindre, ainsi que la propagation, des modifications aux colonnes connexes. Selon les propriétés définies pour le **ForeignKeyConstraint** d’une colonne, si la propriété **EnforceConstraints** du **DataSet** est **vrai,** effectuer certaines opérations sur la ligne mère entraînera une exception. Par exemple, si la propriété **DeleteRule** de la **ForeignKeyConstraint** **n’est pas,** une rangée de parents ne peut pas être supprimée si elle a des rangées d’enfants.  
  
 Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes en utilisant le constructeur **ForeignKeyConstraint.** Passer l’objet **ForeignKeyConstraint** résultant à la méthode **Add** de la propriété **Contraintes** de la table, qui est une **contrainteCollection**. Vous pouvez également passer des arguments constructeurs à plusieurs surcharges de la méthode **Add** d’une **contraintecollection** pour créer un **ForeignKeyConstraint**.  
  
 Lors de la création **d’un ForeignKeyConstraint**, vous pouvez passer les valeurs **DeleteRule** et **UpdateRule** au constructeur comme arguments, ou vous pouvez les définir comme propriétés comme dans l’exemple suivant (où la valeur **DeleteRule** est définie à **Aucun**).  
  
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
 Les modifications apportées aux lignes peuvent être acceptées à l’aide de la méthode **AcceptChanges** ou annulées à l’aide de la méthode **RejectChanges** du **DataSet**, **DataTable**ou **DataRow**. Lorsqu’un **DataSet** contient **ForeignKeyConstraints**, invoquant les méthodes **AcceptChanges** ou **RejectChanges** applique **l’AcceptRejectRule**. La propriété **AcceptRejectRule** du **ForeignKeyConstraint** détermine quelles mesures seront prises sur les rangées d’enfants lorsque **AcceptChanges** ou **RejectChanges** sont appelés sur la ligne des parents.  
  
 Le tableau suivant répertorie les paramètres disponibles pour **l’AcceptRejectRule**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Cascade**|Accepte ou rejette les modifications des lignes enfants.|  
|**Aucun**|N'effectue aucune action sur les lignes enfants. Il s’agit de la valeur par défaut.|  
  
### <a name="example"></a> Exemple  
 L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **L’objet UniqueConstraint,** qui peut être attribué soit à une seule colonne ou à un tableau de colonnes dans un **DataTable**, garantit que toutes les données dans la colonne ou les colonnes spécifiées sont uniques par rangée. Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes en utilisant le constructeur **UniqueConstraint.** Passer l’objet **UniqueConstraint** résultant à la méthode **Add** de la propriété **Contraintes** de la table, qui est une **contrainteCollection**. Vous pouvez également passer des arguments constructeurs à plusieurs surcharges de la méthode **Add** d’une **contraintecollection** pour créer un **UniqueConstraint**. Lors de la création **d’un UniqueConstraint** pour une colonne ou des colonnes, vous pouvez choisir si la colonne ou les colonnes sont une clé principale.  
  
 Vous pouvez également créer une contrainte unique pour une colonne en définissant la propriété **unique** de la colonne à **vrai**. Alternativement, le réglage de la propriété **unique** d’une seule colonne à **faux** supprime toute contrainte unique qui peut exister. Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées. Si vous supprimez une colonne de la propriété **PrimaryKey** d’un **DataTable**, **l’UniqueConstraint** est supprimé.  
  
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
