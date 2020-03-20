---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803271"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open échoue sur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés

|   |   |
|---|---|
|Détails|<xref:System.Data.SqlClient.SqlConnection.Open> et <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> échouent dans .NET Framework 4.5 lors de l’exécution sur un ordinateur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés. Pour déterminer si un fournisseur BSP ou LSP non-IFS est installé, utilisez la commande <code>netsh WinSock Show Catalog</code> et examinez chaque élément <code>Winsock Catalog Provider Entry</code> retourné. Si la valeur des indicateurs de service est définie sur <code>0x20000</code>, le fournisseur utilise des gestionnaires IFS ce qui lui permet de fonctionner correctement. Si la valeur <code>0x20000</code> n’est pas définie, c’est qu’il s’agit d’un BSP ou d’un LSP non IFS.|
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également l’éviter en supprimant tous les LSP Winsock non IFS qui sont installés.|
|Étendue|Secondaire|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
