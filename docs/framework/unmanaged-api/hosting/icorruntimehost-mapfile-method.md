---
title: ICorRuntimeHost::MapFile, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: bcf1b49f0576f5dbd73c001f8edff7a9ab29af22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139500"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="e7913-102">ICorRuntimeHost::MapFile, méthode</span><span class="sxs-lookup"><span data-stu-id="e7913-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="e7913-103">Mappe le fichier spécifié en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e7913-103">Maps the specified file into memory.</span></span> <span data-ttu-id="e7913-104">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="e7913-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7913-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7913-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7913-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e7913-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="e7913-107">dans Handle du fichier à mapper.</span><span class="sxs-lookup"><span data-stu-id="e7913-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="e7913-108">à Adresse de départ de la mémoire à laquelle commencer le mappage du fichier.</span><span class="sxs-lookup"><span data-stu-id="e7913-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7913-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="e7913-109">Requirements</span></span>  
 <span data-ttu-id="e7913-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7913-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7913-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7913-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7913-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e7913-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7913-113">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e7913-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7913-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7913-114">See also</span></span>

- [<span data-ttu-id="e7913-115">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="e7913-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
