---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 95a1173dfbcc4cf49ded8c7b8a42d9764fee9aff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149399"
---
# <a name="oracletypes"></a><span data-ttu-id="52447-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="52447-102">OracleTypes</span></span>
<span data-ttu-id="52447-103">Le fournisseur de données .NET Framework pour Oracle inclut plusieurs structures que vous pouvez utiliser avec des types de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="52447-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="52447-104">Celles-ci comprennent <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="52447-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52447-105">Pour obtenir une liste complète de ces structures, voir <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="52447-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="52447-106">Les exemples C# suivants :</span><span class="sxs-lookup"><span data-stu-id="52447-106">The following C# examples:</span></span>  
  
- <span data-ttu-id="52447-107">créent une table Oracle et la chargent de données.</span><span class="sxs-lookup"><span data-stu-id="52447-107">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="52447-108">Utilisez un <xref:System.Data.OracleClient.OracleDataReader> pour accéder aux données et utilisez plusieurs structures <xref:System.Data.OracleClient.OracleType> pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="52447-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="52447-109">Création d'une table Oracle</span><span class="sxs-lookup"><span data-stu-id="52447-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="52447-110">Cet exemple crée une table Oracle et la charge de données.</span><span class="sxs-lookup"><span data-stu-id="52447-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="52447-111">Vous devez exécuter cet exemple avant d'exécuter l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="52447-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="52447-112">Extraction de données de la table Oracle</span><span class="sxs-lookup"><span data-stu-id="52447-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="52447-113">Cet exemple utilise un **OracleDataReader** pour accéder aux données, et utilise plusieurs structures **OracleType** pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="52447-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="52447-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52447-114">See also</span></span>

- [<span data-ttu-id="52447-115">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="52447-115">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="52447-116">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="52447-116">ADO.NET Overview</span></span>](ado-net-overview.md)
