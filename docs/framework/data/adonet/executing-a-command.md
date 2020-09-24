---
title: Exécution d'une commande
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: d7d290c1c149f9eab2449c25e8d32f2568eb0277
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156457"
---
# <a name="executing-a-command"></a><span data-ttu-id="0024a-102">Exécution d'une commande</span><span class="sxs-lookup"><span data-stu-id="0024a-102">Executing a Command</span></span>

<span data-ttu-id="0024a-103">Chaque fournisseur de données .NET Framework inclus avec le .NET Framework possède son propre objet de commande qui hérite de <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="0024a-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="0024a-104">Le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbCommand>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlCommand>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcCommand> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="0024a-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="0024a-105">Chacun de ces objets expose des méthodes pour exécuter les commandes en fonction du type de commande et de la valeur de retour souhaitée, comme cela est décrit dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0024a-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="0024a-106">Commande</span><span class="sxs-lookup"><span data-stu-id="0024a-106">Command</span></span>|<span data-ttu-id="0024a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0024a-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="0024a-108">Retourne un objet `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="0024a-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="0024a-109">Retourne une valeur scalaire unique.</span><span class="sxs-lookup"><span data-stu-id="0024a-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="0024a-110">Exécute une commande qui ne retourne aucune ligne.</span><span class="sxs-lookup"><span data-stu-id="0024a-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="0024a-111">Retourne un <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0024a-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="0024a-112">Disponible pour un objet `SqlCommand` uniquement.</span><span class="sxs-lookup"><span data-stu-id="0024a-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="0024a-113">Chaque objet de commande fortement typé prend également en charge une énumération <xref:System.Data.CommandType> qui spécifie la manière dont une chaîne de commande est interprétée, comme cela est décrit dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0024a-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="0024a-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="0024a-114">CommandType</span></span>|<span data-ttu-id="0024a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0024a-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="0024a-116">Commande SQL qui définit les instructions à exécuter au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="0024a-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="0024a-117">Nom de la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="0024a-117">The name of the stored procedure.</span></span> <span data-ttu-id="0024a-118">Vous pouvez utiliser la propriété `Parameters` d'une commande pour accéder aux paramètres d'entrée et de sortie et aux valeurs de retour, quelle que soit la méthode `Execute` appelée.</span><span class="sxs-lookup"><span data-stu-id="0024a-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="0024a-119">Lorsque vous utilisez `ExecuteReader`, les valeurs de retour et les paramètres de sortie ne seront pas accessibles tant que `DataReader` ne sera pas fermé.</span><span class="sxs-lookup"><span data-stu-id="0024a-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="0024a-120">Nom d'une table.</span><span class="sxs-lookup"><span data-stu-id="0024a-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0024a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="0024a-121">Example</span></span>  

 <span data-ttu-id="0024a-122">L'exemple de code ci-dessous montre comment créer un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une procédure stockée en définissant ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="0024a-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="0024a-123">Un objet <xref:System.Data.SqlClient.SqlParameter> permet de spécifier le paramètre d'entrée de la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="0024a-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="0024a-124">La commande est exécutée à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> et la sortie de <xref:System.Data.SqlClient.SqlDataReader> est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="0024a-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="0024a-125">Dépannage des commandes</span><span class="sxs-lookup"><span data-stu-id="0024a-125">Troubleshooting Commands</span></span>  

 <span data-ttu-id="0024a-126">Le fournisseur de données .NET Framework pour SQL Server ajoute des compteurs de performance pour vous permettre de détecter des problèmes intermittents liés à des échecs lors de l'exécution des commandes.</span><span class="sxs-lookup"><span data-stu-id="0024a-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="0024a-127">Pour plus d’informations, consultez [compteurs de performances](performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="0024a-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0024a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0024a-128">See also</span></span>

- [<span data-ttu-id="0024a-129">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="0024a-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="0024a-130">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="0024a-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="0024a-131">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0024a-131">ADO.NET Overview</span></span>](ado-net-overview.md)
