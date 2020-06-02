---
title: Connexion à une source de données
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287075"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="148b2-102">Connexion à une source de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="148b2-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="148b2-103">Dans ADO.NET, vous utilisez un objet de **connexion** pour vous connecter à une source de données spécifique en fournissant les informations d’authentification nécessaires dans une chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="148b2-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="148b2-104">L’objet de **connexion** que vous utilisez dépend du type de source de données.</span><span class="sxs-lookup"><span data-stu-id="148b2-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="148b2-105">Chaque fournisseur de données .NET Framework inclut dans le .NET Framework comprend un objet <xref:System.Data.Common.DbConnection> : le fournisseur de données .ENT Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbConnection>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlConnection>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcConnection> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="148b2-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="148b2-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="148b2-106">In This Section</span></span>  
 <span data-ttu-id="148b2-107">[Établissement de la connexion](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="148b2-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="148b2-108">Décrit comment utiliser un objet de **connexion** pour établir une connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="148b2-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="148b2-109">[Événements de connexion](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="148b2-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="148b2-110">Décrit comment utiliser un événement **InfoMessage** pour extraire des messages d’information d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="148b2-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148b2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="148b2-111">See also</span></span>

- [<span data-ttu-id="148b2-112">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="148b2-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="148b2-113">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="148b2-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="148b2-114">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="148b2-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="148b2-115">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="148b2-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="148b2-116">Transactions et accès simultané</span><span class="sxs-lookup"><span data-stu-id="148b2-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="148b2-117">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="148b2-117">ADO.NET Overview</span></span>](ado-net-overview.md)
