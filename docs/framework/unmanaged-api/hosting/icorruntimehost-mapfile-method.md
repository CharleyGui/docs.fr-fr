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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762667"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="a5fb4-102">ICorRuntimeHost::MapFile, méthode</span><span class="sxs-lookup"><span data-stu-id="a5fb4-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="a5fb4-103">Mappe le fichier spécifié en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-103">Maps the specified file into memory.</span></span> <span data-ttu-id="a5fb4-104">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fb4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5fb4-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5fb4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5fb4-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="a5fb4-107">dans Handle du fichier à mapper.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="a5fb4-108">à Adresse de départ de la mémoire à laquelle commencer le mappage du fichier.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5fb4-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a5fb4-109">Requirements</span></span>  
 <span data-ttu-id="a5fb4-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5fb4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5fb4-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5fb4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5fb4-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5fb4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5fb4-113">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a5fb4-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fb4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5fb4-114">See also</span></span>

- [<span data-ttu-id="a5fb4-115">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a5fb4-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
