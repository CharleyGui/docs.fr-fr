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
ms.openlocfilehash: cd5d1f2d59d3e55ba454f23d2e5dd4b1316c0df4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615174"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="e9c5f-102">ISymUnmanagedMethod::GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="e9c5f-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="e9c5f-103">À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="e9c5f-104">Le tableau est un tableau d’entiers et a le format [Start, end, Start, end].</span><span class="sxs-lookup"><span data-stu-id="e9c5f-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="e9c5f-105">Le nombre de paires de plages est la longueur du tableau divisée par 2.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c5f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9c5f-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e9c5f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9c5f-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e9c5f-108">dans Document pour lequel l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="e9c5f-109">dans Ligne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="e9c5f-110">dans Colonne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="e9c5f-111">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="e9c5f-112">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les plages.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="e9c5f-113">à Pointeur vers la mémoire tampon qui reçoit les plages.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c5f-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e9c5f-114">Return Value</span></span>  
 <span data-ttu-id="e9c5f-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e9c5f-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c5f-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e9c5f-116">Requirements</span></span>  
 <span data-ttu-id="e9c5f-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e9c5f-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c5f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9c5f-118">See also</span></span>

- [<span data-ttu-id="e9c5f-119">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="e9c5f-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
