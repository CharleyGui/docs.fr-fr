---
ms.openlocfilehash: fd9f4f3de8f7be39242d4ff6924d480f20a1a06b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496277"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="ba9e3-101">SqlBulkCopy utilise l’encodage de la colonne de destination pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="ba9e3-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="ba9e3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ba9e3-102">Details</span></span>

<span data-ttu-id="ba9e3-103">Lors de l'insertion de données dans une colonne, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> utilise l'encodage de la colonne de destination plutôt que l'encodage par défaut pour les types <code>VARCHAR</code> et <code>CHAR</code>.</span><span class="sxs-lookup"><span data-stu-id="ba9e3-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="ba9e3-104">Cette modification élimine la possibilité d'altération de données provoquée par l'utilisation de l'encodage par défaut lorsque la colonne de destination n'utilise pas l'encodage par défaut.</span><span class="sxs-lookup"><span data-stu-id="ba9e3-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="ba9e3-105">Dans de rares cas, une application existante peut lever une exception SqlException si la modification de l’encodage produit des données qui sont trop volumineuses pour s’insérer dans la colonne de destination.</span><span class="sxs-lookup"><span data-stu-id="ba9e3-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ba9e3-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ba9e3-106">Suggestion</span></span>

<span data-ttu-id="ba9e3-107">Attendez-vous à ce que <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> n’endommage plus les données en raison des différences d’encodage.</span><span class="sxs-lookup"><span data-stu-id="ba9e3-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="ba9e3-108">Si des chaînes près de la limite de taille de la colonne de destination sont copiées, il peut être nécessaire d’encoder au préalable les données (à copier pour vérifier que les données contiennent dans la colonne de destination) ou d’intercepter les <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ba9e3-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="ba9e3-109">Name</span><span class="sxs-lookup"><span data-stu-id="ba9e3-109">Name</span></span>    | <span data-ttu-id="ba9e3-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="ba9e3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ba9e3-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="ba9e3-111">Scope</span></span>   |<span data-ttu-id="ba9e3-112">Edge</span><span class="sxs-lookup"><span data-stu-id="ba9e3-112">Edge</span></span>|
|<span data-ttu-id="ba9e3-113">Version</span><span class="sxs-lookup"><span data-stu-id="ba9e3-113">Version</span></span>|<span data-ttu-id="ba9e3-114">4,5</span><span class="sxs-lookup"><span data-stu-id="ba9e3-114">4.5</span></span>|
|<span data-ttu-id="ba9e3-115">Type</span><span class="sxs-lookup"><span data-stu-id="ba9e3-115">Type</span></span>|<span data-ttu-id="ba9e3-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="ba9e3-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ba9e3-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="ba9e3-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)>

<!--

#### Affected APIs

- `T:System.Data.SqlClient.SqlBulkCopy`
- `M:System.Data.SqlClient.SqlBulkCopy.#ctor(System.Data.SqlClient.SqlConnection)`

-->
