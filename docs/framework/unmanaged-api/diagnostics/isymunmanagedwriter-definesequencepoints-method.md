---
title: ISymUnmanagedWriter::DefineSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614797"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="0e426-102">ISymUnmanagedWriter::DefineSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="0e426-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="0e426-103">Définit un groupe de points de séquence dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="0e426-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="0e426-104">Chaque ligne de départ et colonne de début définissent le début d’une instruction dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="0e426-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="0e426-105">Chaque ligne de fin et colonne de fin définissent la fin d’une instruction dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="0e426-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="0e426-106">Les tableaux doivent être triés par ordre de décalage.</span><span class="sxs-lookup"><span data-stu-id="0e426-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="0e426-107">L’offset est toujours mesuré à partir du début de la méthode, en octets.</span><span class="sxs-lookup"><span data-stu-id="0e426-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e426-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e426-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e426-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e426-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="0e426-110">dans Objet document pour lequel les points de séquence sont définis.</span><span class="sxs-lookup"><span data-stu-id="0e426-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="0e426-111">dans `ULONG32`Qui indique la taille de chacun des tampons,,, `offsets` `lines` `columns` `endLines` et `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="0e426-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="0e426-112">dans Décalage des points de séquence mesuré à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0e426-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="0e426-113">dans Numéros de ligne de départ des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="0e426-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="0e426-114">dans Numéros de colonne de début des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="0e426-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="0e426-115">dans Numéros de ligne de fin des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="0e426-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="0e426-116">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0e426-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="0e426-117">dans Numéros de colonne de fin des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="0e426-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="0e426-118">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0e426-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e426-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0e426-119">Return Value</span></span>  
 <span data-ttu-id="0e426-120">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0e426-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e426-121">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0e426-121">Requirements</span></span>  
 <span data-ttu-id="0e426-122">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0e426-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e426-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e426-123">See also</span></span>

- [<span data-ttu-id="0e426-124">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="0e426-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
