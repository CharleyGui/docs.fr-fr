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
ms.openlocfilehash: a918b5c2334683348adc6a7382527faedb52d7b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683535"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="5d349-102">ISymUnmanagedWriter::SetMethodSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="5d349-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="5d349-103">Spécifie les véritables début et fin d'une méthode dans un fichier source.</span><span class="sxs-lookup"><span data-stu-id="5d349-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="5d349-104">Utilisez cette méthode pour spécifier l’étendue d’une méthode indépendamment des points de séquence qui existent dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="5d349-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d349-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d349-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d349-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d349-106">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="5d349-107">dans Pointeur vers le document contenant la position de départ.</span><span class="sxs-lookup"><span data-stu-id="5d349-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="5d349-108">dans Numéro de la ligne de départ.</span><span class="sxs-lookup"><span data-stu-id="5d349-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="5d349-109">dans Colonne de départ.</span><span class="sxs-lookup"><span data-stu-id="5d349-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="5d349-110">dans Pointeur vers le document contenant la position de fin.</span><span class="sxs-lookup"><span data-stu-id="5d349-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="5d349-111">dans Numéro de la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="5d349-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="5d349-112">dans Numéro de la colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="5d349-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d349-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5d349-113">Return Value</span></span>  

 <span data-ttu-id="5d349-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5d349-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d349-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d349-115">Requirements</span></span>  

 <span data-ttu-id="5d349-116">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5d349-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d349-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d349-117">See also</span></span>

- [<span data-ttu-id="5d349-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="5d349-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
