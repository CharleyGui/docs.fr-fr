---
title: IMetaDataImport::GetPinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1be6079ed382b8ab27d0aec16bd725f5c5b9cb5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778904"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="0ec4f-102">IMetaDataImport::GetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="0ec4f-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="0ec4f-103">Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ec4f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ec4f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0ec4f-106">[in] Jeton FieldDef ou MethodDef pour obtenir les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="0ec4f-107">[out] Pointeur vers les indicateurs utilisés pour le mappage.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="0ec4f-108">Cette valeur est un masque de bits à partir de la [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="0ec4f-109">[out] Le nom de la DLL cible non managée.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="0ec4f-110">[in] La taille en caractères larges de `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="0ec4f-111">[out] Le nombre de caractères étendus retournés dans `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="0ec4f-112">[out] Pointeur vers un jeton ModuleRef qui représente la bibliothèque d’objets cible non managée.</span><span class="sxs-lookup"><span data-stu-id="0ec4f-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec4f-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0ec4f-113">Requirements</span></span>  
 <span data-ttu-id="0ec4f-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec4f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec4f-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ec4f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ec4f-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ec4f-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ec4f-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec4f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec4f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ec4f-118">See also</span></span>

- [<span data-ttu-id="0ec4f-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0ec4f-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0ec4f-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0ec4f-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
