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
ms.openlocfilehash: 3b9c2f0e20488826aca202b3ef454104964b8bb9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210343"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="3de0d-102">ICorDebugILCode2::GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="3de0d-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="3de0d-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="3de0d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3de0d-104">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="3de0d-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de0d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3de0d-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3de0d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3de0d-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="3de0d-107">[en sortie] Un pointeur vers le jeton `mdSignature` pour la signature de variable globale pour cette fonction, ou `mdSignatureNil` s'il n'y a pas de signature (c'est-à-dire si la fonction n'a aucune variable locale).</span><span class="sxs-lookup"><span data-stu-id="3de0d-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de0d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="3de0d-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de0d-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3de0d-109">Requirements</span></span>  
 <span data-ttu-id="3de0d-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de0d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de0d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3de0d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3de0d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3de0d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de0d-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de0d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de0d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3de0d-114">See also</span></span>

- [<span data-ttu-id="3de0d-115">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="3de0d-115">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="3de0d-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3de0d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
