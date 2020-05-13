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
ms.openlocfilehash: 8f3cc16054d4b5340c9460e9c3fbcba6e563567a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212553"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="25740-102">ICorDebugModule::GetMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="25740-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="25740-103">Obtient un objet d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="25740-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25740-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25740-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25740-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25740-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="25740-106">dans ID de référence qui spécifie l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="25740-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="25740-107">à Pointeur vers l’adresse d’un `T:IUnknown` objet qui est l’une des [interfaces de métadonnées](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="25740-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25740-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="25740-108">Remarks</span></span>  
 <span data-ttu-id="25740-109">Le débogueur peut utiliser la `GetMetaDataInterface` méthode pour effectuer une copie des métadonnées d’origine d’un module, ce qu’il doit faire pour modifier ce module.</span><span class="sxs-lookup"><span data-stu-id="25740-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="25740-110">Le débogueur appelle `GetMetaDataInterface` pour obtenir un objet d’interface [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) pour le module, puis appelle [IMetaDataEmit :: SaveToMemory,](../metadata/imetadataemit-savetomemory-method.md) pour enregistrer une copie des métadonnées du module dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="25740-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25740-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25740-111">Requirements</span></span>  
 <span data-ttu-id="25740-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25740-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25740-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25740-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25740-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25740-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25740-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25740-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25740-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25740-116">See also</span></span>

- [<span data-ttu-id="25740-117">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="25740-117">Metadata</span></span>](../metadata/index.md)
