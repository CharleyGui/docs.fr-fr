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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786992"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="583b7-102">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="583b7-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="583b7-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="583b7-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="583b7-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="583b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="583b7-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="583b7-106">[en entrée, en sortie] Les informations de l’horodateur à libérer.</span><span class="sxs-lookup"><span data-stu-id="583b7-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="583b7-107">Consultez la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="583b7-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="583b7-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="583b7-108">Return Value</span></span>  
 <span data-ttu-id="583b7-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="583b7-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="583b7-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="583b7-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583b7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="583b7-111">See also</span></span>

- [<span data-ttu-id="583b7-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="583b7-112">Authenticode</span></span>](index.md)
