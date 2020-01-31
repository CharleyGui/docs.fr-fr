---
title: Méthode ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783580"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="14103-102">Méthode ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="14103-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="14103-103">Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="14103-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14103-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14103-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14103-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="14103-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="14103-106">dans Valeur [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="14103-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="14103-107">[in] Nombre de caractères dans la mémoire tampon qui reçoit le chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="14103-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="14103-108">[out] Pointeur vers le nombre de caractères écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="14103-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="14103-109">[out] Chemin d'accès du module.</span><span class="sxs-lookup"><span data-stu-id="14103-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14103-110">Notes</span><span class="sxs-lookup"><span data-stu-id="14103-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14103-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14103-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14103-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="14103-112">Requirements</span></span>  
 <span data-ttu-id="14103-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14103-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14103-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14103-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14103-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14103-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14103-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14103-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14103-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14103-117">See also</span></span>

- [<span data-ttu-id="14103-118">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="14103-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="14103-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="14103-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
