---
title: Compteurs de performances
description: Utilisez les compteurs de performance ADO.NET pour surveiller l’état de votre application et ses ressources de connexion à l’aide de l’analyseur de performances Windows ou par programme.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 4f645a51996078f8dd80b6c455c420633db36155
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164597"
---
# <a name="performance-counters-in-adonet"></a>Compteurs de performance dans ADO.NET

ADO.NET 2.0 a introduit une prise en charge développée des compteurs de performance qui prend en charge à la fois <xref:System.Data.SqlClient> et <xref:System.Data.OracleClient>. Les compteurs de performance <xref:System.Data.SqlClient> disponibles dans les versions antérieures d'ADO.NET sont déconseillés et remplacés par les nouveaux compteurs de performance évoqués dans cette rubrique.  Vous pouvez utiliser les compteurs de performance ADO.NET pour surveiller le statut de votre application et les ressources de connexion qu'elle utilise. Vous pouvez surveiller les compteurs de performance à l'aide de l'Analyseur de performances Windows ou accéder à ces derniers par programme à l'aide de la classe <xref:System.Diagnostics.PerformanceCounter> dans l'espace de noms <xref:System.Diagnostics>.  
  
## <a name="available-performance-counters"></a>Compteurs de performance disponibles  

 Actuellement, il existe 14 compteurs de performance différents disponibles pour <xref:System.Data.SqlClient> et <xref:System.Data.OracleClient>, comme décrit dans le tableau ci-dessous. Notez que les noms des compteurs individuels ne sont pas localisés dans les versions régionales de Microsoft .NET Framework.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Nombre de connexions par seconde qui sont établies à un serveur de base de données.|  
|`HardDisconnectsPerSecond`|Nombre de déconnexions par seconde qui sont effectuées à un serveur de base de données.|  
|`NumberOfActiveConnectionPoolGroups`|Nombre de groupes du pool de connexion unique qui sont actifs. Ce compteur est contrôlé par le nombre de chaînes de connexion uniques qui se trouvent dans AppDomain.|  
|`NumberOfActiveConnectionPools`|Nombre total de regroupements de connexions.|  
|`NumberOfActiveConnections`|Nombre de connexions actives en cours d'utilisation. **Remarque :**  Ce compteur de performance n’est pas activé par défaut. Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Nombre de connexions disponibles pour une utilisation dans les regroupements de connexions. **Remarque :**  Ce compteur de performance n’est pas activé par défaut. Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Nombre de groupes du regroupement de connexions unique qui sont marqués pour le nettoyage. Ce compteur est contrôlé par le nombre de chaînes de connexion uniques qui se trouvent dans AppDomain.|  
|`NumberOfInactiveConnectionPools`|Nombre de regroupements de connexions inactifs sans activité récente et en attente de suppression.|  
|`NumberOfNonPooledConnections`|Nombre de connexions actives qui n'ont pas été regroupées.|  
|`NumberOfPooledConnections`|Nombre de connexions actives qui sont gérées par l'infrastructure de regroupement de connexions.|  
|`NumberOfReclaimedConnections`|Nombre de connexions ayant été récupérées par le biais du garbage collection dans lequel `Close` ou `Dispose` n'a pas été appelé par l'application. La fermeture ou la suppression non explicites des connexions nuit aux performances.|  
|`NumberOfStasisConnections`|Nombre de connexions en attente de l'achèvement d'une action et par conséquent non disponibles pour une utilisation par votre application.|  
|`SoftConnectsPerSecond`|Nombre de connexions actives en cours d'extraction du regroupement de connexions. **Remarque :**  Ce compteur de performance n’est pas activé par défaut. Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Nombre de connexions actives retournées au regroupement de connexions. **Remarque :**  Ce compteur de performance n’est pas activé par défaut. Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Groupes du regroupement de connexions et regroupements de connexions  

 Lorsque vous utilisez l'authentification Windows (sécurité intégrée), vous devez surveiller les deux compteurs de performance `NumberOfActiveConnectionPoolGroups` et `NumberOfActiveConnectionPools`. En effet, les groupes du regroupement de connexions sont mappés à des chaînes de connexion uniques. Les regroupements de connexions sont mappés aux chaînes de connexion et créent des regroupements séparés pour des identités Windows individuelles, lors de l'utilisation de la sécurité intégrée. Par exemple, si Fred et Julie, qui appartiennent au même AppDomain, utilisent tous les deux la chaîne de connexion `"Data Source=MySqlServer;Integrated Security=true"`, un groupe de regroupement de connexions est créé pour la chaîne de connexion, et deux autres regroupements sont créés, un pour Fred et un pour Julie. Si John et Martha utilisent une chaîne de connexion avec une connexion SQL Server identique, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` , un seul pool est créé pour l’identité **lowPrivUser** .  
  
<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a>Activation des compteurs désactivés par défaut  

 Les compteurs de performance `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond` et `SoftConnectsPerSecond` sont désactivés par défaut. Ajoutez les informations suivantes dans le fichier de configuration de l'application pour les activer :  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Récupération des valeurs de compteur de performance  

 L'application console suivante montre comment récupérer les valeurs de compteur de performance dans votre application. Les connexions doivent être ouvertes et actives afin que les informations soient retournées pour tous les compteurs de performance ADO.NET.  
  
> [!NOTE]
> Cet exemple utilise l’exemple de base de données **AdventureWorks** inclus avec SQL Server. Les chaînes de connexion fournies dans l'exemple de code sont basées sur l'hypothèse que la base de données est installée et disponible sur l'ordinateur local avec un nom d'instance de SqlExpress, et que vous avez créé des connexions SQL Server qui correspondent à celles fournies dans les chaînes de connexion. Vous devrez peut-être activer les connexions SQL Server si votre serveur est configuré à l'aide des paramètres de sécurité par défaut qui autorisent uniquement l'authentification Windows. Modifiez les chaînes de connexion en fonction de votre environnement.  
  
### <a name="example"></a>Exemple  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's
        'FriendlyName. Replace the line above that sets the instanceName with this:
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a>Voir aussi

- [Connexion à une source de données](connecting-to-a-data-source.md)
- [Regroupement de connexions OLE DB, ODBC et Oracle Connection](ole-db-odbc-and-oracle-connection-pooling.md)
- [Compteurs de performances pour ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Génération de profils d'exécution](../../debug-trace-profile/runtime-profiling.md)
- [Présentation de l’analyse des seuils de performance](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
