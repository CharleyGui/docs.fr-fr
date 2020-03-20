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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179391"
---
# <a name="setpekind-method"></a><span data-ttu-id="1f8da-102">SetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="1f8da-102">SetPEKind Method</span></span>
<span data-ttu-id="1f8da-103">Détermine le type portable exécutable, spécifique à la machine ou agnostique à la machine.</span><span class="sxs-lookup"><span data-stu-id="1f8da-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f8da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f8da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="1f8da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f8da-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1f8da-106">ID de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="1f8da-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1f8da-107">Jeton de fichier pour lequel le type PE doit être défini.</span><span class="sxs-lookup"><span data-stu-id="1f8da-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="1f8da-108">Peut être `AssemblyID` NULL si n’indique pas un netmodule non lié.</span><span class="sxs-lookup"><span data-stu-id="1f8da-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="1f8da-109">Le type de PE, comme indiqué par le [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1f8da-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="1f8da-110">L’architecture de la machine cible, comme indiqué dans l’en-tête NT.</span><span class="sxs-lookup"><span data-stu-id="1f8da-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f8da-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1f8da-111">Return Value</span></span>  
 <span data-ttu-id="1f8da-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="1f8da-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f8da-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1f8da-113">Requirements</span></span>  
 <span data-ttu-id="1f8da-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="1f8da-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8da-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f8da-115">See also</span></span>

- [<span data-ttu-id="1f8da-116">GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="1f8da-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="1f8da-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="1f8da-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1f8da-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="1f8da-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1f8da-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="1f8da-119">ALink API</span></span>](index.md)
