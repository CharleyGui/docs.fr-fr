---
title: ICorDebugLoadedModule::GetName (méthode)
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4a0c4e99f23dc949b0bbaa8bbda35cff1537cf3c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209862"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="361c4-102">ICorDebugLoadedModule::GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="361c4-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="361c4-103">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="361c4-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="361c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="361c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="361c4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="361c4-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="361c4-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="361c4-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="361c4-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="361c4-108">[out] Tableau de caractères contenant le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="361c4-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="361c4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="361c4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="361c4-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="361c4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="361c4-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="361c4-111">Requirements</span></span>  
 <span data-ttu-id="361c4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="361c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="361c4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="361c4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="361c4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="361c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="361c4-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="361c4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="361c4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="361c4-116">See also</span></span>

- [<span data-ttu-id="361c4-117">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="361c4-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="361c4-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="361c4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
