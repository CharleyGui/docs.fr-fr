---
ms.openlocfilehash: d7a18a0b457c2a38f40c1da3b2f0bfc578259475
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621068"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>La période de blocage du pool de connexions pour les bases de données Azure SQL Database est supprimée

#### <a name="details"></a>Détails

À partir de la .NET Framework 4.6.2, pour les demandes d’ouverture de connexion aux bases de données Azure SQL connues ( \* . Database.Windows.net, \* . Database.chinacloudapi.CN,. \* database.usgovcloudapi.net, \* . Database.cloudapi.de), la période de blocage du pool de connexions est supprimée et les erreurs d’ouverture de connexion ne sont pas mises en cache. Chaque nouvelle tentative de demande d’ouverture de connexion se produira presque immédiatement après les erreurs de connexion temporaires. Ce changement permet aux demandes d’ouverture de connexion d’être retentées immédiatement pour les bases de données Azure SQL Database, ce qui améliore les performances des applications cloud. Pour toutes les autres tentatives de connexion, la période de blocage du pool de connexions continue d’être appliquée.<p/>Dans .NET Framework 4.6.1 et antérieur, quand une application rencontre un échec temporaire durant la connexion à une base de données, la connexion ne peut pas être retentée rapidement, car le pool de connexions met l’erreur en cache, puis l’affiche de nouveau pendant 5 secondes à 1 minute. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Ce comportement pose problème pour les connexions aux bases de données SQL Azure, qui échouent souvent avec des erreurs temporaires, généralement rétablies au bout de quelques secondes. La fonctionnalité de blocage du pool de connexions signifie que l’application ne peut pas se connecter à la base de données pendant une période prolongée, même si la base de données est disponible et que l’application doit être affichée en quelques secondes.

#### <a name="suggestion"></a>Suggestion

Si ce comportement n’est pas souhaitable, la période de blocage du pool de connexions peut être configurée en définissant la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> introduite dans .NET Framework 4.6.2. La valeur de la propriété est un membre de l’énumération <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> qui peut prendre l’une des trois valeurs suivantes :<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Vous pouvez restaurer le comportement précédent en affectant la valeur <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
