---
title: ICLRDataTarget::GetImageBase, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: fed643ae52f50b1b8cd134880c644c8941da6f56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122876"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="2e121-102">ICLRDataTarget::GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="2e121-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="2e121-103">Obtient l’adresse mémoire de base de l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2e121-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e121-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e121-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e121-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="2e121-106">dans Nom de fichier de l’image, y compris son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2e121-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="2e121-107">à Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="2e121-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e121-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2e121-108">Remarks</span></span>  
 <span data-ttu-id="2e121-109">Le nom du fichier image peut ou non avoir un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2e121-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="2e121-110">Si un chemin d’accès est spécifié, la correspondance est effectuée sur le chemin d’accès entier ; dans le cas contraire, la correspondance est effectuée uniquement sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2e121-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e121-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="2e121-111">Requirements</span></span>  
 <span data-ttu-id="2e121-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e121-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e121-113">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="2e121-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2e121-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e121-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e121-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e121-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e121-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e121-116">See also</span></span>

- [<span data-ttu-id="2e121-117">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="2e121-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
