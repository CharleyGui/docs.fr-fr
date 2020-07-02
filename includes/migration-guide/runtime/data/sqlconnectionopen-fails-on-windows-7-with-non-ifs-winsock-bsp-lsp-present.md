---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622039"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open échoue sur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés

#### <a name="details"></a>Détails

<xref:System.Data.SqlClient.SqlConnection.Open> et <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> échouent dans .NET Framework 4.5 lors de l’exécution sur un ordinateur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés. Pour déterminer si un fournisseur BSP ou LSP non-IFS est installé, utilisez la commande <code>netsh WinSock Show Catalog</code> et examinez chaque élément <code>Winsock Catalog Provider Entry</code> retourné. Si la valeur des indicateurs de service est définie sur <code>0x20000</code>, le fournisseur utilise des gestionnaires IFS ce qui lui permet de fonctionner correctement. Si la valeur <code>0x20000</code> n’est pas définie, c’est qu’il s’agit d’un BSP ou d’un LSP non IFS.

#### <a name="suggestion"></a>Suggestion

Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également l’éviter en supprimant tous les LSP Winsock non IFS qui sont installés.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
