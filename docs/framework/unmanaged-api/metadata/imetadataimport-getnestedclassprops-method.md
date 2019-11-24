---
title: IMetaDataImport::GetNestedClassProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 0adf4f91e1bc7bfb72f634cb3bf038710198b74f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437141"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="3fa58-102">IMetaDataImport::GetNestedClassProps, méthode</span><span class="sxs-lookup"><span data-stu-id="3fa58-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="3fa58-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span><span class="sxs-lookup"><span data-stu-id="3fa58-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fa58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fa58-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fa58-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="3fa58-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span><span class="sxs-lookup"><span data-stu-id="3fa58-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="3fa58-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span><span class="sxs-lookup"><span data-stu-id="3fa58-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa58-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="3fa58-108">Requirements</span></span>  
 <span data-ttu-id="3fa58-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fa58-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fa58-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3fa58-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fa58-111">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fa58-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fa58-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fa58-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa58-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fa58-113">See also</span></span>

- [<span data-ttu-id="3fa58-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3fa58-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3fa58-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="3fa58-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
