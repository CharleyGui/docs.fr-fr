---
title: SetPEKind, méthode
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787192"
---
# <a name="setpekind-method"></a><span data-ttu-id="12922-102">SetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="12922-102">SetPEKind Method</span></span>
<span data-ttu-id="12922-103">Détermine le type d’exécutable portable, propre à l’ordinateur ou indépendant de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12922-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12922-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12922-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="12922-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12922-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="12922-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="12922-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="12922-107">Jeton du fichier pour lequel le type PE doit être défini.</span><span class="sxs-lookup"><span data-stu-id="12922-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="12922-108">Peut avoir la valeur `AssemblyID` null si n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="12922-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="12922-109">Type de PE, comme indiqué par l' [énumération CorPEKind,](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="12922-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="12922-110">Architecture de l’ordinateur cible, comme indiqué dans l’en-tête NT.</span><span class="sxs-lookup"><span data-stu-id="12922-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12922-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="12922-111">Return Value</span></span>  
 <span data-ttu-id="12922-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="12922-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12922-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12922-113">Requirements</span></span>  
 <span data-ttu-id="12922-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="12922-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12922-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12922-115">See also</span></span>

- [<span data-ttu-id="12922-116">GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="12922-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="12922-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="12922-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="12922-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="12922-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="12922-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="12922-119">ALink API</span></span>](index.md)
