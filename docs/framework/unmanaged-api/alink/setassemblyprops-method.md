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
ms.openlocfilehash: 4b0de5f9759491f1303edc978b1548e91214daf8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733748"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="feabc-102">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="feabc-102">SetAssemblyProps Method</span></span>

<span data-ttu-id="feabc-103">Affecte des propriétés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="feabc-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feabc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feabc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="feabc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="feabc-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="feabc-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="feabc-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="feabc-107">Fichier qui définit la propriété.</span><span class="sxs-lookup"><span data-stu-id="feabc-107">File that defines the property.</span></span> <span data-ttu-id="feabc-108">Peut avoir la valeur NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="feabc-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="feabc-109">Indique l’option à modifier.</span><span class="sxs-lookup"><span data-stu-id="feabc-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="feabc-110">Nouvelle valeur de l’option.</span><span class="sxs-lookup"><span data-stu-id="feabc-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feabc-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="feabc-111">Return Value</span></span>  

 <span data-ttu-id="feabc-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="feabc-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feabc-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="feabc-113">Requirements</span></span>  

 <span data-ttu-id="feabc-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="feabc-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feabc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feabc-115">See also</span></span>

- [<span data-ttu-id="feabc-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="feabc-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="feabc-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="feabc-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="feabc-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="feabc-118">ALink API</span></span>](index.md)
