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
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427865"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="5ca12-102">ISymUnmanagedWriter::SetMethodSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="5ca12-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="5ca12-103">Spécifie le début et la fin d’une méthode dans un fichier source.</span><span class="sxs-lookup"><span data-stu-id="5ca12-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="5ca12-104">Utilisez cette méthode pour spécifier l’étendue d’une méthode indépendamment des points de séquence qui existent dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="5ca12-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca12-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca12-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ca12-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ca12-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="5ca12-107">dans Pointeur vers le document contenant la position de départ.</span><span class="sxs-lookup"><span data-stu-id="5ca12-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="5ca12-108">dans Numéro de la ligne de départ.</span><span class="sxs-lookup"><span data-stu-id="5ca12-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="5ca12-109">dans Colonne de départ.</span><span class="sxs-lookup"><span data-stu-id="5ca12-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="5ca12-110">dans Pointeur vers le document contenant la position de fin.</span><span class="sxs-lookup"><span data-stu-id="5ca12-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="5ca12-111">dans Numéro de la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="5ca12-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="5ca12-112">dans Numéro de la colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="5ca12-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ca12-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5ca12-113">Return Value</span></span>  
 <span data-ttu-id="5ca12-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5ca12-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ca12-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ca12-115">Requirements</span></span>  
 <span data-ttu-id="5ca12-116">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5ca12-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca12-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca12-117">See also</span></span>

- [<span data-ttu-id="5ca12-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="5ca12-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
