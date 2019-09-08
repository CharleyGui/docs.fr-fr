---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7879e1f6598108d839287792ed441391764ae2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776646"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="57786-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="57786-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="57786-103">Définit les informations de l'horodateur Authenticode.</span><span class="sxs-lookup"><span data-stu-id="57786-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57786-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="57786-105">Membres</span><span class="sxs-lookup"><span data-stu-id="57786-105">Members</span></span>  
  
|<span data-ttu-id="57786-106">Membre</span><span class="sxs-lookup"><span data-stu-id="57786-106">Member</span></span>|<span data-ttu-id="57786-107">Description</span><span class="sxs-lookup"><span data-stu-id="57786-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="57786-108">La taille de cette structure.</span><span class="sxs-lookup"><span data-stu-id="57786-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="57786-109">Le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="57786-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="57786-110">L'algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="57786-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="57786-111">La date/heure de l'horodatage.</span><span class="sxs-lookup"><span data-stu-id="57786-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="57786-112">La chaîne de contexte de l'horodateur.</span><span class="sxs-lookup"><span data-stu-id="57786-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="57786-113">Consultez la structure [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="57786-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57786-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57786-114">See also</span></span>

- [<span data-ttu-id="57786-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="57786-115">Authenticode</span></span>](index.md)
