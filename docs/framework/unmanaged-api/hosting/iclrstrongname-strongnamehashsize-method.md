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
ms.openlocfilehash: 6ee87fdbf75d4a07a7337a1c9fdc58a06191b992
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674813"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="f69d2-102">Méthode ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="f69d2-102">ICLRStrongName::StrongNameHashSize Method</span></span>

<span data-ttu-id="f69d2-103">Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="f69d2-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f69d2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f69d2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f69d2-105">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="f69d2-106">dans Algorithme de hachage utilisé pour calculer la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f69d2-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="f69d2-107">à Taille de la mémoire tampon retournée, en octets.</span><span class="sxs-lookup"><span data-stu-id="f69d2-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f69d2-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f69d2-108">Return Value</span></span>  

 <span data-ttu-id="f69d2-109">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="f69d2-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f69d2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f69d2-110">Requirements</span></span>  

 <span data-ttu-id="f69d2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f69d2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f69d2-112">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="f69d2-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f69d2-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f69d2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f69d2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f69d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69d2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f69d2-115">See also</span></span>

- [<span data-ttu-id="f69d2-116">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="f69d2-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
