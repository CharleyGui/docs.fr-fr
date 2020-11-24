---
title: AXL_AUTHENTICODE_SIGNER_INFO, structure
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 1bb6df4aa82f8dfc367083732af2065aba9d07b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679986"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="abc53-102">AXL_AUTHENTICODE_SIGNER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="abc53-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="abc53-103">Définit les informations du signataire Authenticode.</span><span class="sxs-lookup"><span data-stu-id="abc53-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc53-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="abc53-105">Membres</span><span class="sxs-lookup"><span data-stu-id="abc53-105">Members</span></span>  
  
|<span data-ttu-id="abc53-106">Membre</span><span class="sxs-lookup"><span data-stu-id="abc53-106">Member</span></span>|<span data-ttu-id="abc53-107">Description</span><span class="sxs-lookup"><span data-stu-id="abc53-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="abc53-108">La taille de cette structure.</span><span class="sxs-lookup"><span data-stu-id="abc53-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="abc53-109">Code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="abc53-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="abc53-110">L'algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="abc53-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="abc53-111">Hachage.</span><span class="sxs-lookup"><span data-stu-id="abc53-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="abc53-112">Description.</span><span class="sxs-lookup"><span data-stu-id="abc53-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="abc53-113">L'URL de la description.</span><span class="sxs-lookup"><span data-stu-id="abc53-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="abc53-114">Le contexte de chaîne du signataire.</span><span class="sxs-lookup"><span data-stu-id="abc53-114">The chain context of the signer.</span></span> <span data-ttu-id="abc53-115">Consultez la structure [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="abc53-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abc53-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abc53-116">See also</span></span>

- [<span data-ttu-id="abc53-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="abc53-117">Authenticode</span></span>](index.md)
