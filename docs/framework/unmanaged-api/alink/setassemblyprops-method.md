---
title: SetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776915"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="99147-102">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="99147-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="99147-103">Affecte des propriétés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="99147-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99147-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99147-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="99147-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99147-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="99147-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="99147-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="99147-107">Fichier qui définit la propriété.</span><span class="sxs-lookup"><span data-stu-id="99147-107">File that defines the property.</span></span> <span data-ttu-id="99147-108">Peut avoir la valeur `AssemblyID` null si n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="99147-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="99147-109">Indique l’option à modifier.</span><span class="sxs-lookup"><span data-stu-id="99147-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="99147-110">Nouvelle valeur de l’option.</span><span class="sxs-lookup"><span data-stu-id="99147-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99147-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="99147-111">Return Value</span></span>  
 <span data-ttu-id="99147-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="99147-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99147-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="99147-113">Requirements</span></span>  
 <span data-ttu-id="99147-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="99147-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99147-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99147-115">See also</span></span>

- [<span data-ttu-id="99147-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="99147-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="99147-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="99147-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="99147-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="99147-118">ALink API</span></span>](index.md)
