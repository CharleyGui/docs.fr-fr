---
title: IMetaDataDispenser, interface
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: c798aeba46adf91a8c13f8143c00f02173a0bb52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726104"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="d02f1-102">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="d02f1-102">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="d02f1-103">Fournit des méthodes pour créer une portée de métadonnées ou en ouvrir une existante.</span><span class="sxs-lookup"><span data-stu-id="d02f1-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d02f1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d02f1-104">Methods</span></span>  
  
|<span data-ttu-id="d02f1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d02f1-105">Method</span></span>|<span data-ttu-id="d02f1-106">Description</span><span class="sxs-lookup"><span data-stu-id="d02f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d02f1-107">DefineScope, méthode</span><span class="sxs-lookup"><span data-stu-id="d02f1-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="d02f1-108">Crée une zone en mémoire dans laquelle vous pouvez créer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d02f1-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="d02f1-109">OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="d02f1-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="d02f1-110">Ouvre un fichier sur disque existant et mappe ses métadonnées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d02f1-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="d02f1-111">OpenScopeOnMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="d02f1-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="d02f1-112">Ouvre une zone de mémoire qui contient des métadonnées existantes.</span><span class="sxs-lookup"><span data-stu-id="d02f1-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="d02f1-113">Autrement dit, cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d02f1-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d02f1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d02f1-114">Requirements</span></span>  

 <span data-ttu-id="d02f1-115">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d02f1-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d02f1-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d02f1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d02f1-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d02f1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d02f1-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d02f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02f1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d02f1-119">See also</span></span>

- [<span data-ttu-id="d02f1-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="d02f1-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="d02f1-121">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="d02f1-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
