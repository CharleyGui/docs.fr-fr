---
title: ISymUnmanagedMethod::GetRanges, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: 8ed492b573215736c82ab6c231cc5f2e188ea013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732149"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="58f01-102">ISymUnmanagedMethod::GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="58f01-102">ISymUnmanagedMethod::GetRanges Method</span></span>

<span data-ttu-id="58f01-103">À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="58f01-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="58f01-104">Le tableau est un tableau d’entiers et a le format [Start, end, Start, end].</span><span class="sxs-lookup"><span data-stu-id="58f01-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="58f01-105">Le nombre de paires de plages est la longueur du tableau divisée par 2.</span><span class="sxs-lookup"><span data-stu-id="58f01-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f01-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58f01-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58f01-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58f01-107">Parameters</span></span>  

 `document`  
 <span data-ttu-id="58f01-108">dans Document pour lequel l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="58f01-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="58f01-109">dans Ligne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="58f01-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="58f01-110">dans Colonne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="58f01-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="58f01-111">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="58f01-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="58f01-112">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les plages.</span><span class="sxs-lookup"><span data-stu-id="58f01-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="58f01-113">à Pointeur vers la mémoire tampon qui reçoit les plages.</span><span class="sxs-lookup"><span data-stu-id="58f01-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58f01-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="58f01-114">Return Value</span></span>  

 <span data-ttu-id="58f01-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="58f01-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f01-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58f01-116">Requirements</span></span>  

 <span data-ttu-id="58f01-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="58f01-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f01-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58f01-118">See also</span></span>

- [<span data-ttu-id="58f01-119">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="58f01-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
