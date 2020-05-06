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
ms.openlocfilehash: 71b07e11cd3fec1a0dbebe986d98067c2e6f18e1
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860632"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="56f84-102">ICLRDataTarget::GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="56f84-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="56f84-103">Obtient l’adresse mémoire de base de l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="56f84-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56f84-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56f84-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="56f84-106">dans Nom de fichier de l’image, y compris son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="56f84-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="56f84-107">à Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="56f84-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f84-108">Notes </span><span class="sxs-lookup"><span data-stu-id="56f84-108">Remarks</span></span>  
 <span data-ttu-id="56f84-109">Le nom du fichier image peut ou non avoir un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="56f84-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="56f84-110">Si un chemin d’accès est spécifié, la correspondance est effectuée sur le chemin d’accès entier ; dans le cas contraire, la correspondance est effectuée uniquement sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="56f84-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f84-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="56f84-111">Requirements</span></span>  
 <span data-ttu-id="56f84-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f84-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f84-113">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="56f84-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="56f84-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56f84-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f84-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f84-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f84-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56f84-116">See also</span></span>

- [<span data-ttu-id="56f84-117">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="56f84-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
