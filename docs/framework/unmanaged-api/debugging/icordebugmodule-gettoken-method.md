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
ms.openlocfilehash: a6aff37a480460bfed7064d59b4c5276daf3207c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212501"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="059db-102">ICorDebugModule::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="059db-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="059db-103">Obtient le jeton pour l’entrée de table pour ce module.</span><span class="sxs-lookup"><span data-stu-id="059db-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="059db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="059db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="059db-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="059db-106">à Pointeur vers le `mdModule` jeton qui référence les métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="059db-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="059db-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="059db-107">Remarks</span></span>  
 <span data-ttu-id="059db-108">Le jeton peut être passé aux interfaces d’importation de métadonnées [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)et [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="059db-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059db-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="059db-109">Requirements</span></span>  
 <span data-ttu-id="059db-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="059db-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="059db-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="059db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="059db-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="059db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="059db-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="059db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059db-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="059db-114">See also</span></span>

- [<span data-ttu-id="059db-115">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="059db-115">Metadata</span></span>](../metadata/index.md)
