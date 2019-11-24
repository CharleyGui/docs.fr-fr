---
title: IMetaDataAssemblyImport::GetAssemblyFromScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: 953aa16566c2a15939fbd556f478bbdb3c0c77d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448239"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="bf3f7-102">IMetaDataAssemblyImport::GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="bf3f7-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="bf3f7-103">Gets a pointer to the assembly in the current scope.</span><span class="sxs-lookup"><span data-stu-id="bf3f7-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf3f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf3f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf3f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf3f7-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="bf3f7-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span><span class="sxs-lookup"><span data-stu-id="bf3f7-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf3f7-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="bf3f7-107">Requirements</span></span>  
 <span data-ttu-id="bf3f7-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf3f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf3f7-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf3f7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf3f7-110">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf3f7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf3f7-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3f7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf3f7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf3f7-112">See also</span></span>

- [<span data-ttu-id="bf3f7-113">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="bf3f7-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
