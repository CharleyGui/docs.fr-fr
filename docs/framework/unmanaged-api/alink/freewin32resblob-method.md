---
title: FreeWin32ResBlob, méthode
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 75aec187452e2f9f442a5d4856fe6777c03f34c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741978"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="1909c-102">FreeWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="1909c-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="1909c-103">Libère le blob de ressources Win32 et les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="1909c-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1909c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1909c-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1909c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1909c-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="1909c-106">Le blob de ressources à libérer.</span><span class="sxs-lookup"><span data-stu-id="1909c-106">The resource blob to be released.</span></span> <span data-ttu-id="1909c-107">Cette méthode attribue le pointeur d’objet blob avec la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="1909c-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1909c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1909c-108">Return Value</span></span>  
 <span data-ttu-id="1909c-109">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="1909c-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1909c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1909c-110">Requirements</span></span>  
 <span data-ttu-id="1909c-111">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="1909c-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1909c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1909c-112">See also</span></span>

- [<span data-ttu-id="1909c-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="1909c-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1909c-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="1909c-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1909c-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="1909c-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
