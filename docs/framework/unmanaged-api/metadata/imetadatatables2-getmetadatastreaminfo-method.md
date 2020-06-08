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
ms.openlocfilehash: 7d39d089c348b7320651ed21ea14ba07d7877fd4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501093"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="7b743-102">IMetaDataTables2::GetMetaDataStreamInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="7b743-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="7b743-103">Obtient le nom, la taille et le contenu du flux de métadonnées au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="7b743-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b743-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b743-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b743-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7b743-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="7b743-106">dans Index du flux de métadonnées demandé.</span><span class="sxs-lookup"><span data-stu-id="7b743-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="7b743-107">à Pointeur vers le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="7b743-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="7b743-108">à Pointeur vers le flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7b743-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="7b743-109">à Taille, en octets, de `ppv` .</span><span class="sxs-lookup"><span data-stu-id="7b743-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b743-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7b743-110">Requirements</span></span>  
 <span data-ttu-id="7b743-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b743-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b743-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7b743-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b743-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b743-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b743-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b743-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b743-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b743-115">See also</span></span>

- [<span data-ttu-id="7b743-116">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="7b743-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="7b743-117">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="7b743-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
