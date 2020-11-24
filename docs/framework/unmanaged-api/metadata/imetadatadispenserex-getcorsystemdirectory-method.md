---
title: IMetaDataDispenserEx::GetCORSystemDirectory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: ea0e6f96028afc201f498119976eb87aa762a6eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681689"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="c905a-102">IMetaDataDispenserEx::GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="c905a-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="c905a-103">Obtient le répertoire qui contient le common language runtime actuel (CLR).</span><span class="sxs-lookup"><span data-stu-id="c905a-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="c905a-104">Cette méthode est prise en charge uniquement par les débogueurs hors processus.</span><span class="sxs-lookup"><span data-stu-id="c905a-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="c905a-105">Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c905a-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c905a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c905a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c905a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c905a-107">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="c905a-108">à Mémoire tampon pour recevoir le nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="c905a-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c905a-109">dans Taille, en octets, de `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="c905a-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="c905a-110">à Nombre d’octets réellement retournés dans `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="c905a-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c905a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c905a-111">Requirements</span></span>  

 <span data-ttu-id="c905a-112">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c905a-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c905a-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c905a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c905a-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c905a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c905a-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c905a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c905a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c905a-116">See also</span></span>

- [<span data-ttu-id="c905a-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="c905a-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="c905a-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="c905a-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
