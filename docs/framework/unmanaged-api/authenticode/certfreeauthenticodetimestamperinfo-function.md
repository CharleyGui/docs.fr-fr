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
ms.openlocfilehash: 4f0806e0273b111e3398fb8f2884231b96cf1116
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099769"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="f698c-102">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="f698c-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="f698c-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f698c-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f698c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f698c-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f698c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f698c-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="f698c-106">[en entrée, en sortie] Les informations de l’horodateur à libérer.</span><span class="sxs-lookup"><span data-stu-id="f698c-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="f698c-107">Consultez la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f698c-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f698c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f698c-108">Return Value</span></span>  
 <span data-ttu-id="f698c-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="f698c-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f698c-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f698c-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f698c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f698c-111">See also</span></span>

- [<span data-ttu-id="f698c-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f698c-112">Authenticode</span></span>](index.md)
