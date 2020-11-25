---
title: IMetaDataImport::GetModuleRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: 606a3f2cfba05b014960842c5db77149f449193d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733124"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="001cc-102">IMetaDataImport::GetModuleRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="001cc-102">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="001cc-103">Obtient le nom du module référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="001cc-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="001cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="001cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="001cc-105">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="001cc-106">dans Jeton de métadonnées ModuleRef qui référence le module pour lequel obtenir les informations de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="001cc-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="001cc-107">à Mémoire tampon destinée à contenir le nom du module.</span><span class="sxs-lookup"><span data-stu-id="001cc-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="001cc-108">dans Taille demandée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="001cc-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="001cc-109">à Taille retournée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="001cc-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="001cc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="001cc-110">Requirements</span></span>  

 <span data-ttu-id="001cc-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="001cc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="001cc-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="001cc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="001cc-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="001cc-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="001cc-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="001cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001cc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="001cc-115">See also</span></span>

- [<span data-ttu-id="001cc-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="001cc-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="001cc-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="001cc-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
