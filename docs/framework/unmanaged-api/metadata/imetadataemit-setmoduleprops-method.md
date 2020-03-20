---
title: IMetaDataEmit::SetModuleProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 69c3ee366dbb8505e0df744037c480da996bb836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175614"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="04e76-102">IMetaDataEmit::SetModuleProps, méthode</span><span class="sxs-lookup"><span data-stu-id="04e76-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="04e76-103">Mise à jour des références à un module défini par un appel antérieur à [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="04e76-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e76-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04e76-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="04e76-106">[dans] Le nom du module dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="04e76-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="04e76-107">C’est le nom de fichier seulement et pas le nom complet de chemin.</span><span class="sxs-lookup"><span data-stu-id="04e76-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e76-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04e76-108">Requirements</span></span>  
 <span data-ttu-id="04e76-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e76-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e76-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="04e76-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e76-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04e76-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04e76-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e76-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e76-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04e76-113">See also</span></span>

- [<span data-ttu-id="04e76-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="04e76-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="04e76-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="04e76-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
