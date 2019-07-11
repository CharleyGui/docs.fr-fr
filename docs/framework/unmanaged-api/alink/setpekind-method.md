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
ms.openlocfilehash: 8fc581904351443f4368a68a653fd39b3548999a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741417"
---
# <a name="setpekind-method"></a><span data-ttu-id="56f2a-102">SetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="56f2a-102">SetPEKind Method</span></span>
<span data-ttu-id="56f2a-103">Détermine le type de fichier exécutable portable, spécifiques à l’ordinateur ou indépendant de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56f2a-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f2a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="56f2a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56f2a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="56f2a-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="56f2a-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="56f2a-107">Jeton du fichier pour lequel le type PE doit être défini.</span><span class="sxs-lookup"><span data-stu-id="56f2a-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="56f2a-108">Peut être NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="56f2a-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="56f2a-109">Le type de PE, comme indiqué par le [CorPEKind, énumération](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="56f2a-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="56f2a-110">L’architecture d’ordinateur cible, comme indiqué dans l’en-tête NT.</span><span class="sxs-lookup"><span data-stu-id="56f2a-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56f2a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="56f2a-111">Return Value</span></span>  
 <span data-ttu-id="56f2a-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="56f2a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f2a-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56f2a-113">Requirements</span></span>  
 <span data-ttu-id="56f2a-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="56f2a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f2a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56f2a-115">See also</span></span>

- [<span data-ttu-id="56f2a-116">GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="56f2a-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="56f2a-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="56f2a-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="56f2a-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="56f2a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="56f2a-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="56f2a-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
