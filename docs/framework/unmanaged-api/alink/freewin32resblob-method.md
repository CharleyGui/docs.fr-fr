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
ms.openlocfilehash: 44c5228f7ee467abd02a9ec09590d0352fc82036
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684757"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="d1985-102">FreeWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="d1985-102">FreeWin32ResBlob Method</span></span>

<span data-ttu-id="d1985-103">Libère l’objet blob de ressources Win32 et les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="d1985-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1985-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1985-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1985-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1985-105">Parameters</span></span>  

 `ppResBlob`  
 <span data-ttu-id="d1985-106">Objet blob de ressources à libérer.</span><span class="sxs-lookup"><span data-stu-id="d1985-106">The resource blob to be released.</span></span> <span data-ttu-id="d1985-107">Cette méthode affecte le pointeur d’objet blob à NULL.</span><span class="sxs-lookup"><span data-stu-id="d1985-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1985-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d1985-108">Return Value</span></span>  

 <span data-ttu-id="d1985-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="d1985-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1985-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1985-110">Requirements</span></span>  

 <span data-ttu-id="d1985-111">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="d1985-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1985-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1985-112">See also</span></span>

- [<span data-ttu-id="d1985-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d1985-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d1985-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d1985-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d1985-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="d1985-115">ALink API</span></span>](index.md)
