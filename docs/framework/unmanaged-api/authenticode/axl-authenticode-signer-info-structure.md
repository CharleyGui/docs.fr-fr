---
title: AXL_AUTHENTICODE_SIGNER_INFO, structure
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 232c78db32aecd0ee1379d4d969fa0378db4159a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741359"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="2b6a0-102">AXL_AUTHENTICODE_SIGNER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="2b6a0-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="2b6a0-103">Définit les informations du signataire Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b6a0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2b6a0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2b6a0-105">Members</span></span>  
  
|<span data-ttu-id="2b6a0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2b6a0-106">Member</span></span>|<span data-ttu-id="2b6a0-107">Description</span><span class="sxs-lookup"><span data-stu-id="2b6a0-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="2b6a0-108">La taille de cette structure.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="2b6a0-109">Le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="2b6a0-110">L'algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="2b6a0-111">Le hachage.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="2b6a0-112">La description.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="2b6a0-113">L'URL de la description.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="2b6a0-114">Le contexte de chaîne du signataire.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-114">The chain context of the signer.</span></span> <span data-ttu-id="2b6a0-115">Consultez le [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span><span class="sxs-lookup"><span data-stu-id="2b6a0-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b6a0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b6a0-116">See also</span></span>

- [<span data-ttu-id="2b6a0-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2b6a0-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
