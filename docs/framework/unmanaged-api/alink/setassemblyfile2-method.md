---
title: SetAssemblyFile2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 131f5d951e524ef48f2cfe1e3e88ef80ac21c452
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703679"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="f4a9b-102">SetAssemblyFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="f4a9b-102">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="f4a9b-103">Définit le nom et les options d’un nouvel assembly.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="f4a9b-104">N’appelez pas cette méthode quand vous produisez des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a9b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4a9b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4a9b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4a9b-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="f4a9b-107">Nom du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="f4a9b-108">Interface d' [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="f4a9b-109">Options représentées par l' [énumération AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f4a9b-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="f4a9b-110">Reçoit l’ID unique de l’assembly en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4a9b-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f4a9b-111">Return Value</span></span>  

 <span data-ttu-id="f4a9b-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4a9b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f4a9b-113">Requirements</span></span>  

 <span data-ttu-id="f4a9b-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="f4a9b-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a9b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4a9b-115">See also</span></span>

- [<span data-ttu-id="f4a9b-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f4a9b-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f4a9b-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f4a9b-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f4a9b-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="f4a9b-118">ALink API</span></span>](index.md)
