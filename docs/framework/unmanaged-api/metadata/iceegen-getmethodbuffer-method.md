---
title: ICeeGen::GetMethodBuffer, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14ea8dab2c4258fe490ef362fd527d80bd8a0178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746107"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="0187a-102">ICeeGen::GetMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="0187a-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="0187a-103">Obtient une mémoire tampon de la taille appropriée pour la méthode à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0187a-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0187a-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="0187a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0187a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0187a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0187a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0187a-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="0187a-107">[in] L’adresse virtuelle relative de la méthode pour laquelle retourner une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="0187a-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0187a-108">[out] Pointeur vers la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="0187a-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0187a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0187a-109">Requirements</span></span>  
 <span data-ttu-id="0187a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0187a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0187a-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0187a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0187a-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0187a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0187a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0187a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0187a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0187a-114">See also</span></span>

- [<span data-ttu-id="0187a-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="0187a-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
