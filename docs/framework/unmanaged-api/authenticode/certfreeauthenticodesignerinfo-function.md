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
ms.openlocfilehash: a233e0b8d17b9ee61b1991086f794c9fb20f89e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099832"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="46869-102">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="46869-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="46869-103">Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="46869-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46869-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46869-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46869-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46869-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="46869-106">[en entrée, en sortie] Les informations du signataire à libérer.</span><span class="sxs-lookup"><span data-stu-id="46869-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="46869-107">Consultez la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="46869-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46869-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="46869-108">Return Value</span></span>  
 <span data-ttu-id="46869-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="46869-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="46869-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="46869-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46869-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46869-111">See also</span></span>

- [<span data-ttu-id="46869-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="46869-112">Authenticode</span></span>](index.md)
