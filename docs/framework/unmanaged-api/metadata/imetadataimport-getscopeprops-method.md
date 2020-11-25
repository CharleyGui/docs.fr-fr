---
title: IMetaDataImport::GetScopeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 5a89d1406daa9a2416a708b63d88fd9005234015
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729198"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="bd121-102">IMetaDataImport::GetScopeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bd121-102">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="bd121-103">Obtient le nom et éventuellement l'identificateur de version de l'assembly ou du module dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="bd121-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd121-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd121-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd121-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="bd121-106">à Mémoire tampon pour le nom de l’assembly ou du module.</span><span class="sxs-lookup"><span data-stu-id="bd121-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bd121-107">dans Taille en caractères larges de `szName` .</span><span class="sxs-lookup"><span data-stu-id="bd121-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bd121-108">à Nombre de caractères larges retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="bd121-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="bd121-109">[out, optional] Pointeur vers un GUID qui identifie de façon unique la version de l’assembly ou du module.</span><span class="sxs-lookup"><span data-stu-id="bd121-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd121-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bd121-110">Remarks</span></span>  

 <span data-ttu-id="bd121-111">La méthode [IMetaDataEmit :: SetModuleProps,](imetadataemit-setmoduleprops-method.md) est utilisée pour définir ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="bd121-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd121-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd121-112">Requirements</span></span>  

 <span data-ttu-id="bd121-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd121-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd121-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bd121-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd121-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd121-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd121-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd121-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd121-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd121-117">See also</span></span>

- [<span data-ttu-id="bd121-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="bd121-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bd121-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="bd121-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
