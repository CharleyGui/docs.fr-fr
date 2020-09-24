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
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="c0557-103">Compteurs de performance dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c0557-103">Performance Counters in ADO.NET</span></span>

<span data-ttu-id="c0557-104">ADO.NET 2.0 a introduit une prise en charge développée des compteurs de performance qui prend en charge à la fois <xref:System.Data.SqlClient> et <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="c0557-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="c0557-105">Les compteurs de performance <xref:System.Data.SqlClient> disponibles dans les versions antérieures d'ADO.NET sont déconseillés et remplacés par les nouveaux compteurs de performance évoqués dans cette rubrique. </span><span class="sxs-lookup"><span data-stu-id="c0557-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="c0557-106">Vous pouvez utiliser les compteurs de performance ADO.NET pour surveiller le statut de votre application et les ressources de connexion qu'elle utilise.</span><span class="sxs-lookup"><span data-stu-id="c0557-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="c0557-107">Vous pouvez surveiller les compteurs de performance à l'aide de l'Analyseur de performances Windows ou accéder à ces derniers par programme à l'aide de la classe <xref:System.Diagnostics.PerformanceCounter> dans l'espace de noms <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="c0557-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="c0557-108">Compteurs de performance disponibles</span><span class="sxs-lookup"><span data-stu-id="c0557-108">Available Performance Counters</span></span>  

 <span data-ttu-id="c0557-109">Actuellement, il existe 14 compteurs de performance différents disponibles pour <xref:System.Data.SqlClient> et <xref:System.Data.OracleClient>, comme décrit dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c0557-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="c0557-110">Notez que les noms des compteurs individuels ne sont pas localisés dans les versions régionales de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0557-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="c0557-111">Compteur de performances</span><span class="sxs-lookup"><span data-stu-id="c0557-111">Performance counter</span></span>|<span data-ttu-id="c0557-112">Description</span><span class="sxs-lookup"><span data-stu-id="c0557-112">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="c0557-113">Nombre de connexions par seconde qui sont établies à un serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="c0557-113">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="c0557-114">Nombre de déconnexions par seconde qui sont effectuées à un serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="c0557-114">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="c0557-115">Nombre de groupes du pool de connexion unique qui sont actifs.</span><span class="sxs-lookup"><span data-stu-id="c0557-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="c0557-116">Ce compteur est contrôlé par le nombre de chaînes de connexion uniques qui se trouvent dans AppDomain.</span><span class="sxs-lookup"><span data-stu-id="c0557-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="c0557-117">Nombre total de regroupements de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0557-117">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="c0557-118">Nombre de connexions actives en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="c0557-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="c0557-119">**Remarque :**  Ce compteur de performance n’est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0557-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="c0557-120">Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="c0557-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="c0557-121">Nombre de connexions disponibles pour une utilisation dans les regroupements de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0557-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="c0557-122">**Remarque :**  Ce compteur de performance n’est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0557-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="c0557-123">Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="c0557-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="c0557-124">Nombre de groupes du regroupement de connexions unique qui sont marqués pour le nettoyage.</span><span class="sxs-lookup"><span data-stu-id="c0557-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="c0557-125">Ce compteur est contrôlé par le nombre de chaînes de connexion uniques qui se trouvent dans AppDomain.</span><span class="sxs-lookup"><span data-stu-id="c0557-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="c0557-126">Nombre de regroupements de connexions inactifs sans activité récente et en attente de suppression.</span><span class="sxs-lookup"><span data-stu-id="c0557-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="c0557-127">Nombre de connexions actives qui n'ont pas été regroupées.</span><span class="sxs-lookup"><span data-stu-id="c0557-127">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="c0557-128">Nombre de connexions actives qui sont gérées par l'infrastructure de regroupement de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0557-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="c0557-129">Nombre de connexions ayant été récupérées par le biais du garbage collection dans lequel `Close` ou `Dispose` n'a pas été appelé par l'application.</span><span class="sxs-lookup"><span data-stu-id="c0557-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="c0557-130">La fermeture ou la suppression non explicites des connexions nuit aux performances.</span><span class="sxs-lookup"><span data-stu-id="c0557-130">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="c0557-131">Nombre de connexions en attente de l'achèvement d'une action et par conséquent non disponibles pour une utilisation par votre application.</span><span class="sxs-lookup"><span data-stu-id="c0557-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="c0557-132">Nombre de connexions actives en cours d'extraction du regroupement de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0557-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="c0557-133">**Remarque :**  Ce compteur de performance n’est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0557-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="c0557-134">Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="c0557-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="c0557-135">Nombre de connexions actives retournées au regroupement de connexions.</span><span class="sxs-lookup"><span data-stu-id="c0557-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="c0557-136">**Remarque :**  Ce compteur de performance n’est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0557-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="c0557-137">Pour activer ce compteur de performance, consultez [activation des compteurs désactivés par défaut](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="c0557-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="c0557-138">Groupes du regroupement de connexions et regroupements de connexions</span><span class="sxs-lookup"><span data-stu-id="c0557-138">Connection Pool Groups and Connection Pools</span></span>  

 <span data-ttu-id="c0557-139">Lorsque vous utilisez l'authentification Windows (sécurité intégrée), vous devez surveiller les deux compteurs de performance `NumberOfActiveConnectionPoolGroups` et `NumberOfActiveConnectionPools`.</span><span class="sxs-lookup"><span data-stu-id="c0557-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="c0557-140">En effet, les groupes du regroupement de connexions sont mappés à des chaînes de connexion uniques.</span><span class="sxs-lookup"><span data-stu-id="c0557-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="c0557-141">Les regroupements de connexions sont mappés aux chaînes de connexion et créent des regroupements séparés pour des identités Windows individuelles, lors de l'utilisation de la sécurité intégrée.</span><span class="sxs-lookup"><span data-stu-id="c0557-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="c0557-142">Par exemple, si Fred et Julie, qui appartiennent au même AppDomain, utilisent tous les deux la chaîne de connexion `"Data Source=MySqlServer;Integrated Security=true"`, un groupe de regroupement de connexions est créé pour la chaîne de connexion, et deux autres regroupements sont créés, un pour Fred et un pour Julie.</span><span class="sxs-lookup"><span data-stu-id="c0557-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="c0557-143">Si John et Martha utilisent une chaîne de connexion avec une connexion SQL Server identique, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` , un seul pool est créé pour l’identité **lowPrivUser** .</span><span class="sxs-lookup"><span data-stu-id="c0557-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a><span data-ttu-id="c0557-144">Activation des compteurs désactivés par défaut</span><span class="sxs-lookup"><span data-stu-id="c0557-144">Activating Off-By-Default Counters</span></span>  

 <span data-ttu-id="c0557-145">Les compteurs de performance `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond` et `SoftConnectsPerSecond` sont désactivés par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0557-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="c0557-146">Ajoutez les informations suivantes dans le fichier de configuration de l'application pour les activer :</span><span class="sxs-lookup"><span data-stu-id="c0557-146">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="c0557-147">Récupération des valeurs de compteur de performance</span><span class="sxs-lookup"><span data-stu-id="c0557-147">Retrieving Performance Counter Values</span></span>  

 <span data-ttu-id="c0557-148">L'application console suivante montre comment récupérer les valeurs de compteur de performance dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c0557-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="c0557-149">Les connexions doivent être ouvertes et actives afin que les informations soient retournées pour tous les compteurs de performance ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c0557-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0557-150">Cet exemple utilise l’exemple de base de données **AdventureWorks** inclus avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0557-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="c0557-151">Les chaînes de connexion fournies dans l'exemple de code sont basées sur l'hypothèse que la base de données est installée et disponible sur l'ordinateur local avec un nom d'instance de SqlExpress, et que vous avez créé des connexions SQL Server qui correspondent à celles fournies dans les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="c0557-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="c0557-152">Vous devrez peut-être activer les connexions SQL Server si votre serveur est configuré à l'aide des paramètres de sécurité par défaut qui autorisent uniquement l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="c0557-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="c0557-153">Modifiez les chaînes de connexion en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="c0557-153">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c0557-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0557-154">Example</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="c0557-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0557-155">See also</span></span>

- [<span data-ttu-id="c0557-156">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="c0557-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="c0557-157">Regroupement de connexions OLE DB, ODBC et Oracle Connection</span><span class="sxs-lookup"><span data-stu-id="c0557-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="c0557-158">[Compteurs de performances pour ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0557-158">[Performance Counters for ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="c0557-159">Génération de profils d'exécution</span><span class="sxs-lookup"><span data-stu-id="c0557-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="c0557-160">[Présentation de l’analyse des seuils de performance](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c0557-160">[Introduction to Monitoring Performance Thresholds](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="c0557-161">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c0557-161">ADO.NET Overview</span></span>](ado-net-overview.md)
