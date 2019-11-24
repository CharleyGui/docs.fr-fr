---
title: ISymUnmanagedWriter::OpenNamespace, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: acbd49de7362d9c05a609a2d870af100637e10ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427905"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="e6998-102">ISymUnmanagedWriter::OpenNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="e6998-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="e6998-103">Ouvre un nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e6998-103">Opens a new namespace.</span></span> <span data-ttu-id="e6998-104">Call this method before defining methods or variables that occupy a namespace.</span><span class="sxs-lookup"><span data-stu-id="e6998-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="e6998-105">Namespaces can be nested.</span><span class="sxs-lookup"><span data-stu-id="e6998-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6998-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6998-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6998-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6998-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e6998-108">[in] A pointer to the name of the new namespace.</span><span class="sxs-lookup"><span data-stu-id="e6998-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6998-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e6998-109">Return Value</span></span>  
 <span data-ttu-id="e6998-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="e6998-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6998-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="e6998-111">Requirements</span></span>  
 <span data-ttu-id="e6998-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6998-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6998-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6998-113">See also</span></span>

- [<span data-ttu-id="e6998-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="e6998-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="e6998-115">CloseNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="e6998-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
