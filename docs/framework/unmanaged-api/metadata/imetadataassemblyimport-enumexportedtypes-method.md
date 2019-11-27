---
title: IMetaDataAssemblyImport::EnumExportedTypes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: 45e2348b4726447548544d975e60b93e464fb402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450333"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="a9473-102">IMetaDataAssemblyImport::EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="a9473-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="a9473-103">Énumère les types exportés référencés dans le manifeste de l’assembly dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="a9473-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9473-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9473-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9473-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9473-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a9473-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a9473-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a9473-107">Il doit s’agir d’une valeur NULL lorsque la méthode `EnumExportedTypes` est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="a9473-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="a9473-108">à Énumération des jetons de métadonnées de `mdExportedType`.</span><span class="sxs-lookup"><span data-stu-id="a9473-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a9473-109">dans Nombre maximal de jetons de `mdExportedType` qui peuvent être placés dans le tableau de `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="a9473-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a9473-110">à Nombre de jetons de `mdExportedType` placés en `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="a9473-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9473-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a9473-111">Return Value</span></span>  
  
|<span data-ttu-id="a9473-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9473-112">HRESULT</span></span>|<span data-ttu-id="a9473-113">Description</span><span class="sxs-lookup"><span data-stu-id="a9473-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a9473-114">`EnumExportedTypes` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a9473-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a9473-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a9473-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a9473-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="a9473-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9473-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a9473-117">Requirements</span></span>  
 <span data-ttu-id="a9473-118">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9473-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9473-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a9473-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9473-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9473-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9473-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9473-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9473-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9473-122">See also</span></span>

- [<span data-ttu-id="a9473-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="a9473-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
