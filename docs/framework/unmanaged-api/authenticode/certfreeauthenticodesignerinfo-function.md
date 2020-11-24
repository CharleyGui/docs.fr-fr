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
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674175"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="1043e-102">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="1043e-102">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="1043e-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1043e-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1043e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1043e-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1043e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1043e-105">Parameters</span></span>  

 `pSignerInfo`  
 <span data-ttu-id="1043e-106">[en entrée, en sortie] Les informations du signataire à libérer.</span><span class="sxs-lookup"><span data-stu-id="1043e-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="1043e-107">Consultez la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1043e-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1043e-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1043e-108">Return Value</span></span>  

 <span data-ttu-id="1043e-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="1043e-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="1043e-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1043e-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1043e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1043e-111">See also</span></span>

- [<span data-ttu-id="1043e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1043e-112">Authenticode</span></span>](index.md)
