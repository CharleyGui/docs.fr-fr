---
title: CloseAssembly, méthode
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7828c86018724bb934de99cab4617f9885fdca6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787605"
---
# <a name="closeassembly-method"></a><span data-ttu-id="6767f-102">CloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="6767f-102">CloseAssembly Method</span></span>
<span data-ttu-id="6767f-103">Finalise les opérations d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6767f-103">Finalizes assembly operations.</span></span> <span data-ttu-id="6767f-104">Appelez cette méthode avant de commencer un nouvel assembly ou un module indépendant.</span><span class="sxs-lookup"><span data-stu-id="6767f-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6767f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6767f-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6767f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6767f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6767f-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6767f-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6767f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6767f-108">Return Value</span></span>  
 <span data-ttu-id="6767f-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="6767f-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6767f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6767f-110">Requirements</span></span>  
 <span data-ttu-id="6767f-111">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="6767f-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6767f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6767f-112">See also</span></span>

- [<span data-ttu-id="6767f-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="6767f-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6767f-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="6767f-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6767f-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="6767f-115">ALink API</span></span>](index.md)
