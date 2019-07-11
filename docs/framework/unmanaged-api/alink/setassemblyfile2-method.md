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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d96881ce35dca1ee7a196507ef8d81a565eed82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741502"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="90e81-102">SetAssemblyFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="90e81-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="90e81-103">Définit le nom et les options pour un nouvel assembly.</span><span class="sxs-lookup"><span data-stu-id="90e81-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="90e81-104">N’appelez pas cette méthode lorsque vous générez des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="90e81-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e81-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e81-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e81-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90e81-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="90e81-107">Nom du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="90e81-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="90e81-108">[IMetaDataEmit2, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="90e81-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="90e81-109">Les options représentées par [AssemblyFlags, énumération](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="90e81-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="90e81-110">Reçoit l’ID unique pour l’assembly en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="90e81-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90e81-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90e81-111">Return Value</span></span>  
 <span data-ttu-id="90e81-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="90e81-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90e81-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90e81-113">Requirements</span></span>  
 <span data-ttu-id="90e81-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="90e81-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e81-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90e81-115">See also</span></span>

- [<span data-ttu-id="90e81-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="90e81-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="90e81-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="90e81-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="90e81-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="90e81-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
