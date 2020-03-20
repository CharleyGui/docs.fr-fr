---
title: IMetaDataEmit::DefineModuleRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: 94261b7796166cf482a7de990551890e4722dd3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177737"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="41ee8-102">IMetaDataEmit::DefineModuleRef, méthode</span><span class="sxs-lookup"><span data-stu-id="41ee8-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="41ee8-103">Crée la signature des métadonnées pour un module avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="41ee8-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ee8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41ee8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ee8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41ee8-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="41ee8-106">[dans] Le nom de l’autre fichier de métadonnées, généralement un DLL.</span><span class="sxs-lookup"><span data-stu-id="41ee8-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="41ee8-107">C’est le nom du fichier seulement.</span><span class="sxs-lookup"><span data-stu-id="41ee8-107">This is the file name only.</span></span> <span data-ttu-id="41ee8-108">N’utilisez pas un nom de chemin complet.</span><span class="sxs-lookup"><span data-stu-id="41ee8-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="41ee8-109">[out] Le `mdModuleRef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="41ee8-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ee8-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="41ee8-110">Requirements</span></span>  
 <span data-ttu-id="41ee8-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ee8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ee8-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="41ee8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41ee8-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41ee8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41ee8-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ee8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ee8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41ee8-115">See also</span></span>

- [<span data-ttu-id="41ee8-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="41ee8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="41ee8-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="41ee8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
