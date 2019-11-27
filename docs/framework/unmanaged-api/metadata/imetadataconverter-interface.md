---
title: IMetaDataConverter, interface
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: b771b368c069a4577d266b47bfb4a5ee1935e48e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436271"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="8f415-102">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="8f415-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="8f415-103">Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="8f415-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f415-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8f415-104">Methods</span></span>  
  
|<span data-ttu-id="8f415-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8f415-105">Method</span></span>|<span data-ttu-id="8f415-106">Description</span><span class="sxs-lookup"><span data-stu-id="8f415-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f415-107">GetMetaDataFromTypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="8f415-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="8f415-108">Obtient un pointeur vers une instance [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la signature de métadonnées pour la bibliothèque de types référencée par l’instance de `ITypeInfo` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8f415-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="8f415-109">GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="8f415-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="8f415-110">Obtient un pointeur vers une instance de `IMetaDataImport` qui représente la signature de métadonnées pour la bibliothèque de types représentée par l’instance de `ITypeLib` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8f415-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="8f415-111">GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="8f415-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="8f415-112">Obtient un pointeur vers une instance de `ITypeLib` qui représente la bibliothèque de types qui contient le module et les noms de bibliothèque spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8f415-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f415-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f415-113">Requirements</span></span>  
 <span data-ttu-id="8f415-114">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f415-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f415-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8f415-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f415-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f415-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f415-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f415-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f415-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f415-118">See also</span></span>

- [<span data-ttu-id="8f415-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8f415-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="8f415-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8f415-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
