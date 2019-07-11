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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c4e39fdbb400475d1b14639114325309ddb7597
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751031"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="93611-102">IMetaDataEmit::SetModuleProps, méthode</span><span class="sxs-lookup"><span data-stu-id="93611-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="93611-103">Met à jour les références à un module défini par un appel antérieur à [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="93611-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93611-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93611-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93611-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93611-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="93611-106">[in] Le nom du module au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="93611-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="93611-107">C’est le nom de fichier uniquement et pas le nom de chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="93611-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93611-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93611-108">Requirements</span></span>  
 <span data-ttu-id="93611-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93611-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93611-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="93611-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93611-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93611-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93611-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93611-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93611-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93611-113">See also</span></span>

- [<span data-ttu-id="93611-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="93611-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="93611-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="93611-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
