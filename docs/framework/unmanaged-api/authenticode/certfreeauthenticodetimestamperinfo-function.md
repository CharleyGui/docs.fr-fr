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
ms.openlocfilehash: 1ef71b14faf66c179030dff2a7d953e27463c1f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674162"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="906f0-102">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="906f0-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="906f0-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="906f0-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="906f0-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="906f0-105">Parameters</span></span>  

 `pTimestamperInfo`  
 <span data-ttu-id="906f0-106">[en entrée, en sortie] Les informations de l’horodateur à libérer.</span><span class="sxs-lookup"><span data-stu-id="906f0-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="906f0-107">Consultez la structure [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="906f0-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="906f0-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="906f0-108">Return Value</span></span>  

 <span data-ttu-id="906f0-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="906f0-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="906f0-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="906f0-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906f0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="906f0-111">See also</span></span>

- [<span data-ttu-id="906f0-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="906f0-112">Authenticode</span></span>](index.md)
