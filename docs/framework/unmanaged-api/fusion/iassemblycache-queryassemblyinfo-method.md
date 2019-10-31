---
title: IAssemblyCache::QueryAssemblyInfo, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
ms.openlocfilehash: e975db68252e866a0bf7898f1c9d3cbe67bbe24f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134577"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="ab08f-102">IAssemblyCache::QueryAssemblyInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="ab08f-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="ab08f-103">Obtient les données demandées relatives à l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab08f-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab08f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab08f-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab08f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab08f-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ab08f-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="ab08f-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="ab08f-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="ab08f-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="ab08f-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="ab08f-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="ab08f-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="ab08f-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="ab08f-110">dans Nom de l’assembly pour lequel les données seront récupérées.</span><span class="sxs-lookup"><span data-stu-id="ab08f-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="ab08f-111">[in, out] Structure [ASSEMBLY_INFO](assembly-info-structure.md) qui contient les données relatives à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ab08f-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab08f-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="ab08f-112">Requirements</span></span>  
 <span data-ttu-id="ab08f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab08f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab08f-114">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ab08f-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ab08f-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab08f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab08f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab08f-116">See also</span></span>

- [<span data-ttu-id="ab08f-117">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="ab08f-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
