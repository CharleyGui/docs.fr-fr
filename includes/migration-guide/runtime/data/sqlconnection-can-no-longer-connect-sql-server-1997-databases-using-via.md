---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620003"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection ne peut plus se connecter à SQL Server 1997 ou des bases de données à l’aide de l’adaptateur VIA

#### <a name="details"></a>Détails

Les connexions aux bases de données SQL Server à l’aide du [protocole via (Virtual interface adapter)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) ne sont plus prises en charge. Le protocole utilisé pour se connecter à une base de données SQL Server est visible dans la chaîne de connexion. Une connexion VIA contiendra via:&lt;nom_serveur&gt;. Si cette application se connecte à SQL via un protocole autre que VIA (TCP : ou NP : par exemple), aucune modification avec rupture ne sera détectée. En outre, les connexions à SQL Server 7 (1997) ne sont plus prises en charge.

#### <a name="suggestion"></a>Suggestion

Comme le protocole VIA est déprécié, un autre protocole doit être utilisé pour se connecter aux bases de données SQL. Le protocole utilisé le plus courant est TCP/IP. Pour plus d’informations sur la connexion TCP/IP, voir [Activer le protocole TCP/IP pour une instance de base de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Si la base de données est accessible uniquement à partir d’un intranet, le protocole des canaux nommés peut offrir de meilleures performances en cas de réseau lent.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|
