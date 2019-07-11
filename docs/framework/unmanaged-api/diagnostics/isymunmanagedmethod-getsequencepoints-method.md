---
title: ISymUnmanagedMethod::GetSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8cfde8f0eb14919c12d261c3f9f7209365829c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759447"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="ffd6b-102">ISymUnmanagedMethod::GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="ffd6b-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="ffd6b-103">Obtient tous les points de séquence au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffd6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffd6b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffd6b-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="ffd6b-106">[in] Un `ULONG32` qui reçoit la taille de la `offsets`, `documents`, `lines`, `columns`, `endLines`, et `endColumns` tableaux.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="ffd6b-107">[out] Un pointeur vers un `ULONG32` qui reçoit la longueur de la mémoire tampon requise pour contenir les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="ffd6b-108">[in] Tableau dans lequel stocker le Microsoft intermediate language (MSIL) offsets à partir du début de la méthode pour les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="ffd6b-109">[in] Tableau dans lequel stocker les documents dans laquelle se trouvent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="ffd6b-110">[in] Tableau dans lequel stocker les lignes des documents auxquelles figurent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="ffd6b-111">[in] Tableau dans lequel stocker les colonnes des documents auxquelles figurent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="ffd6b-112">[in] Tableau de lignes des documents auxquelles la séquence de points de fin.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="ffd6b-113">[in] Tableau de colonnes des documents auxquelles la séquence de points de fin.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffd6b-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ffd6b-114">Return Value</span></span>  
 <span data-ttu-id="ffd6b-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ffd6b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffd6b-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ffd6b-116">Requirements</span></span>  
 <span data-ttu-id="ffd6b-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ffd6b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd6b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffd6b-118">See also</span></span>

- [<span data-ttu-id="ffd6b-119">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="ffd6b-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
