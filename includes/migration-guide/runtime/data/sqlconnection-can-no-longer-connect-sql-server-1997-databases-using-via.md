---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606807"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection ne peut plus se connecter à SQL Server 1997 ou des bases de données à l’aide de l’adaptateur VIA

#### <a name="details"></a>Détails

Les connexions aux bases de données SQL Server à l’aide du [protocole via (Virtual interface adapter)](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) ne sont plus prises en charge. Le protocole utilisé pour se connecter à une base de données SQL Server est visible dans la chaîne de connexion. Une connexion VIA contiendra via:&lt;nom_serveur&gt;. Si cette application se connecte à SQL via un protocole autre que VIA (TCP : ou NP : par exemple), aucune modification avec rupture ne sera détectée. En outre, les connexions à SQL Server 7 (1997) ne sont plus prises en charge.

#### <a name="suggestion"></a>Suggestion

Comme le protocole VIA est déprécié, un autre protocole doit être utilisé pour se connecter aux bases de données SQL. Le protocole utilisé le plus courant est TCP/IP. Pour plus d’informations sur la connexion TCP/IP, voir [Activer le protocole TCP/IP pour une instance de base de données](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Si la base de données est accessible uniquement à partir d’un intranet, le protocole des canaux nommés peut offrir de meilleures performances en cas de réseau lent.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
