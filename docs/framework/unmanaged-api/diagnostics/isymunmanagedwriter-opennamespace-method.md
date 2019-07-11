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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bd07411acd074bf5a25148110dbdf28a004551a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777245"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="ab78a-102">ISymUnmanagedWriter::OpenNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="ab78a-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="ab78a-103">Ouvre un nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ab78a-103">Opens a new namespace.</span></span> <span data-ttu-id="ab78a-104">Appelez cette méthode avant de définir des méthodes ou des variables qui occupent un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ab78a-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="ab78a-105">Espaces de noms peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="ab78a-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab78a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab78a-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab78a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab78a-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ab78a-108">[in] Pointeur vers le nom du nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ab78a-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab78a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab78a-109">Return Value</span></span>  
 <span data-ttu-id="ab78a-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ab78a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab78a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab78a-111">Requirements</span></span>  
 <span data-ttu-id="ab78a-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab78a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab78a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab78a-113">See also</span></span>

- [<span data-ttu-id="ab78a-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="ab78a-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ab78a-115">CloseNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="ab78a-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
