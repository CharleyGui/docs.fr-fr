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
ms.openlocfilehash: 8f8c0c2cb8dea8ad2b9c0040654122ef5942aca0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008389"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="4f978-102">IMetaDataConverter::GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="4f978-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="4f978-103">Obtient un pointeur d’interface vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types représentée par l' `ITypeLib` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4f978-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f978-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f978-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f978-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f978-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="4f978-106">dans Pointeur vers un `ITypeLib` objet qui représente la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="4f978-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="4f978-107">à Pointeur vers un emplacement qui reçoit l’adresse de l' `IMetaDataImport` instance qui représente la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4f978-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f978-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f978-108">Requirements</span></span>  
 <span data-ttu-id="4f978-109">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f978-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f978-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f978-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f978-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f978-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f978-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f978-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f978-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f978-113">See also</span></span>

- [<span data-ttu-id="4f978-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4f978-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4f978-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4f978-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
