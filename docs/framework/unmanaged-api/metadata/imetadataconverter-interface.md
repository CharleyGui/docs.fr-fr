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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008376"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="63d98-102">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="63d98-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="63d98-103">Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="63d98-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63d98-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="63d98-104">Methods</span></span>  
  
|<span data-ttu-id="63d98-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="63d98-105">Method</span></span>|<span data-ttu-id="63d98-106">Description</span><span class="sxs-lookup"><span data-stu-id="63d98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63d98-107">GetMetaDataFromTypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="63d98-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="63d98-108">Obtient un pointeur vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature de métadonnées pour la bibliothèque de types référencée par l' `ITypeInfo` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63d98-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="63d98-109">GetMetaDataFromTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="63d98-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="63d98-110">Obtient un pointeur vers une `IMetaDataImport` instance qui représente la signature de métadonnées pour la bibliothèque de types représentée par l' `ITypeLib` instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63d98-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="63d98-111">GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="63d98-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="63d98-112">Obtient un pointeur vers une `ITypeLib` instance de qui représente la bibliothèque de types qui contient les noms de module et de bibliothèque spécifiés.</span><span class="sxs-lookup"><span data-stu-id="63d98-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63d98-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63d98-113">Requirements</span></span>  
 <span data-ttu-id="63d98-114">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63d98-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d98-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="63d98-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63d98-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63d98-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63d98-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d98-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d98-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63d98-118">See also</span></span>

- [<span data-ttu-id="63d98-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="63d98-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="63d98-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="63d98-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
