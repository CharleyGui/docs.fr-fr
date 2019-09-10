---
title: Génération SQL de modification
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 94b6c3c97e8255db2dc4d72bae6c6c12905d9710
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854291"
---
# <a name="modification-sql-generation"></a>Génération SQL de modification

Cette section décrit la manière de développer un module de génération SQL de modification pour votre fournisseur (base de données conforme SQL:1999). Ce module doit traduire une arborescence de commandes de modification en instructions SQL INSERT, UPDATE ou DELETE appropriées.

Pour plus d’informations sur la génération SQL pour les instructions SELECT, consultez [génération SQL](sql-generation.md).

## <a name="overview-of-modification-command-trees"></a>Vue d’ensemble des arborescences de commandes de modification

Le module de génération SQL de modification génère des instructions SQL de modification spécifiques à la base de données selon un DbModificationCommandTree d'entrée donné.

Un DbModificationCommandTree est une représentation du modèle objet d'une opération DML de modification (opération INSERT, UPDATE ou DELETE), en héritant de DbCommandTree. Il existe trois implémentations de DbModificationCommandTree :

- DbInsertCommandTree

- DbUpdateCommandTree

- DbDeleteCommandTree

DbModificationCommandTree et ses implémentations produites par le Entity Framework représentent toujours une seule opération de ligne. Cette section décrit ces types avec leurs contraintes dans .NET Framework version 3.5.

![Diagramme](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")

DbModificationCommandTree a une propriété Target qui représente le jeu de cibles pour l'opération de modification. La propriété d'expression de la cible, qui définit le jeu de données d'entrée, est toujours DbScanExpression.  Un DbScanExpression peut représenter une table ou une vue, ou un jeu de données défini avec une requête si la propriété de métadonnées « définition de la requête » de sa cible n’a pas la valeur null.

Un DbScanExpression qui représente une requête peut atteindre un fournisseur en tant que cible de modification uniquement si le jeu a été défini à l'aide d'une requête de définition dans le modèle mais qu'aucune fonction n'a été fournie pour l'opération de modification correspondante. Il est possible que les fournisseurs ne puissent pas prendre en charge un tel scénario (par exemple, c'est le cas de SqlClient).

DbInsertCommandTree représente une opération d'insertion d'une seule ligne exprimée sous la forme d'une arborescence de commandes.

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

DbUpdateCommandTree représente une opération de mise à jour d'une seule ligne exprimée sous la forme d'une arborescence de commandes.

DbDeleteCommandTree représente une opération de suppression d'une seule ligne exprimée sous la forme d'une arborescence de commandes.

### <a name="restrictions-on-modification-command-tree-properties"></a>Restrictions sur les propriétés de l'arborescence de commandes de modification

Les informations et restrictions suivantes s’appliquent aux propriétés de l’arborescence de commandes de modification.

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Renvoi dans DbInsertCommandTree et DbUpdateCommandTree

Lorsque la valeur n'est pas null, le renvoi indique que la commande retourne un lecteur. Dans le cas contraire, la commande doit retourner une valeur scalaire qui indique le nombre de lignes affectées (insérées ou mises à jour).

La valeur du renvoi spécifie une projection de résultats à retourner selon la ligne insérée ou mise à jour. Une ligne ne peut être représentée que par le type DbNewInstanceExpression, avec chacun de ses arguments DbPropertyExpression sur un DbVariableReferenceExpression qui représente une référence à la cible du DbModificationCommandTree correspondant. Les propriétés représentées par les DbPropertyExpressions utilisés dans le renvoi de propriété sont toujours des valeurs générées ou calculées par la banque. Dans DbInsertCommandTree, le renvoi n'a pas la valeur null lorsque au moins une propriété de la table dans laquelle la ligne est insérée est spécifiée comme générée ou calculée par la banque (marquée comme StoreGeneratedPattern.Identity ou StoreGeneratedPattern.Computed dans le ssdl). Dans DbUpdateCommandTrees, le renvoi n'a pas la valeur null lorsque au moins une propriété de la table dans laquelle la ligne est mise à jour est spécifiée comme calculée par la banque (marqué comme StoreGeneratedPattern.Computed dans le ssdl).

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses dans DbInsertCommandTree et DbUpdateCommandTree

SetClauses spécifie la liste des clauses set d'insertion ou de mise à jour qui définissent l'opération d'insertion ou de mise à jour.

```
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.
```

Property spécifie la propriété à mettre à jour. Il s'agit toujours d'un DbPropertyExpression sur un DbVariableReferenceExpression, qui représente une référence à la cible du DbModificationCommandTree correspondant.

Value spécifie la nouvelle valeur avec laquelle mettre à jour la propriété. Elle est de type DbConstantExpression ou DbNullExpression.

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predicate dans DbUpdateCommandTree et DbDeleteCommandTree

Predicate spécifie le prédicat utilisé pour identifier dans la collection cible les membres à mettre à jour ou à supprimer. Il s’agit d’une arborescence de l’expression construite sur le sous-ensemble de DbExpressions suivant :

- DbComparisonExpression de genre est égal à, avec l’enfant approprié qui est un DbPropertyExpression comme restreint ci-dessous et l’enfant gauche d’un DbConstantExpression.

- DbConstantExpression

- DbIsNullExpression sur un DbPropertyExpression comme restreint ci-dessous

- DbPropertyExpression sur un DbVariableReferenceExpression qui représente une référence à la cible du DbModificationCommandTree correspondant.

- DbAndExpression

- DbNotExpression

- DbOrExpression

## <a name="modification-sql-generation-in-the-sample-provider"></a>Génération SQL de modification dans le fournisseur d'exemples

L' [exemple de fournisseur Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) illustre les composants des fournisseurs de données ADO.net qui prennent en charge l’Entity Framework. Il cible une base de données SQL Server 2005 et est implémenté comme un wrapper sur le fournisseur de données ADO.NET 2.0 System.Data.SqlClient.

Le module de génération SQL de modification du fournisseur d'exemples (situé dans le fichier SQL Generation\DmlSqlGenerator.cs) prend un DbModificationCommandTree d'entrée et produit une instruction SQL de modification unique pouvant être suivie par une instruction SELECT pour retourner un lecteur, si spécifié par le DbModificationCommandTree. Notez que la forme des commandes générées est affectée par la base de données SQL Server cible.

### <a name="helper-classes-expressiontranslator"></a>Classes d’assistance : ExpressionTranslator

ExpressionTranslator fait office de traducteur commun léger pour toutes les propriétés de l’arborescence de commandes de modification de type DbExpression. Il prend uniquement en charge la traduction des types de l’expression auxquels les propriétés de l’arborescence de commandes de modification sont contraintes et est construit en fonction de ces contraintes particulières.

Les informations suivantes décrivent la visite de types de l'expression spécifiques (les nœuds avec des traductions simples sont omis).

### <a name="dbcomparisonexpression"></a>DbComparisonExpression

Lorsque l'ExpressionTranslator est construit avec preserveMemberValues = true et lorsque la constante de droite est un DbConstantExpression (au lieu de DbNullExpression), il associe l'opérande de gauche (DbPropertyExpressions) à ce DbConstantExpression. Cela est utilisé si une instruction SELECT de renvoi doit être générée pour identifier la ligne affectée.

### <a name="dbconstantexpression"></a>DbConstantExpression

Pour chaque constante visitée un paramètre est créé.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Étant donné que l'instance de DbPropertyExpression représente toujours la table d'entrée, sauf si la génération a créé un alias (ce qui se produit seulement pour les scénarios de mise à jour lorsqu'une variable de table est utilisée), aucun alias ne doit être spécifié pour l'entrée, la traduction par défaut est le nom de la propriété.

## <a name="generating-an-insert-sql-command"></a>Génération d'une commande SQL d'insertion

Pour un DbInsertCommandTree donné dans le fournisseur d'exemples, la commande d'insertion générée suit l'un des deux modèles d'insertion ci-dessous.

Le premier modèle possède une commande pour effectuer l'insertion selon les valeurs de la liste de SetClauses et une instruction SELECT pour retourner les propriétés spécifiées dans la propriété Returning pour la ligne insérée, si la propriété Returning n'a pas la valeur null. L’élément de prédicat «\@ @ROWCOUNT > 0 » a la valeur true si une ligne a été insérée. L’élément de prédicat « keyMemberI = keyValueI &#124; SCOPE_IDENTITY () » prend la forme « keyMemberI = SCOPE_IDENTITY () » uniquement si keyMemberI est une clé générée par le magasin, car SCOPE_IDENTITY () retourne la dernière valeur d’identité insérée dans une identité ( colonne générée par le magasin).

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Le deuxième modèle est nécessaire si l'insertion spécifie une insertion de ligne à l'endroit où la clé primaire est générée par la banque mais n'est pas de type entier et par conséquent ne peut pas être utilisée avec scope_identity()). Il est également utilisé s'il s'agit d'une clé composée générée par la banque.

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

Voici un exemple qui utilise le modèle inclus avec le fournisseur d'exemples. Il génère une commande d'insertion d'un DbInsertCommandTree.

Le code suivant insère une catégorie :

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

Ce code produit l’arborescence de commandes suivante, passée au fournisseur :

```
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

La commande de stockage que le fournisseur d'exemples produit est l'instruction SQL suivante :

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a>Génération d'une commande SQL de mise à jour

Pour un DbUpdateCommandTree donné, la commande de mise à jour générée est basée sur le modèle suivant :

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

La clause SET contient la clause d’ensemble factice (@i « = 0 ») uniquement si aucune clause SET n’est spécifiée. Ceci permet de vérifier que toutes les colonnes calculées par la banque sont recalculées.

Uniquement si la propriété Returning n'a pas la valeur null, une instruction SELECT est générée pour retourner les propriétés spécifiées dans la propriété Returning.

L'exemple suivant utilise le modèle inclus avec le fournisseur d'exemples pour générer une commande de mise à jour.

Le code utilisateur suivant met à jour une catégorie :

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

Ce code utilisateur produit l’arborescence de commandes suivante, passée au fournisseur :

```
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

Le fournisseur d'exemples produit la commande de stockage suivante :

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a>Génération d'une commande SQL de suppression

Pour un DbDeleteCommandTree donné, la commande DELETE générée est basée sur le modèle suivant :

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

L'exemple suivant utilise le modèle inclus avec le fournisseur d'exemples pour générer une commande de suppression.

Le code utilisateur suivant supprime une catégorie :

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

Ce code utilisateur produit l’arborescence de commandes suivante, passée au fournisseur.

```
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

La commande de stockage suivante est produite par le fournisseur d'exemples :

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a>Voir aussi

- [Écriture d’un fournisseur de données Entity Framework](writing-an-ef-data-provider.md)
