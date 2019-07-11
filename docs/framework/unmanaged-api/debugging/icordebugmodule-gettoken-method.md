---
title: ICorDebugModule::GetToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30097ff0cd92253897a366a5a18f305eddb06b5b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763516"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="27ec5-102">ICorDebugModule::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="27ec5-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="27ec5-103">Obtient le jeton pour l’entrée de table pour ce module.</span><span class="sxs-lookup"><span data-stu-id="27ec5-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ec5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27ec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27ec5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27ec5-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="27ec5-106">[out] Un pointeur vers le `mdModule` jeton qui référence les métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="27ec5-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27ec5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="27ec5-107">Remarks</span></span>  
 <span data-ttu-id="27ec5-108">Le jeton peut être passé à la [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), et [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfaces d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="27ec5-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27ec5-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27ec5-109">Requirements</span></span>  
 <span data-ttu-id="27ec5-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27ec5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27ec5-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27ec5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27ec5-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27ec5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27ec5-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27ec5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ec5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27ec5-114">See also</span></span>

- [<span data-ttu-id="27ec5-115">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="27ec5-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
