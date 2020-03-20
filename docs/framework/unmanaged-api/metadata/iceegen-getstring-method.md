---
title: ICeeGen::GetString, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177904"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="27f30-102">ICeeGen::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="27f30-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="27f30-103">Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="27f30-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="27f30-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="27f30-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f30-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27f30-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f30-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27f30-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="27f30-107">[dans] L’adresse virtuelle relative de la chaîne à revenir.</span><span class="sxs-lookup"><span data-stu-id="27f30-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="27f30-108">[out] La ficelle retournée.</span><span class="sxs-lookup"><span data-stu-id="27f30-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f30-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27f30-109">Requirements</span></span>  
 <span data-ttu-id="27f30-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f30-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f30-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="27f30-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27f30-112">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27f30-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27f30-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f30-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f30-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f30-114">See also</span></span>

- [<span data-ttu-id="27f30-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="27f30-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
