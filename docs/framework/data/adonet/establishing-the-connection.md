---
title: Établissement de la connexion
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: bf38475711a193bc69176993154f87d455aefe7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156470"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="e1683-102">Établissement de la connexion</span><span class="sxs-lookup"><span data-stu-id="e1683-102">Establishing the Connection</span></span>

<span data-ttu-id="e1683-103">Pour vous connecter à Microsoft SQL Server, utilisez l'objet <xref:System.Data.SqlClient.SqlConnection> du fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e1683-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e1683-104">Pour vous connecter à une source de données OLE DB, utilisez l'objet <xref:System.Data.OleDb.OleDbConnection> du fournisseur de données .NET Framework pour OLE DB.</span><span class="sxs-lookup"><span data-stu-id="e1683-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="e1683-105">Pour vous connecter à une source de données ODBC, utilisez l'objet <xref:System.Data.Odbc.OdbcConnection> du fournisseur de données .NET Framework pour ODBC.</span><span class="sxs-lookup"><span data-stu-id="e1683-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="e1683-106">Pour vous connecter à une source de données Oracle, utilisez l'objet <xref:System.Data.OracleClient.OracleConnection> du fournisseur de données .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="e1683-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="e1683-107">Pour stocker et récupérer en toute sécurité des chaînes de connexion, consultez [protection des informations de connexion](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e1683-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="e1683-108">Fermeture de connexions</span><span class="sxs-lookup"><span data-stu-id="e1683-108">Closing Connections</span></span>  

 <span data-ttu-id="e1683-109">Nous vous recommandons de toujours fermer la connexion lorsque vous avez fini de l'utiliser, de façon à ce qu'elle puisse être retournée au pool.</span><span class="sxs-lookup"><span data-stu-id="e1683-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="e1683-110">Le bloc `Using` dans Visual Basic ou C# supprime automatiquement la connexion lorsque le code quitte le bloc, même dans le cas d'une exception non traitée.</span><span class="sxs-lookup"><span data-stu-id="e1683-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="e1683-111">Pour plus d’informations, consultez Utilisation de l' [instruction using](../../../csharp/language-reference/keywords/using-statement.md) et de [l’instruction using](../../../visual-basic/language-reference/statements/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="e1683-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="e1683-112">Vous pouvez également utiliser la méthode `Close` ou `Dispose` de l'objet de connexion pour le fournisseur que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e1683-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="e1683-113">Les connexions qui ne sont pas explicitement fermées risquent de ne pas être ajoutées ni retournées au pool.</span><span class="sxs-lookup"><span data-stu-id="e1683-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="e1683-114">Par exemple, une connexion devenue hors de portée mais qui n'a pas été explicitement fermée sera retournée au pool de connexion seulement si la taille maximale de celui-ci a été atteinte et si la connexion est toujours valide.</span><span class="sxs-lookup"><span data-stu-id="e1683-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="e1683-115">Pour plus d’informations, consultez [OLE DB, ODBC et regroupement de connexions Oracle](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="e1683-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1683-116">N’appelez pas `Close` ou `Dispose` sur une **connexion**, un **DataReader**ou tout autre objet managé dans la `Finalize` méthode de votre classe.</span><span class="sxs-lookup"><span data-stu-id="e1683-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="e1683-117">Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.</span><span class="sxs-lookup"><span data-stu-id="e1683-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="e1683-118">Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="e1683-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="e1683-119">Pour plus d’informations, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1683-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1683-120">Les événements de connexion et de déconnexion ne seront pas déclenchés sur le serveur si une connexion est récupérée depuis le pool de connexions ou qu’elle est retournée au pool, car elle n’est pas réellement fermée lorsqu’elle est retournée au pool.</span><span class="sxs-lookup"><span data-stu-id="e1683-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="e1683-121">Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="e1683-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="e1683-122">Connexion à SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1683-122">Connecting to SQL Server</span></span>  

 <span data-ttu-id="e1683-123">Le fournisseur de données .NET Framework pour SQL Server prend en charge un format de chaîne de connexion similaire à celui de la chaîne de connexion OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="e1683-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="e1683-124">Pour obtenir les noms et les valeurs de format de chaîne valides, voir la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="e1683-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="e1683-125">Vous pouvez également utiliser la classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e1683-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="e1683-126">Pour plus d’informations, consultez [Builders de chaînes de connexion](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="e1683-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="e1683-127">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e1683-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="e1683-128">Sécurité intégrée et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e1683-128">Integrated Security and ASP.NET</span></span>  

 <span data-ttu-id="e1683-129">La sécurité intégrée SQL Server (également appelée « connexions approuvées ») fournit une protection lors de la connexion à SQL Server car elle n'expose pas d'ID utilisateur et de mot de passe dans la chaîne de connexion, et elle est la méthode recommandée pour l'authentification d'une connexion.</span><span class="sxs-lookup"><span data-stu-id="e1683-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="e1683-130">La sécurité intégrée utilise l'identité de sécurité active, ou jeton, du processus en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="e1683-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="e1683-131">Dans les applications bureautiques, il s'agit généralement de l'identité de l'utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="e1683-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="e1683-132">Dans les applications ASP.NET, l'identité de sécurité peut être définie à l'aide d'une option parmi plusieurs options différentes.</span><span class="sxs-lookup"><span data-stu-id="e1683-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="e1683-133">Pour mieux comprendre l’identité de sécurité qu’une application ASP.NET utilise pour se connecter à SQL Server, consultez [emprunt d’identité ASP.net](/previous-versions/aspnet/xh507fc5(v=vs.100)), [authentification ASP.net](/previous-versions/aspnet/eeyk640h(v=vs.100))et [Comment : accéder à SQL Server à l’aide de la sécurité intégrée de Windows](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e1683-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="e1683-134">Connexion à une source de données OLE DB</span><span class="sxs-lookup"><span data-stu-id="e1683-134">Connecting to an OLE DB Data Source</span></span>  

 <span data-ttu-id="e1683-135">La .NET Framework Fournisseur de données pour OLE DB fournit la connectivité aux sources de données exposées à l’aide de OLE DB (via SQLOLEDB, le fournisseur OLE DB pour SQL Server), à l’aide de l’objet **OleDbConnection** .</span><span class="sxs-lookup"><span data-stu-id="e1683-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="e1683-136">Pour le fournisseur de données .NET Framework pour OLE DB, le format de chaîne de connexion est identique à celui utilisé dans ADO, avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1683-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="e1683-137">Le mot clé **Provider** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e1683-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="e1683-138">Les mots clés **URL**, **Remote Provider**et **Remote Server** ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e1683-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="e1683-139">Pour plus d'informations sur les chaînes de connexion OLE DB, voir la rubrique <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1683-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="e1683-140">Vous pouvez également utiliser <xref:System.Data.OleDb.OleDbConnectionStringBuilder> pour créer des chaînes de connexion au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e1683-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1683-141">L’objet **OleDbConnection** ne prend pas en charge la définition ou la récupération de propriétés dynamiques spécifiques à un fournisseur OLE DB.</span><span class="sxs-lookup"><span data-stu-id="e1683-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="e1683-142">Seules les propriétés pouvant être passées dans la chaîne de connexion du fournisseur OLE DB sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e1683-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="e1683-143">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données OLE DB.</span><span class="sxs-lookup"><span data-stu-id="e1683-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="e1683-144">N'utilisez pas de fichiers UDL (Universal Data Link)</span><span class="sxs-lookup"><span data-stu-id="e1683-144">Do Not Use Universal Data Link Files</span></span>  

 <span data-ttu-id="e1683-145">Il est possible de fournir des informations de connexion pour un **OleDbConnection** dans un fichier Universal Data Link (UDL); Toutefois, vous devez éviter de le faire.</span><span class="sxs-lookup"><span data-stu-id="e1683-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="e1683-146">Les fichiers UDL n'étant pas chiffrés, ils exposent les informations de chaîne de connexion en texte brut.</span><span class="sxs-lookup"><span data-stu-id="e1683-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="e1683-147">Comme un fichier UDL est une ressource basée sur un fichier externe pour votre application, il n'est pas possible de le sécuriser à l'aide du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1683-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="e1683-148">Connexion à une source de données ODBC</span><span class="sxs-lookup"><span data-stu-id="e1683-148">Connecting to an ODBC Data Source</span></span>  

 <span data-ttu-id="e1683-149">La .NET Framework Fournisseur de données pour ODBC assure la connectivité aux sources de données exposées à l’aide d’ODBC à l’aide de l’objet **OdbcConnection** .</span><span class="sxs-lookup"><span data-stu-id="e1683-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="e1683-150">Pour le fournisseur de données .NET Framework pour ODBC, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion ODBC.</span><span class="sxs-lookup"><span data-stu-id="e1683-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="e1683-151">Vous pouvez également fournir un nom de source de données ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="e1683-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="e1683-152">Pour plus d’informations sur **OdbcConnection** , consultez <xref:System.Data.Odbc.OdbcConnection> .</span><span class="sxs-lookup"><span data-stu-id="e1683-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="e1683-153">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données ODBC.</span><span class="sxs-lookup"><span data-stu-id="e1683-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="e1683-154">Connexion à une source de données Oracle</span><span class="sxs-lookup"><span data-stu-id="e1683-154">Connecting to an Oracle Data Source</span></span>  

 <span data-ttu-id="e1683-155">La .NET Framework Fournisseur de données pour Oracle assure la connectivité aux sources de données Oracle à l’aide de l’objet **OracleConnection** .</span><span class="sxs-lookup"><span data-stu-id="e1683-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="e1683-156">Pour le fournisseur de données .NET Framework pour Oracle, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion du fournisseur de données OLE DB pour Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="e1683-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="e1683-157">Pour plus d’informations sur le **OracleConnection**, consultez <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="e1683-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="e1683-158">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="e1683-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1683-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1683-159">See also</span></span>

- [<span data-ttu-id="e1683-160">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="e1683-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="e1683-161">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="e1683-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="e1683-162">Regroupement de connexions OLE DB, ODBC et Oracle Connection</span><span class="sxs-lookup"><span data-stu-id="e1683-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="e1683-163">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e1683-163">ADO.NET Overview</span></span>](ado-net-overview.md)
