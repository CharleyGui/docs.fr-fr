---
title: Séquences Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: d6e6bb51b8bd317c7161500b89993be689659fad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149412"
---
# <a name="oracle-sequences"></a>Séquences Oracle
Le fournisseur de données .NET Framework pour Oracle offre une prise en charge pour l'extraction des valeurs de séquence Oracle clés générées par le serveur, une fois les insertions réalisées par <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server et Oracle prennent en charge la création des colonnes à incrémentation automatique pouvant être désignées comme des clés primaires. Ces valeurs sont générées par le serveur lorsque des lignes sont ajoutées à une table. Dans SQL Server, vous définissez la propriété Identity d'une colonne ; dans Oracle, vous créez une séquence. La différence entre les colonnes à incrémentation automatique dans SQL Server et les séquences dans Oracle est la suivante :  
  
- Dans SQL Server, vous marquez une colonne en tant que colonne à incrémentation automatique et SQL Server génère automatiquement de nouvelles valeurs pour la colonne lorsque vous insérez une nouvelle ligne.  
  
- Dans Oracle, vous créez une séquence afin de générer de nouvelles valeurs pour une colonne de votre table, mais il n'existe aucun lien direct entre la séquence et la table ou la colonne. Une séquence Oracle est un objet, comme une table ou une procédure stockée.  
  
 Lorsque vous créez une séquence dans une base de données Oracle, vous pouvez définir sa valeur initiale et l'incrémentation entre ses valeurs. Vous pouvez également interroger la séquence à propos de nouvelles valeurs avant de soumettre de nouvelles lignes. Cela signifie que votre code peut reconnaître les valeurs clés des nouvelles lignes avant que vous ne les insériez dans la base de données.  
  
 Pour plus d’informations sur la création de colonnes d’incrément automatique en utilisant SQL Server et ADO.NET, voir [Retrieving Identity ou Autonumber Values](retrieving-identity-or-autonumber-values.md) et [Créer des colonnes d’augmentation automatique](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a> Exemple  
 L'exemple C# suivant montre comment vous pouvez extraire de nouvelles valeurs de séquence à partir d'une base de données Oracle. Cet exemple référence la séquence dans la requête INSERT INTO utilisée pour soumettre les nouvelles lignes, puis retourne la valeur de séquence générée à l'aide de la clause RETURNING introduite dans Oracle10g. L'exemple ajoute une série de nouvelles lignes en attente dans <xref:System.Data.DataTable> à l'aide d'une fonctionnalité d'incrémentation automatique ADO.NET pour générer des valeurs de clé primaire « espace réservé ». Notez que la valeur incrémentielle ADO.NET générée pour la nouvelle ligne est simplement un « espace réservé ». Cela signifie que la base de données peut générer des valeurs différentes de celles qu'ADO.NET génère.  
  
 Avant de soumettre les insertions en attente à la base de données, l'exemple affiche le contenu des lignes. Ensuite, le code crée un nouvel objet <xref:System.Data.OracleClient.OracleDataAdapter>, puis définit ses propriétés <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> et <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A>. Cet exemple fournit également la logique pour retourner les valeurs générées par le serveur à l'aide des paramètres de sortie. Ensuite, il procède à la mise à jour pour soumettre les lignes en attente et affiche le contenu de <xref:System.Data.DataTable>.  
  
```csharp  
public void OracleSequence(String connectionString)  
{  
   String insertString =
      "INSERT INTO SequenceTest_Table (ID, OtherColumn)" +  
      "VALUES (SequenceTest_Sequence.NEXTVAL, :OtherColumn)" +  
      "RETURNING ID INTO :ID";  
  
   using (OracleConnection conn = new OracleConnection(connectionString))  
   {  
      //Open a connection.  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
  
      // Prepare the database.  
      cmd.CommandText = "DROP SEQUENCE SequenceTest_Sequence";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "DROP TABLE SequenceTest_Table";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "CREATE TABLE SequenceTest_Table " +  
                     "(ID int PRIMARY KEY, OtherColumn varchar(255))";  
      cmd.ExecuteNonQuery();  
  
      cmd.CommandText = "CREATE SEQUENCE SequenceTest_Sequence " +  
                        "START WITH 100 INCREMENT BY 5";  
      cmd.ExecuteNonQuery();  
  
      DataTable testTable = new DataTable();  
      DataColumn column = testTable.Columns.Add("ID", typeof(int));  
      column.AutoIncrement = true;  
      column.AutoIncrementSeed = -1;  
      column.AutoIncrementStep = -1;  
      testTable.PrimaryKey = new DataColumn[] { column };  
      testTable.Columns.Add("OtherColumn", typeof(string));  
      for (int rowCounter = 1; rowCounter <= 15; rowCounter++)  
      {  
         testTable.Rows.Add(null, "Row #" + rowCounter.ToString());  
      }  
  
      Console.WriteLine("Before Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      Console.WriteLine();  
  
      cmd.CommandText =
        "SELECT ID, OtherColumn FROM SequenceTest_Table";  
      OracleDataAdapter da = new OracleDataAdapter(cmd);  
      da.InsertCommand = new OracleCommand(insertString, conn);  
      da.InsertCommand.Parameters.Add(":ID", OracleType.Int32, 0, "ID");  
      da.InsertCommand.Parameters[0].Direction = ParameterDirection.Output;  
      da.InsertCommand.Parameters.Add(":OtherColumn", OracleType.VarChar, 255, "OtherColumn");  
      da.InsertCommand.UpdatedRowSource = UpdateRowSource.OutputParameters;  
      da.UpdateBatchSize = 10;  
  
      da.Update(testTable);  
  
      Console.WriteLine("After Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      // Close the connection.  
      conn.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
