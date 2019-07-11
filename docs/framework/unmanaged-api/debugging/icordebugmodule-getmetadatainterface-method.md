---
title: ICorDebugModule::GetMetaDataInterface, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 398c48bfd30020efdb57861991c9541d412d3e0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763434"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="e9e5e-102">ICorDebugModule::GetMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="e9e5e-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="e9e5e-103">Obtient un objet d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées pour le module.</span><span class="sxs-lookup"><span data-stu-id="e9e5e-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9e5e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9e5e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9e5e-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e9e5e-106">[in] L’ID de référence qui spécifie l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e9e5e-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="e9e5e-107">[out] Un pointeur vers l’adresse d’un `T:IUnknown` objet qui est un de la [interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="e9e5e-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9e5e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e9e5e-108">Remarks</span></span>  
 <span data-ttu-id="e9e5e-109">Le débogueur peut utiliser le `GetMetaDataInterface` méthode pour effectuer une copie des métadonnées d’origine pour un module, il doit faire pour modifier ce module.</span><span class="sxs-lookup"><span data-stu-id="e9e5e-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="e9e5e-110">Le débogueur appelle `GetMetaDataInterface` pour obtenir un [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objet d’interface pour le module, puis appelle [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) pour enregistrer une copie des métadonnées du module dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9e5e-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e5e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e9e5e-111">Requirements</span></span>  
 <span data-ttu-id="e9e5e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9e5e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e5e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9e5e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9e5e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9e5e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9e5e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e5e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e5e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9e5e-116">See also</span></span>

- [<span data-ttu-id="e9e5e-117">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="e9e5e-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
