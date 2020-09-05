---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496343"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="3880d-101">SqlConnection.Open échoue sur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés</span><span class="sxs-lookup"><span data-stu-id="3880d-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="3880d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3880d-102">Details</span></span>

<span data-ttu-id="3880d-103"><xref:System.Data.SqlClient.SqlConnection.Open> et <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> échouent dans .NET Framework 4.5 lors de l’exécution sur un ordinateur Windows 7 si des fournisseurs Winsock BSP ou LSP non-IFS sont installés. Pour déterminer si un fournisseur BSP ou LSP non-IFS est installé, utilisez la commande <code>netsh WinSock Show Catalog</code> et examinez chaque élément <code>Winsock Catalog Provider Entry</code> retourné.</span><span class="sxs-lookup"><span data-stu-id="3880d-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="3880d-104">Si la valeur des indicateurs de service est définie sur <code>0x20000</code>, le fournisseur utilise des gestionnaires IFS ce qui lui permet de fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="3880d-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="3880d-105">Si la valeur <code>0x20000</code> n’est pas définie, c’est qu’il s’agit d’un BSP ou d’un LSP non IFS.</span><span class="sxs-lookup"><span data-stu-id="3880d-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3880d-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3880d-106">Suggestion</span></span>

<span data-ttu-id="3880d-107">Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3880d-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="3880d-108">Vous pouvez également l’éviter en supprimant tous les LSP Winsock non IFS qui sont installés.</span><span class="sxs-lookup"><span data-stu-id="3880d-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="3880d-109">Name</span><span class="sxs-lookup"><span data-stu-id="3880d-109">Name</span></span>    | <span data-ttu-id="3880d-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="3880d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3880d-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="3880d-111">Scope</span></span>   |<span data-ttu-id="3880d-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3880d-112">Minor</span></span>|
|<span data-ttu-id="3880d-113">Version</span><span class="sxs-lookup"><span data-stu-id="3880d-113">Version</span></span>|<span data-ttu-id="3880d-114">4,5</span><span class="sxs-lookup"><span data-stu-id="3880d-114">4.5</span></span>|
|<span data-ttu-id="3880d-115">Type</span><span class="sxs-lookup"><span data-stu-id="3880d-115">Type</span></span>|<span data-ttu-id="3880d-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="3880d-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3880d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="3880d-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
