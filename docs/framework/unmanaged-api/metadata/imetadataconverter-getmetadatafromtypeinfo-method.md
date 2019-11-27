---
title: IMetaDataConverter::GetMetaDataFromTypeInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: df7be11e8f275824fca658a9604178e7cf28e3ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436292"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="f0bb1-102">IMetaDataConverter::GetMetaDataFromTypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f0bb1-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="f0bb1-103">Obtient un pointeur vers une instance [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types référencée par l’instance de `ITypeInfo` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0bb1-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0bb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0bb1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0bb1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0bb1-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="f0bb1-106">dans Pointeur vers un objet `ITypeInfo` qui fait référence à la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="f0bb1-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="f0bb1-107">à Pointeur vers un emplacement qui reçoit l’adresse de l’instance de `IMetaDataImport` qui représente la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f0bb1-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0bb1-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0bb1-108">Requirements</span></span>  
 <span data-ttu-id="f0bb1-109">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0bb1-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0bb1-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f0bb1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0bb1-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0bb1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0bb1-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0bb1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bb1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0bb1-113">See also</span></span>

- [<span data-ttu-id="f0bb1-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f0bb1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f0bb1-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f0bb1-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
