---
title: ISymUnmanagedDocument::GetSourceRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 64ecbb56ab32ac8381a4864acd5fd40741786d30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449137"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="c6e2d-102">ISymUnmanagedDocument::GetSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="c6e2d-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="c6e2d-103">Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="c6e2d-104">La mémoire tampon doit être suffisamment grande pour contenir la source.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6e2d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e2d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6e2d-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="c6e2d-107">dans Ligne de début dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="c6e2d-108">dans Colonne de début dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="c6e2d-109">dans Dernière ligne dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="c6e2d-110">dans Dernière colonne dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="c6e2d-111">dans Taille de la source, en octets.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="c6e2d-112">à Pointeur vers une variable qui reçoit la taille de la source.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="c6e2d-113">à Taille et longueur de la plage spécifiée du document source, en octets.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6e2d-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6e2d-114">Return Value</span></span>  
 <span data-ttu-id="c6e2d-115">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c6e2d-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e2d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6e2d-116">See also</span></span>

- [<span data-ttu-id="c6e2d-117">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="c6e2d-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
