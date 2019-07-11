---
title: ISymUnmanagedWriter::SetMethodSourceRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e06695f5ba348315523c7414822ce87d594bdbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776604"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="d9817-102">ISymUnmanagedWriter::SetMethodSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="d9817-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="d9817-103">Spécifie les véritables début et la fin d’une méthode dans un fichier source.</span><span class="sxs-lookup"><span data-stu-id="d9817-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="d9817-104">Utilisez cette méthode pour spécifier l’étendue d’une méthode indépendamment les points de séquence qui existent au sein de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9817-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9817-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9817-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9817-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9817-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="d9817-107">[in] Pointeur vers le document contenant la position de départ.</span><span class="sxs-lookup"><span data-stu-id="d9817-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="d9817-108">[in] Le numéro de ligne de départ.</span><span class="sxs-lookup"><span data-stu-id="d9817-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="d9817-109">[in] La colonne de départ.</span><span class="sxs-lookup"><span data-stu-id="d9817-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="d9817-110">[in] Pointeur vers le document contenant la position de fin.</span><span class="sxs-lookup"><span data-stu-id="d9817-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="d9817-111">[in] Numéro de ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="d9817-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="d9817-112">[in] Numéro de colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="d9817-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9817-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d9817-113">Return Value</span></span>  
 <span data-ttu-id="d9817-114">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d9817-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9817-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9817-115">Requirements</span></span>  
 <span data-ttu-id="d9817-116">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d9817-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9817-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9817-117">See also</span></span>

- [<span data-ttu-id="d9817-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="d9817-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
