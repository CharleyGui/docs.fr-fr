---
title: IMetaDataAssemblyEmit::SetFileProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176030"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="4725a-102">IMetaDataAssemblyEmit::SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4725a-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="4725a-103">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4725a-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4725a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4725a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4725a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4725a-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="4725a-106">[dans] Le jeton des métadonnées `File` qui spécifie la structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="4725a-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4725a-107">[dans] Un pointeur vers les données de hachage associées au fichier.</span><span class="sxs-lookup"><span data-stu-id="4725a-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4725a-108">[dans] La taille dans `pbHashValue`les octets de .</span><span class="sxs-lookup"><span data-stu-id="4725a-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="4725a-109">[dans] Une combinaison bitwise de valeurs [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) qui spécifient différents attributs du fichier.</span><span class="sxs-lookup"><span data-stu-id="4725a-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4725a-110">Notes </span><span class="sxs-lookup"><span data-stu-id="4725a-110">Remarks</span></span>  
 <span data-ttu-id="4725a-111">Pour créer `File` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)</span><span class="sxs-lookup"><span data-stu-id="4725a-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4725a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4725a-112">Requirements</span></span>  
 <span data-ttu-id="4725a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4725a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4725a-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4725a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4725a-115">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4725a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4725a-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4725a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4725a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4725a-117">See also</span></span>

- [<span data-ttu-id="4725a-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4725a-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
