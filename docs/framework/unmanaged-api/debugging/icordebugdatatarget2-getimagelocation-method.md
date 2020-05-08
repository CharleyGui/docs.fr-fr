---
title: ICorDebugDataTarget2::GetImageLocation, méthode
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: 185b6a4979491a323f6eb15ab08a06f87fabc8d3
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976458"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="51044-102">ICorDebugDataTarget2::GetImageLocation, méthode</span><span class="sxs-lookup"><span data-stu-id="51044-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="51044-103">Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="51044-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51044-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51044-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51044-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51044-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="51044-106">dans Valeur [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="51044-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="51044-107">[in] Nombre de caractères dans la mémoire tampon qui reçoit le chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="51044-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="51044-108">[out] Pointeur vers le nombre de caractères écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="51044-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="51044-109">[out] Chemin d'accès du module.</span><span class="sxs-lookup"><span data-stu-id="51044-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51044-110">Notes </span><span class="sxs-lookup"><span data-stu-id="51044-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51044-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51044-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51044-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="51044-112">Requirements</span></span>  
 <span data-ttu-id="51044-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51044-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51044-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51044-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51044-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51044-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51044-116">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51044-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51044-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51044-117">See also</span></span>

- [<span data-ttu-id="51044-118">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="51044-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="51044-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="51044-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
