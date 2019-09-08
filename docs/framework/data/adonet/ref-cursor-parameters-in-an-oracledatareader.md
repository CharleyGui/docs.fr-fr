---
title: Paramètres REF CURSOR dans un OracleDataReader
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 801dff0f-2508-45aa-9416-f45d6887740c
ms.openlocfilehash: 3622e21978377aed42958e2dc96ef9aa5a872d00
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782913"
---
# <a name="ref-cursor-parameters-in-an-oracledatareader"></a><span data-ttu-id="b8c2d-102">Paramètres REF CURSOR dans un OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="b8c2d-102">REF CURSOR Parameters in an OracleDataReader</span></span>
<span data-ttu-id="b8c2d-103">Cet exemple Microsoft Visual Basic exécute une procédure stockée PL/SQL qui retourne un paramètre REF CURSOR et lit la valeur comme un <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b8c2d-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_ONE_CURSOR"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter(  
      "N_EMPNO", OracleType.Number)).Value = 7369  
    cmd.Parameters.Add(New OracleParameter(  
      "IO_CURSOR", OracleType.Cursor)).Direction = ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader()  
    While (rdr.Read())  
        REM do something with the values  
    End While  
  
    rdr.Close()  
  End Using  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8c2d-104">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8c2d-104">See also</span></span>

- [<span data-ttu-id="b8c2d-105">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="b8c2d-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="b8c2d-106">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8c2d-106">ADO.NET Overview</span></span>](ado-net-overview.md)
