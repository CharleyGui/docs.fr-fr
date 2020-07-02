---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617176"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="a729d-101">Les méthodes MachineKey.Encode et MachineKey.Decode sont maintenant obsolètes</span><span class="sxs-lookup"><span data-stu-id="a729d-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="a729d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a729d-102">Details</span></span>

<span data-ttu-id="a729d-103">Ces méthodes sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="a729d-103">These methods are now obsolete.</span></span> <span data-ttu-id="a729d-104">La compilation du code qui appelle ces méthodes génère un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a729d-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a729d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a729d-105">Suggestion</span></span>

<span data-ttu-id="a729d-106">Les alternatives recommandées sont <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> et <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="a729d-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="a729d-107">Vous pouvez également supprimer les avertissements de génération, ou les éviter en utilisant un compilateur plus ancien.</span><span class="sxs-lookup"><span data-stu-id="a729d-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="a729d-108">Ces API sont toujours prises en charge.</span><span class="sxs-lookup"><span data-stu-id="a729d-108">The APIs are still supported.</span></span>

| <span data-ttu-id="a729d-109">Nom</span><span class="sxs-lookup"><span data-stu-id="a729d-109">Name</span></span>    | <span data-ttu-id="a729d-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="a729d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a729d-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="a729d-111">Scope</span></span>   | <span data-ttu-id="a729d-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="a729d-112">Minor</span></span>       |
| <span data-ttu-id="a729d-113">Version</span><span class="sxs-lookup"><span data-stu-id="a729d-113">Version</span></span> | <span data-ttu-id="a729d-114">4,5</span><span class="sxs-lookup"><span data-stu-id="a729d-114">4.5</span></span>         |
| <span data-ttu-id="a729d-115">Type</span><span class="sxs-lookup"><span data-stu-id="a729d-115">Type</span></span>    | <span data-ttu-id="a729d-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="a729d-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a729d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="a729d-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
