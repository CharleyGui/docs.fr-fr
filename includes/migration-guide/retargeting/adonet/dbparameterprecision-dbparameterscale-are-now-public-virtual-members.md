---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616055"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="ed521-101">DbParameter.Precision et DbParameter.Scale sont maintenant des membres virtuels publics</span><span class="sxs-lookup"><span data-stu-id="ed521-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="ed521-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ed521-102">Details</span></span>

<span data-ttu-id="ed521-103">Les propriétés <xref:System.Data.Common.DbParameter.Precision> et <xref:System.Data.Common.DbParameter.Scale> sont implémentées en tant que propriétés virtuelles publiques.</span><span class="sxs-lookup"><span data-stu-id="ed521-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="ed521-104">Elles remplacent les implémentations d'interface explicites correspondantes, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> et <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="ed521-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed521-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ed521-105">Suggestion</span></span>

<span data-ttu-id="ed521-106">Lorsque vous régénérez un fournisseur de base de données ADO.NET, vous devez désormais appliquer le mot clé « override » aux propriétés Precision et Scale.</span><span class="sxs-lookup"><span data-stu-id="ed521-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="ed521-107">Cette opération est nécessaire uniquement si vous régénérez les composants. Les fichiers binaires existants continuent de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="ed521-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="ed521-108">Nom</span><span class="sxs-lookup"><span data-stu-id="ed521-108">Name</span></span>    | <span data-ttu-id="ed521-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ed521-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed521-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="ed521-110">Scope</span></span>   | <span data-ttu-id="ed521-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ed521-111">Minor</span></span>       |
| <span data-ttu-id="ed521-112">Version</span><span class="sxs-lookup"><span data-stu-id="ed521-112">Version</span></span> | <span data-ttu-id="ed521-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ed521-113">4.5.1</span></span>       |
| <span data-ttu-id="ed521-114">Type</span><span class="sxs-lookup"><span data-stu-id="ed521-114">Type</span></span>    | <span data-ttu-id="ed521-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ed521-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ed521-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="ed521-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
