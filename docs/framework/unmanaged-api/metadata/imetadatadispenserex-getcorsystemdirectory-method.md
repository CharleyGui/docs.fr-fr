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
ms.openlocfilehash: a76c17e663fdf6555ed878cca1b86b6a9395730e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008792"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="866ab-102">IMetaDataDispenserEx::GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="866ab-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="866ab-103">Obtient le répertoire qui contient le common language runtime actuel (CLR).</span><span class="sxs-lookup"><span data-stu-id="866ab-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="866ab-104">Cette méthode est prise en charge uniquement par les débogueurs hors processus.</span><span class="sxs-lookup"><span data-stu-id="866ab-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="866ab-105">Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="866ab-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="866ab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="866ab-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="866ab-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="866ab-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="866ab-108">à Mémoire tampon pour recevoir le nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="866ab-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="866ab-109">dans Taille, en octets, de `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="866ab-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="866ab-110">à Nombre d’octets réellement retournés dans `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="866ab-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="866ab-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="866ab-111">Requirements</span></span>  
 <span data-ttu-id="866ab-112">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="866ab-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="866ab-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="866ab-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="866ab-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="866ab-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="866ab-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="866ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866ab-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="866ab-116">See also</span></span>

- [<span data-ttu-id="866ab-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="866ab-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="866ab-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="866ab-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
