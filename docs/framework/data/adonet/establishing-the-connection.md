---
title: Établissement de la connexion
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 50cf5011376576d371dba558a602187201395bd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599600"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="1519a-102">Établissement de la connexion</span><span class="sxs-lookup"><span data-stu-id="1519a-102">Establishing the Connection</span></span>
<span data-ttu-id="1519a-103">Pour vous connecter à Microsoft SQL Server, utilisez l'objet <xref:System.Data.SqlClient.SqlConnection> du fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1519a-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="1519a-104">Pour vous connecter à une source de données OLE DB, utilisez l'objet <xref:System.Data.OleDb.OleDbConnection> du fournisseur de données .NET Framework pour OLE DB.</span><span class="sxs-lookup"><span data-stu-id="1519a-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="1519a-105">Pour vous connecter à une source de données ODBC, utilisez l'objet <xref:System.Data.Odbc.OdbcConnection> du fournisseur de données .NET Framework pour ODBC.</span><span class="sxs-lookup"><span data-stu-id="1519a-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="1519a-106">Pour vous connecter à une source de données Oracle, utilisez l'objet <xref:System.Data.OracleClient.OracleConnection> du fournisseur de données .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="1519a-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="1519a-107">Pour stocker en toute sécurité et l’extraction des chaînes de connexion, consultez [protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1519a-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="1519a-108">Fermeture de connexions</span><span class="sxs-lookup"><span data-stu-id="1519a-108">Closing Connections</span></span>  
 <span data-ttu-id="1519a-109">Nous vous recommandons de toujours fermer la connexion lorsque vous avez fini de l'utiliser, de façon à ce qu'elle puisse être retournée au pool.</span><span class="sxs-lookup"><span data-stu-id="1519a-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="1519a-110">Le bloc `Using` dans Visual Basic ou C# supprime automatiquement la connexion lorsque le code quitte le bloc, même dans le cas d'une exception non traitée.</span><span class="sxs-lookup"><span data-stu-id="1519a-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="1519a-111">Consultez [à l’aide d’instruction](~/docs/csharp/language-reference/keywords/using-statement.md) et [Using, instruction](~/docs/visual-basic/language-reference/statements/using-statement.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1519a-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="1519a-112">Vous pouvez également utiliser la méthode `Close` ou `Dispose` de l'objet de connexion pour le fournisseur que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1519a-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="1519a-113">Les connexions qui ne sont pas explicitement fermées risquent de ne pas être ajoutées ni retournées au pool.</span><span class="sxs-lookup"><span data-stu-id="1519a-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="1519a-114">Par exemple, une connexion devenue hors de portée mais qui n'a pas été explicitement fermée sera retournée au pool de connexion seulement si la taille maximale de celui-ci a été atteinte et si la connexion est toujours valide.</span><span class="sxs-lookup"><span data-stu-id="1519a-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="1519a-115">Pour plus d’informations, consultez [OLE DB, ODBC et le regroupement de connexions Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="1519a-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1519a-116">N’appelez pas `Close` ou `Dispose` sur un **connexion**, un **DataReader**, ou tout autre objet managé dans le `Finalize` méthode de votre classe.</span><span class="sxs-lookup"><span data-stu-id="1519a-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="1519a-117">Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.</span><span class="sxs-lookup"><span data-stu-id="1519a-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="1519a-118">Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="1519a-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="1519a-119">Pour plus d’informations, consultez [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="1519a-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1519a-120">Les événements de connexion et de déconnexion ne seront pas déclenchés sur le serveur si une connexion est récupérée depuis le pool de connexions ou qu’elle est retournée au pool, car elle n’est pas réellement fermée lorsqu’elle est retournée au pool.</span><span class="sxs-lookup"><span data-stu-id="1519a-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="1519a-121">Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="1519a-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="1519a-122">Connexion à SQL Server</span><span class="sxs-lookup"><span data-stu-id="1519a-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="1519a-123">Le fournisseur de données .NET Framework pour SQL Server prend en charge un format de chaîne de connexion similaire à celui de la chaîne de connexion OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="1519a-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="1519a-124">Pour obtenir les noms et les valeurs de format de chaîne valides, voir la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="1519a-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="1519a-125">Vous pouvez également utiliser la classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1519a-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="1519a-126">Pour plus d’informations, consultez [Builders de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="1519a-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="1519a-127">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1519a-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="1519a-128">Sécurité intégrée et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1519a-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="1519a-129">La sécurité intégrée SQL Server (également appelée « connexions approuvées ») fournit une protection lors de la connexion à SQL Server car elle n'expose pas d'ID utilisateur et de mot de passe dans la chaîne de connexion, et elle est la méthode recommandée pour l'authentification d'une connexion.</span><span class="sxs-lookup"><span data-stu-id="1519a-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="1519a-130">La sécurité intégrée utilise l'identité de sécurité active, ou jeton, du processus en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1519a-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="1519a-131">Dans les applications bureautiques, il s'agit généralement de l'identité de l'utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="1519a-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="1519a-132">Dans les applications ASP.NET, l'identité de sécurité peut être définie à l'aide d'une option parmi plusieurs options différentes.</span><span class="sxs-lookup"><span data-stu-id="1519a-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="1519a-133">Pour mieux comprendre l’identité de sécurité qu’une application ASP.NET utilise lors de la connexion à SQL Server, consultez [emprunt d’identité ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [l’authentification ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), et [Comment : Accéder à SQL Server à l’aide de Windows la sécurité intégrée](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1519a-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="1519a-134">Connexion à une source de données OLE DB</span><span class="sxs-lookup"><span data-stu-id="1519a-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="1519a-135">Le fournisseur de données .NET Framework pour OLE DB assure la connectivité aux sources de données exposées à l’aide de OLE DB (via SQLOLEDB, le fournisseur OLE DB pour SQL Server), à l’aide de la **OleDbConnection** objet.</span><span class="sxs-lookup"><span data-stu-id="1519a-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="1519a-136">Pour le fournisseur de données .NET Framework pour OLE DB, le format de chaîne de connexion est identique à celui utilisé dans ADO, avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1519a-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="1519a-137">Le **fournisseur** mot clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1519a-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="1519a-138">Le **URL**, **fournisseur distant**, et **serveur distant** mots clés ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1519a-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="1519a-139">Pour plus d'informations sur les chaînes de connexion OLE DB, voir la rubrique <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="1519a-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="1519a-140">Vous pouvez également utiliser <xref:System.Data.OleDb.OleDbConnectionStringBuilder> pour créer des chaînes de connexion au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1519a-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1519a-141">Le **OleDbConnection** objet ne prend pas en charge la définition ou la récupération des propriétés dynamiques spécifiques à un fournisseur OLE DB.</span><span class="sxs-lookup"><span data-stu-id="1519a-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="1519a-142">Seules les propriétés pouvant être passées dans la chaîne de connexion du fournisseur OLE DB sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1519a-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="1519a-143">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données OLE DB.</span><span class="sxs-lookup"><span data-stu-id="1519a-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="1519a-144">N'utilisez pas de fichiers UDL (Universal Data Link)</span><span class="sxs-lookup"><span data-stu-id="1519a-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="1519a-145">Il est possible de fournir des informations de connexion pour un **OleDbConnection** dans un fichier lien UDL (Universal Data) ; toutefois vous devez éviter cela.</span><span class="sxs-lookup"><span data-stu-id="1519a-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="1519a-146">Les fichiers UDL n'étant pas chiffrés, ils exposent les informations de chaîne de connexion en texte brut.</span><span class="sxs-lookup"><span data-stu-id="1519a-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="1519a-147">Comme un fichier UDL est une ressource basée sur un fichier externe pour votre application, il n'est pas possible de le sécuriser à l'aide du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1519a-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="1519a-148">Connexion à une source de données ODBC</span><span class="sxs-lookup"><span data-stu-id="1519a-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="1519a-149">Le fournisseur de données .NET Framework pour ODBC assure la connectivité aux sources de données exposées à l’aide de ODBC à l’aide du **OdbcConnection** objet.</span><span class="sxs-lookup"><span data-stu-id="1519a-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="1519a-150">Pour le fournisseur de données .NET Framework pour ODBC, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion ODBC.</span><span class="sxs-lookup"><span data-stu-id="1519a-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="1519a-151">Vous pouvez également fournir un nom de source de données ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="1519a-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="1519a-152">Pour plus d’informations sur la **OdbcConnection** , consultez le <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="1519a-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="1519a-153">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données ODBC.</span><span class="sxs-lookup"><span data-stu-id="1519a-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="1519a-154">Connexion à une source de données Oracle</span><span class="sxs-lookup"><span data-stu-id="1519a-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="1519a-155">Le fournisseur de données .NET Framework pour Oracle assure la connectivité aux sources de données Oracle à l’aide de la **OracleConnection** objet.</span><span class="sxs-lookup"><span data-stu-id="1519a-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="1519a-156">Pour le fournisseur de données .NET Framework pour Oracle, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion du fournisseur de données OLE DB pour Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="1519a-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="1519a-157">Pour plus d’informations sur la **OracleConnection**, consultez le <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="1519a-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="1519a-158">L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="1519a-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1519a-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1519a-159">See also</span></span>

- [<span data-ttu-id="1519a-160">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="1519a-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="1519a-161">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="1519a-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="1519a-162">Regroupement de connexions OLE DB, ODBC et Oracle</span><span class="sxs-lookup"><span data-stu-id="1519a-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="1519a-163">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="1519a-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
