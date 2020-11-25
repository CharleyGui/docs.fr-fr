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
ms.openlocfilehash: ed0902824bdbb4d057bf5a7920db4b1d18eb7347
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714664"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="d4822-102">IMetaDataConverter::GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="d4822-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="d4822-103">Obtient un pointeur d’interface vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types représentée par l' `ITypeLib` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d4822-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4822-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4822-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4822-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4822-105">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="d4822-106">dans Pointeur vers un `ITypeLib` objet qui représente la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="d4822-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="d4822-107">à Pointeur vers un emplacement qui reçoit l’adresse de l' `IMetaDataImport` instance qui représente la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d4822-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4822-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d4822-108">Requirements</span></span>  

 <span data-ttu-id="d4822-109">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4822-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4822-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4822-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4822-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4822-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4822-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4822-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4822-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4822-113">See also</span></span>

- [<span data-ttu-id="d4822-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d4822-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d4822-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d4822-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
