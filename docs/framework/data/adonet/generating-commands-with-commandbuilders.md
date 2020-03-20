---
title: Génération de commandes avec CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 76c2a6cb0661a0e39fc3a0dd599fcbb3c046f382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149610"
---
# <a name="generating-commands-with-commandbuilders"></a>Génération de commandes avec CommandBuilders
Lorsque la propriété `SelectCommand` est spécifiée de manière dynamique au moment de l'exécution, par l'intermédiaire d'un outil de requête qui prend une commande textuelle provenant de l'utilisateur par exemple, il est possible que vous ne puissiez pas spécifier les propriétés `InsertCommand`, `UpdateCommand` ou `DeleteCommand` appropriées au moment de la conception. Si l'objet <xref:System.Data.DataTable> est mappé à une table de base de données unique ou est généré par elle, vous pouvez tirer parti de l'objet <xref:System.Data.Common.DbCommandBuilder> pour générer automatiquement les propriétés `DeleteCommand`, `InsertCommand` et `UpdateCommand` de l'objet <xref:System.Data.Common.DbDataAdapter>.  
  
 Vous devez au minimum définir la propriété `SelectCommand` afin que la génération de automatique de commandes fonctionne. Le schéma de table extrait par la propriété `SelectCommand` détermine la syntaxe des instructions INSERT, UPDATE et DELETE générées automatiquement.  
  
 L'objet <xref:System.Data.Common.DbCommandBuilder> doit exécuter `SelectCommand` afin de retourner les métadonnées nécessaires à la construction des commandes INSERT, UPDATE et DELETE SQL. En conséquence, un trajet supplémentaire vers la source de données est nécessaire et peut gêner les performances. Pour parvenir à une performance optimale, spécifiez vos commandes explicitement plutôt que d'utiliser l'objet <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` doit aussi retourner au moins une clé primaire ou une colonne unique. Si aucune n'est présente, une exception `InvalidOperation` est levée et les commandes ne sont pas générées.  
  
 Lorsqu'il est associé à `DataAdapter`, l'objet <xref:System.Data.Common.DbCommandBuilder> génère automatiquement les propriétés `InsertCommand`, `UpdateCommand` et `DeleteCommand` du `DataAdapter` si ce sont des références null. Si une `Command` existe déjà pour une propriété, la `Command` existante est utilisée.  
  
 Les vues de base de données qui sont créées en reliant deux ou plusieurs tables ne sont pas considérées comme une table de base de données unique. Dans ce cas, vous ne pouvez pas utiliser l'objet <xref:System.Data.Common.DbCommandBuilder> pour générer automatiquement des commandes et devez spécifier vos commandes explicitement. Pour obtenir des informations sur la `DataSet` définition explicite des commandes pour résoudre les mises à jour à un retour à la source de données, voir [Mise à jour des sources de données avec DataAdapters](updating-data-sources-with-dataadapters.md).  
  
 Il est possible de mapper les paramètres de sortie à la ligne mise à jour d'un `DataSet`. Une tâche courante consisterait à extraire la valeur d'un champ Identité généré automatiquement ou d'un horodatage provenant de la source de données. L'objet <xref:System.Data.Common.DbCommandBuilder> ne mappera pas les paramètres de sortie aux colonnes dans une ligne mise à jour par défaut. Dans ce cas, vous devez explicitement spécifier votre commande. Par exemple, la cartographie d’un champ d’identité généré automatiquement vers une colonne d’une rangée [insérée, voir Retrieving Identity ou Autonumber Values](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Règles pour les commandes générées automatiquement  
 Le tableau suivant présente les règles de génération des commandes générées automatiquement.  
  
|Commande|Règle|  
|-------------|----------|  
|`InsertCommand`|Insère une ligne dans la source de données pour toutes les lignes de la table dont la propriété <xref:System.Data.DataRow.RowState%2A> a la valeur <xref:System.Data.DataRowState.Added>. Insère des valeurs pour toutes les colonnes qui peuvent être mises à jour (mais pas les colonnes comme les identités, les expressions ou les horodatages).|  
|`UpdateCommand`|Met à jour les lignes dans la source de données pour toutes les lignes de la table dont la propriété `RowState` a la valeur <xref:System.Data.DataRowState.Modified>. Met à jour les valeurs de toutes les colonnes à l'exception de celles qui ne peuvent pas être mises à jour, telles que les identités ou les expressions. Met à jour toutes les lignes où les valeurs de colonne au niveau de la source de données correspondent aux valeurs de colonne de clé primaire de la ligne et où les colonnes restantes correspondent aux valeurs d'origine de la ligne. Pour plus d'informations, voir « Modèle d'accès simultané optimiste pour les mises à jour et les suppressions », plus loin dans cette rubrique.|  
|`DeleteCommand`|Supprime les lignes dans la source de données pour toutes les lignes de la table dont la propriété `RowState` a la valeur <xref:System.Data.DataRowState.Deleted>. Supprime toutes les lignes où les valeurs de colonne correspondent aux valeurs de colonne de clé primaire de la ligne et où les colonnes restantes de la source de données correspondent aux valeurs d'origine de la ligne. Pour plus d'informations, voir « Modèle d'accès simultané optimiste pour les mises à jour et les suppressions », plus loin dans cette rubrique.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Modèle d'accès simultané optimiste pour les mises à jour et les suppressions  
 La logique pour générer des commandes automatiquement pour les instructions UPDATE et DELETE est basée sur *une concordance optimiste*- c’est-à-dire que les enregistrements ne sont pas verrouillés pour l’édition et peuvent être modifiés par d’autres utilisateurs ou processus à tout moment. Puisqu'un enregistrement aurait pu être modifié après avoir été retourné de l'instruction SELECT mais avant que l'instruction UPDATE ou DELETE ne soit émise, l'instruction UPDATE ou DELETE générée automatiquement contient une clause WHERE spécifiant qu'une ligne n'est mise à jour que si elle contient toutes les valeurs d'origine et n'a pas été supprimée de la source de données. Cela permet d'éviter le remplacement de nouvelles données. Quand une mise à jour générée automatiquement tente de mettre à jour une ligne qui a été supprimée ou qui ne contient pas les valeurs d'origine qui se trouvent dans l'objet <xref:System.Data.DataSet>, la commande n'affecte pas d'enregistrement et un objet <xref:System.Data.DBConcurrencyException> est généré.  
  
 Si vous souhaitez que les instructions UPDATE ou DELETE soient exécutées indépendamment des valeurs d'origine, vous devez explicitement définir la propriété `UpdateCommand` pour le `DataAdapter` et ne pas compter sur la génération automatique de commandes.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Limites de la logique de génération automatique de commandes  
 Les limites suivantes s'appliquent à la génération automatique de commandes.  
  
### <a name="unrelated-tables-only"></a>Tables dissociées uniquement  
 La logique de génération automatique de commandes génère des instructions INSERT, UPDATE ou DELETE pour les tables autonomes sans prendre en compte les relations avec les autres tables au niveau de la source de données. En conséquence, il est possible que l'appel à `Update`, pour soumettre les modifications pour une colonne qui participe à une contrainte de clé étrangère dans la base de données, échoue. Pour éviter cette exception, n'utilisez pas l'objet <xref:System.Data.Common.DbCommandBuilder> pour mettre à jour les colonnes impliquées dans une contrainte de clé étrangère et spécifiez plutôt explicitement les instructions utilisées pour effectuer l'opération.  
  
### <a name="table-and-column-names"></a>Noms de table et de colonne  
 La logique de génération automatique de commandes peut échouer si les noms de colonne ou de table contiennent des caractères spéciaux (notamment espaces, points, points d'interrogation ou autres caractères non alphanumériques), même s'ils sont délimités par des crochets. Selon le fournisseur, le fait de définir les paramètres QuotePrefix et QuoteSuffix peut permettre à la logique de génération de traiter les espaces, mais pas les caractères spéciaux d'échappement. Les noms de table entièrement qualifiés sous forme de *catalog.schema.table* sont pris en charge.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Utilisation de CommandBuilder pour générer automatiquement une instruction SQL  
 Pour générer automatiquement des instructions SQL pour un `DataAdapter`, commencez par définir la propriété `SelectCommand` du `DataAdapter`, puis créez un objet `CommandBuilder` et spécifiez comme argument le `DataAdapter` pour lequel l’objet `CommandBuilder` génère automatiquement des instructions SQL.  
  
```vb  
' Assumes that connection is a valid SqlConnection object
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a>Modification de SelectCommand  
 Si vous modifiez le `CommandText` du `SelectCommand` après la génération automatique des commandes INSERT, UPDATE ou DELETE, une exception peut se produire. Si le `SelectCommand.CommandText` modifié contient des informations de schéma qui ne sont pas cohérentes par rapport au `SelectCommand.CommandText` utilisé lors de la génération automatique des commandes d'insertion, de mise à jour ou de suppression, les appels ultérieurs à la méthode `DataAdapter.Update` peuvent chercher à accéder à des colonnes qui n'existent plus dans la table actuelle référencée par `SelectCommand` et une exception sera levée.  
  
 Vous pouvez actualiser les informations de schéma utilisées par `CommandBuilder` pour générer automatiquement les commandes en appelant la méthode `RefreshSchema` du `CommandBuilder`.  
  
 Si vous souhaitez connaître les commandes générées automatiquement, vous pouvez en obtenir une référence en appliquant les méthodes `GetInsertCommand`, `GetUpdateCommand` et `GetDeleteCommand` de l'objet `CommandBuilder` et en vérifiant la propriété `CommandText` de la commande associée.  
  
 L'exemple de code suivant écrit sur la console la commande de mise à jour générée automatiquement.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 L'exemple suivant recrée la table `Customers` dans le dataset `custDS`. La méthode **RefreshSchema** est appelée pour actualiser les commandes générées automatiquement avec ces nouvelles informations de colonne.  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a>Voir aussi

- [Commandes et paramètres](commands-and-parameters.md)
- [Exécution d’un commandement](executing-a-command.md)
- [DbConnection, DbCommand et DbException](dbconnection-dbcommand-and-dbexception.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
