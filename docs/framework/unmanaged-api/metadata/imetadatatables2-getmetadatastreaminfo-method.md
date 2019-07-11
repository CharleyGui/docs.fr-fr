---
title: IMetaDataTables2::GetMetaDataStreamInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f559a269b48ceabfbe9c3a0cf3665458a2cf012
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769281"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="10628-102">IMetaDataTables2::GetMetaDataStreamInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="10628-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="10628-103">Obtient le nom, la taille et le contenu du flux de métadonnées à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="10628-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10628-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10628-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10628-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10628-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="10628-106">[in] L’index du flux de métadonnées demandées.</span><span class="sxs-lookup"><span data-stu-id="10628-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="10628-107">[out] Un pointeur vers le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="10628-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="10628-108">[out] Un pointeur vers le flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="10628-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="10628-109">[out] La taille, en octets, de `ppv`.</span><span class="sxs-lookup"><span data-stu-id="10628-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10628-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="10628-110">Requirements</span></span>  
 <span data-ttu-id="10628-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10628-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10628-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10628-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10628-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10628-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10628-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10628-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10628-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10628-115">See also</span></span>

- [<span data-ttu-id="10628-116">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="10628-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="10628-117">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="10628-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
