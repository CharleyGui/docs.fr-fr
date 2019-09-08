---
title: Fournisseur de statistiques pour SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b6fa4207531e86cbde8657d0c47596f22c886f89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791873"
---
# <a name="provider-statistics-for-sql-server"></a>Fournisseur de statistiques pour SQL Server
À partir du .NET Framework version 2.0, le fournisseur de données .NET Framework pour SQL Server prend en charge des statistiques d'exécution. Vous devez activer les statistiques en attribuant à la propriété <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection> la valeur `True` après la création d'un objet de connexion valide. Une fois les statistiques activées, vous pouvez les consulter comme « instantané dans le temps » en extrayant une référence <xref:System.Collections.IDictionary> via la méthode <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection>. Vous détaillez la liste comme un ensemble d'entrées de dictionnaire de paires nom-valeur. Ces paires nom-valeur ne sont triées. À tout moment, vous pouvez appeler la méthode <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection> pour réinitialiser les compteurs. Si la collecte de statistiques n'est pas activée, aucune exception n'est générée. En outre, si <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> est appelé sans que <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ait été appelé précédemment, les valeurs extraites sont les valeurs initiales de chaque entrée. Si vous activez les statistiques, exécutez votre application pendant un moment, puis désactivez les statistiques, les valeurs extraites reflètent celles collectées jusqu'au point où les statistiques étaient désactivées. Toutes les valeurs statistiques sont collectées par connexion.  
  
## <a name="statistical-values-available"></a>Valeurs statistiques disponibles  
 Il y a actuellement 18 éléments différents disponibles auprès du fournisseur Microsoft SQL Server. Le nombre d’éléments disponibles est accessible via la propriété **Count** de la <xref:System.Collections.IDictionary> référence d’interface retournée <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>par. Tous les compteurs pour les statistiques du fournisseur utilisent le type <xref:System.Int64> de Common Language Runtime (long C# dans et Visual Basic), qui est de 64 bits en largeur. Valeur maximale du type de données **Int64** , telle que définie par **Int64.** Le champ MaxValue, est ((2 ^ 63)-1)). Lorsque les valeurs des compteurs atteignent cette valeur maximale, elles ne doivent plus être considérées comme précises. Cela signifie que **Int64. MaxValue**-1 ((2 ^ 63)-2) est effectivement la plus grande valeur valide pour toutes les statistiques.  
  
> [!NOTE]
> Un dictionnaire est utilisé pour retourner des statistiques de fournisseur du fait que le nombre, les noms et l'ordre des statistiques retournées peuvent changer dans le futur. Les applications ne doivent pas dépendre d'une valeur spécifique trouvée dans le dictionnaire, mais contrôler si la valeur existe et créer une branche en conséquence.  
  
 Le tableau suivant décrit les valeurs statistiques actuelles disponibles. Notez que les noms clés pour les valeurs individuelles ne sont pas localisés dans les versions régionales de Microsoft .NET Framework.  
  
|Nom de clé|Description|  
|--------------|-----------------|  
|`BuffersReceived`|Retourne le nombre de paquets de flux de données tabulaires (TDS) reçus par le fournisseur à partir de SQL Server, après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`BuffersSent`|Retourne le nombre de paquets TDS envoyés à SQL Server par le fournisseur après que les statistiques ont été activées. Les commandes longues peuvent nécessiter plusieurs tampons. Par exemple, si une commande longue est envoyée au serveur et qu'elle requière six paquets, `ServerRoundtrips` est incrémenté d'une unité et `BuffersSent` de six.|  
|`BytesReceived`|Retourne le nombre d'octets de données dans les paquets TDS reçus par le fournisseur à partir de SQL Server, après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`BytesSent`|Retourne le nombre d'octets de données envoyés à SQL Server dans des paquets TDS après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`ConnectionTime`|La quantité de temps (en millisecondes) pendant laquelle les connexions ont été ouvertes après que les statistiques ont été activées (temps de connexion total si les statistiques ont été activées avant l'ouverture de la connexion).|  
|`CursorOpens`|Retourne le nombre de fois qu'un curseur a été ouvert par la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.<br /><br /> Notez que les résultats en lecture seule/en avant uniquement retournés par les instructions SELECT ne sont pas considérés comme des curseurs et n'affectent donc pas ce compteur.|  
|`ExecutionTime`|Retourne la quantité de temps cumulé (en millisecondes) que le fournisseur a consacré au traitement une fois les statistiques activées, y compris le temps passé à attendre des réponses du serveur, ainsi que le temps passé à exécuter du code dans le fournisseur proprement dit.<br /><br /> Les classes incluant un code de minutage sont les suivantes :<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Pour maintenir le nombre de membres critiques pour les performances le plus petit possible, les membres suivants ne sont pas minutés :<br /><br /> SqlDataReader<br /><br /> this[] operator (toutes les surcharges)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Retourne le nombre total d'instructions INSERT, DELETE et UPDATE exécutées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`IduRows`|Retourne le nombre total de lignes affectées par les instructions INSERT, DELETE et UPDATE exécutées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`NetworkServerTime`|Retourne la quantité de temps cumulé (en millisecondes) que le fournisseur a passé à attendre des réponses du serveur après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`PreparedExecs`|Retourne le nombre de commandes préparées exécutées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`Prepares`|Retourne le nombre d'instructions préparées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`SelectCount`|Retourne le nombre d'instructions SELECT exécutées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques. Cela inclut les instructions FETCH permettant d'extraire des lignes de curseurs et le compte des instructions SELECT est mis à jour à la fin d'un <xref:System.Data.SqlClient.SqlDataReader>.|  
|`SelectRows`|Retourne le nombre de lignes sélectionnées après que l'application a démarré à l'aide du fournisseur et a activé les statistiques. Ce compteur reflète toutes les lignes générées par les instructions SQL, y compris celles qui n'ont pas été réellement consommées par l'appelant. Par exemple, la fermeture d'un lecteur de données avant d'avoir lu l'ensemble de résultats complet n'affecterait pas le compte. Cela inclut les lignes extraites de curseurs à l'aide d'instructions FETCH.|  
|`ServerRoundtrips`|Retourne le nombre de fois que la connexion a envoyé des commandes au serveur et obtenu une réponse après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
|`SumResultSets`|Retourne le nombre d'ensembles de résultats utilisés après que l'application a démarré à l'aide du fournisseur et a activé les statistiques. Par exemple, cela inclut tout ensemble de résultats retourné au client. Pour les curseurs, chaque opération d'extraction ou d'extraction de bloc est considérée comme un ensemble de résultats indépendant.|  
|`Transactions`|Retourne le nombre de transactions d'utilisateur démarrées après que l'application a démarré à l'aide du fournisseur et a activé les statistiques, y compris les annulations. Si une connexion est en cours avec une validation automatique activée, chaque commande est considérée comme une transaction.<br /><br /> Ce compteur incrémente le compte des transactions dès qu'une instruction BEGIN TRAN est exécutée, indépendamment du fait que la transaction soit validée ou annulée ultérieurement.|  
|`UnpreparedExecs`|Retourne le nombre d'instructions non préparées exécutées via la connexion après que l'application a démarré à l'aide du fournisseur et a activé les statistiques.|  
  
### <a name="retrieving-a-value"></a>Extraction d'une valeur  
 L'application console suivante montre comment activer les statistiques sur une connexion, extraire quatre valeurs statistiques individuelles et les afficher dans la fenêtre de console.  
  
> [!NOTE]
> L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus avec SQL Server. La chaîne de connexion fournie dans l'exemple de code suppose que la base de données est installée et disponible sur l'ordinateur local. Si nécessaire, modifiez la chaîne de connexion en fonction de votre environnement.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Extraction de toutes les valeurs  
 L'application console suivante montre comment activer les statistiques sur une connexion, extraire toutes les valeurs statistiques disponibles à l'aide de l'énumérateur et les afficher dans la fenêtre de console.  
  
> [!NOTE]
> L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus avec SQL Server. La chaîne de connexion fournie dans l'exemple de code suppose que la base de données est installée et disponible sur l'ordinateur local. Si nécessaire, modifiez la chaîne de connexion en fonction de votre environnement.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
