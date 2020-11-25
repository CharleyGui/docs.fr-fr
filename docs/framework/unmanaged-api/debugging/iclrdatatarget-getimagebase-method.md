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
ms.openlocfilehash: f1b9f55a383f1deb867c6b3e2fa385a82158d1e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703575"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="f2fef-102">ICLRDataTarget::GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="f2fef-102">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="f2fef-103">Obtient l’adresse mémoire de base de l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2fef-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2fef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2fef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2fef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2fef-105">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="f2fef-106">dans Nom de fichier de l’image, y compris son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f2fef-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="f2fef-107">à Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="f2fef-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2fef-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2fef-108">Remarks</span></span>  

 <span data-ttu-id="f2fef-109">Le nom du fichier image peut ou non avoir un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f2fef-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="f2fef-110">Si un chemin d’accès est spécifié, la correspondance est effectuée sur le chemin d’accès entier ; dans le cas contraire, la correspondance est effectuée uniquement sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="f2fef-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2fef-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2fef-111">Requirements</span></span>  

 <span data-ttu-id="f2fef-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2fef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2fef-113">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f2fef-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f2fef-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2fef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2fef-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2fef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2fef-116">See also</span></span>

- [<span data-ttu-id="f2fef-117">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="f2fef-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
