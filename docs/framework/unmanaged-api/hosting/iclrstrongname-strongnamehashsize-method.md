---
title: Méthode ICLRStrongName::StrongNameHashSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: abcae4a89dc2ee3895d6ff246fa7358a5fe2f06e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901112"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="53bd7-102">Méthode ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="53bd7-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="53bd7-103">Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="53bd7-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53bd7-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53bd7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="53bd7-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="53bd7-106">dans Algorithme de hachage utilisé pour calculer la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="53bd7-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="53bd7-107">à Taille de la mémoire tampon retournée, en octets.</span><span class="sxs-lookup"><span data-stu-id="53bd7-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53bd7-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="53bd7-108">Return Value</span></span>  
 <span data-ttu-id="53bd7-109">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="53bd7-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bd7-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="53bd7-110">Requirements</span></span>  
 <span data-ttu-id="53bd7-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53bd7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bd7-112">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="53bd7-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53bd7-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53bd7-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53bd7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bd7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53bd7-115">See also</span></span>

- [<span data-ttu-id="53bd7-116">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="53bd7-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
