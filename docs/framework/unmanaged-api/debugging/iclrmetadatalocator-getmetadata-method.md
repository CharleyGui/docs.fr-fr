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
ms.openlocfilehash: 66b3934d000b4f000c368acb1f57c8fc82a5c453
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793625"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="f908c-102">ICLRMetadataLocator::GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="f908c-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="f908c-103">Appelée par les services d’accès aux données common language runtime (CLR) pour récupérer les métadonnées d’une image.</span><span class="sxs-lookup"><span data-stu-id="f908c-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f908c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f908c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f908c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f908c-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="f908c-106">dans Chaîne qui spécifie le chemin d’accès du fichier image.</span><span class="sxs-lookup"><span data-stu-id="f908c-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="f908c-107">dans Horodatage du fichier image.</span><span class="sxs-lookup"><span data-stu-id="f908c-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="f908c-108">dans Taille du fichier image.</span><span class="sxs-lookup"><span data-stu-id="f908c-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="f908c-109">dans Identificateur global unique de l’image.</span><span class="sxs-lookup"><span data-stu-id="f908c-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="f908c-110">dans Adresse virtuelle relative (RVA) des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f908c-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="f908c-111">L’adresse est relative à l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="f908c-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="f908c-112">dans Réservé pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f908c-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="f908c-113">dans Taille de la mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f908c-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f908c-114">à Mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f908c-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="f908c-115">à Taille des métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="f908c-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f908c-116">Notes</span><span class="sxs-lookup"><span data-stu-id="f908c-116">Remarks</span></span>  
 <span data-ttu-id="f908c-117">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="f908c-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f908c-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f908c-118">Requirements</span></span>  
 <span data-ttu-id="f908c-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f908c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f908c-120">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f908c-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f908c-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f908c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f908c-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f908c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f908c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f908c-123">See also</span></span>

- [<span data-ttu-id="f908c-124">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="f908c-124">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
