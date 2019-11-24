---
title: IMetaDataImport::GetParamForMethodIndex, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: a70691b9c519bc59ae7df7a86d5d6697db565575
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437167"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="2d72f-102">IMetaDataImport::GetParamForMethodIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="2d72f-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="2d72f-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="2d72f-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d72f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d72f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d72f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d72f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="2d72f-106">[in] A token that represents the method to return the parameter token for.</span><span class="sxs-lookup"><span data-stu-id="2d72f-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="2d72f-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span><span class="sxs-lookup"><span data-stu-id="2d72f-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="2d72f-108">Parameters are numbered starting from one, with the method's return value in position zero.</span><span class="sxs-lookup"><span data-stu-id="2d72f-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="2d72f-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span><span class="sxs-lookup"><span data-stu-id="2d72f-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d72f-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="2d72f-110">Requirements</span></span>  
 <span data-ttu-id="2d72f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d72f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d72f-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d72f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d72f-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d72f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d72f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d72f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d72f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d72f-115">See also</span></span>

- [<span data-ttu-id="2d72f-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2d72f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2d72f-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2d72f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
