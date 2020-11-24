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
ms.openlocfilehash: 60e1d5d49f6f8c6fec060d8751e94410986aa3fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671380"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="19038-102">ICorRuntimeHost::MapFile, méthode</span><span class="sxs-lookup"><span data-stu-id="19038-102">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="19038-103">Mappe le fichier spécifié en mémoire.</span><span class="sxs-lookup"><span data-stu-id="19038-103">Maps the specified file into memory.</span></span> <span data-ttu-id="19038-104">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="19038-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19038-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19038-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19038-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19038-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="19038-107">dans Handle du fichier à mapper.</span><span class="sxs-lookup"><span data-stu-id="19038-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="19038-108">à Adresse de départ de la mémoire à laquelle commencer le mappage du fichier.</span><span class="sxs-lookup"><span data-stu-id="19038-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19038-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="19038-109">Requirements</span></span>  

 <span data-ttu-id="19038-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19038-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19038-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19038-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19038-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19038-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19038-113">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="19038-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19038-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19038-114">See also</span></span>

- [<span data-ttu-id="19038-115">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="19038-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
