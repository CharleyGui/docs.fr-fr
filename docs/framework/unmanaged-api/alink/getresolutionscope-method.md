---
title: GetResolutionScope, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2bfb43002b79fd3e499272b87756bdc3ab0b589
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787338"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="d789d-102">GetResolutionScope, méthode</span><span class="sxs-lookup"><span data-stu-id="d789d-102">GetResolutionScope Method</span></span>
<span data-ttu-id="d789d-103">Récupère la portée d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="d789d-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d789d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d789d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d789d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d789d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d789d-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d789d-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d789d-107">Fichier qui a besoin d’une référence.</span><span class="sxs-lookup"><span data-stu-id="d789d-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="d789d-108">Jeton du fichier dans lequel le type est défini dans, généralement récupéré à l’aide de la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d789d-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="d789d-109">Reçoit la référence de l’assembly ou du module.</span><span class="sxs-lookup"><span data-stu-id="d789d-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d789d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d789d-110">Return Value</span></span>  
 <span data-ttu-id="d789d-111">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="d789d-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d789d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d789d-112">Requirements</span></span>  
 <span data-ttu-id="d789d-113">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d789d-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d789d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d789d-114">See also</span></span>

- [<span data-ttu-id="d789d-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d789d-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d789d-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d789d-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d789d-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="d789d-117">ALink API</span></span>](index.md)
