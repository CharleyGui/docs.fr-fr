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
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448879"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="2173e-102">ISymUnmanagedMethod::GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="2173e-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="2173e-103">Obtient tous les points de séquence de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2173e-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2173e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2173e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2173e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2173e-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="2173e-106">dans `ULONG32` qui reçoit la taille des tableaux `offsets`, `documents`, `lines`, `columns`, `endLines`et `endColumns`.</span><span class="sxs-lookup"><span data-stu-id="2173e-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="2173e-107">à Pointeur vers un `ULONG32` qui reçoit la longueur de la mémoire tampon requise pour contenir les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="2173e-108">dans Tableau dans lequel stocker les offsets MSIL (Microsoft Intermediate Language) à partir du début de la méthode pour les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="2173e-109">dans Tableau dans lequel stocker les documents dans lesquels se trouvent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="2173e-110">dans Tableau dans lequel stocker les lignes des documents où se trouvent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="2173e-111">dans Tableau dans lequel stocker les colonnes des documents où se trouvent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="2173e-112">dans Tableau de lignes des documents où se terminent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="2173e-113">dans Tableau de colonnes dans les documents où se terminent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="2173e-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2173e-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2173e-114">Return Value</span></span>  
 <span data-ttu-id="2173e-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2173e-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2173e-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2173e-116">Requirements</span></span>  
 <span data-ttu-id="2173e-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2173e-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2173e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2173e-118">See also</span></span>

- [<span data-ttu-id="2173e-119">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="2173e-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
