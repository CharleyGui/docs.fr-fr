---
title: ICLRMetadataLocator::GetMetadata, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: ad309290319396ff4e74e30d572effeffe802d1d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859877"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="251dc-102">ICLRMetadataLocator::GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="251dc-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="251dc-103">Appelée par les services d’accès aux données common language runtime (CLR) pour récupérer les métadonnées d’une image.</span><span class="sxs-lookup"><span data-stu-id="251dc-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="251dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="251dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="251dc-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="251dc-106">dans Chaîne qui spécifie le chemin d’accès du fichier image.</span><span class="sxs-lookup"><span data-stu-id="251dc-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="251dc-107">dans Horodatage du fichier image.</span><span class="sxs-lookup"><span data-stu-id="251dc-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="251dc-108">dans Taille du fichier image.</span><span class="sxs-lookup"><span data-stu-id="251dc-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="251dc-109">dans Identificateur global unique de l’image.</span><span class="sxs-lookup"><span data-stu-id="251dc-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="251dc-110">dans Adresse virtuelle relative (RVA) des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="251dc-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="251dc-111">L’adresse est relative à l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="251dc-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="251dc-112">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="251dc-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="251dc-113">dans Taille de la mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="251dc-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="251dc-114">à Mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="251dc-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="251dc-115">à Taille des métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="251dc-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="251dc-116">Notes </span><span class="sxs-lookup"><span data-stu-id="251dc-116">Remarks</span></span>  
 <span data-ttu-id="251dc-117">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="251dc-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251dc-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="251dc-118">Requirements</span></span>  
 <span data-ttu-id="251dc-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251dc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251dc-120">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="251dc-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="251dc-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="251dc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="251dc-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251dc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="251dc-123">See also</span></span>

- [<span data-ttu-id="251dc-124">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="251dc-124">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
