---
title: ICorDebugILCode2::GetLocalVarSigToken, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: 3759cfa330ac37d2ed62a0b8bb70b5e10cd9d12e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782445"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="46339-102">ICorDebugILCode2::GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="46339-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="46339-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="46339-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="46339-104">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="46339-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46339-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46339-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46339-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="46339-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="46339-107">[en sortie] Un pointeur vers le jeton `mdSignature` pour la signature de variable globale pour cette fonction, ou `mdSignatureNil` s'il n'y a pas de signature (c'est-à-dire si la fonction n'a aucune variable locale).</span><span class="sxs-lookup"><span data-stu-id="46339-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46339-108">Notes</span><span class="sxs-lookup"><span data-stu-id="46339-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46339-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="46339-109">Requirements</span></span>  
 <span data-ttu-id="46339-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46339-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46339-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46339-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46339-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46339-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46339-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46339-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46339-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46339-114">See also</span></span>

- [<span data-ttu-id="46339-115">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="46339-115">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="46339-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="46339-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
