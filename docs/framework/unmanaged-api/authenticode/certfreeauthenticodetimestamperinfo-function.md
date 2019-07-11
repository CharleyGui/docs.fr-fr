---
title: CertFreeAuthenticodeTimestamperInfo, fonction
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 680d9c959c57620ff38f8e785c670b451e5805b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741230"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="49064-102">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="49064-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="49064-103">Libère les ressources allouées pour le [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="49064-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49064-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49064-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49064-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49064-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="49064-106">[en entrée, en sortie] Les informations de l’horodateur à libérer.</span><span class="sxs-lookup"><span data-stu-id="49064-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="49064-107">Consultez le [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="49064-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49064-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49064-108">Return Value</span></span>  
 <span data-ttu-id="49064-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="49064-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="49064-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="49064-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49064-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49064-111">See also</span></span>

- [<span data-ttu-id="49064-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="49064-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
