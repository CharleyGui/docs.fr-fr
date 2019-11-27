---
title: EmitAssemblyCustomAttribute, méthode
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446507"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="a1790-102">EmitAssemblyCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="a1790-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="a1790-103">Appelez pour définir des attributs personnalisés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a1790-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1790-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1790-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1790-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1790-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a1790-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a1790-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a1790-107">Fichier qui défile l’attribut.</span><span class="sxs-lookup"><span data-stu-id="a1790-107">File that defiles the attribute.</span></span> <span data-ttu-id="a1790-108">Peut avoir la valeur NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="a1790-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="a1790-109">Type de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a1790-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="a1790-110">Données de valeur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a1790-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="a1790-111">Longueur des données de la valeur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a1790-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="a1790-112">TRUE si l’attribut personnalisé est lié à la signature de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a1790-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="a1790-113">TRUE si plusieurs attributs doivent être émis.</span><span class="sxs-lookup"><span data-stu-id="a1790-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1790-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1790-114">Return Value</span></span>  
 <span data-ttu-id="a1790-115">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="a1790-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1790-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1790-116">Requirements</span></span>  
 <span data-ttu-id="a1790-117">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="a1790-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1790-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1790-118">See also</span></span>

- [<span data-ttu-id="a1790-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="a1790-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a1790-120">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="a1790-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a1790-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="a1790-121">ALink API</span></span>](index.md)
