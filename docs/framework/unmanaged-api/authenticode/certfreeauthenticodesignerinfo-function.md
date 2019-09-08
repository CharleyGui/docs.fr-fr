---
title: CertFreeAuthenticodeSignerInfo, fonction
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776726"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="29b27-102">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="29b27-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="29b27-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="29b27-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29b27-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b27-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29b27-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="29b27-106">[en entrée, en sortie] Les informations du signataire à libérer.</span><span class="sxs-lookup"><span data-stu-id="29b27-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="29b27-107">Consultez la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="29b27-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29b27-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="29b27-108">Return Value</span></span>  
 <span data-ttu-id="29b27-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="29b27-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="29b27-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="29b27-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b27-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29b27-111">See also</span></span>

- [<span data-ttu-id="29b27-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="29b27-112">Authenticode</span></span>](index.md)
