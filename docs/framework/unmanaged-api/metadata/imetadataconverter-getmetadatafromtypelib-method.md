---
title: IMetaDataConverter::GetMetaDataFromTypeLib, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436284"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="513ed-102">IMetaDataConverter::GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="513ed-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="513ed-103">Obtient un pointeur d’interface vers une instance [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types représentée par l’instance de `ITypeLib` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="513ed-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="513ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="513ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="513ed-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="513ed-106">dans Pointeur vers un objet `ITypeLib` qui représente la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="513ed-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="513ed-107">à Pointeur vers un emplacement qui reçoit l’adresse de l’instance de `IMetaDataImport` qui représente la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="513ed-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="513ed-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="513ed-108">Requirements</span></span>  
 <span data-ttu-id="513ed-109">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="513ed-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="513ed-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="513ed-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="513ed-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="513ed-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="513ed-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="513ed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513ed-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="513ed-113">See also</span></span>

- [<span data-ttu-id="513ed-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="513ed-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="513ed-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="513ed-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
