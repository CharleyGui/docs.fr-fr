---
title: IMetaDataAssemblyEmit::SetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177852"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="4cf89-102">IMetaDataAssemblyEmit::SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4cf89-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="4cf89-103">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4cf89-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cf89-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf89-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4cf89-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="4cf89-106">[dans] Le jeton des métadonnées `ExportedType` qui spécifie la structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="4cf89-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="4cf89-107">[dans] Le jeton, `File`de `AssemblyRef`type `ExportedType`, , ou , qui spécifie comment ce type est mis en œuvre.</span><span class="sxs-lookup"><span data-stu-id="4cf89-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="4cf89-108">[dans] Le `TypeDef` jeton référencé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="4cf89-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="4cf89-109">[dans] Une combinaison de valeurs qui spécifient les attributs du type.</span><span class="sxs-lookup"><span data-stu-id="4cf89-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cf89-110">Notes </span><span class="sxs-lookup"><span data-stu-id="4cf89-110">Remarks</span></span>  
 <span data-ttu-id="4cf89-111">Pour créer `ExportedType` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineExportedType.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)</span><span class="sxs-lookup"><span data-stu-id="4cf89-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf89-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4cf89-112">Requirements</span></span>  
 <span data-ttu-id="4cf89-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cf89-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cf89-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4cf89-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cf89-115">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cf89-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4cf89-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cf89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf89-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cf89-117">See also</span></span>

- [<span data-ttu-id="4cf89-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4cf89-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
