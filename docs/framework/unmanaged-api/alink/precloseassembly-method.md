---
title: PreCloseAssembly, méthode
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: fcfd3e79bbb52837a333b5ffacf5c13ae60f2490
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445613"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="b789a-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="b789a-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="b789a-103">Closes the assembly file.</span><span class="sxs-lookup"><span data-stu-id="b789a-103">Closes the assembly file.</span></span> <span data-ttu-id="b789a-104">Call this method after closing all other files, but before closing the assembly file.</span><span class="sxs-lookup"><span data-stu-id="b789a-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="b789a-105">Do not call this method for unbound modules.</span><span class="sxs-lookup"><span data-stu-id="b789a-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b789a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b789a-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b789a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b789a-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b789a-108">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="b789a-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b789a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b789a-109">Return Value</span></span>  
 <span data-ttu-id="b789a-110">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="b789a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b789a-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="b789a-111">Requirements</span></span>  
 <span data-ttu-id="b789a-112">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="b789a-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b789a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b789a-113">See also</span></span>

- [<span data-ttu-id="b789a-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b789a-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b789a-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b789a-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b789a-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="b789a-116">ALink API</span></span>](index.md)
