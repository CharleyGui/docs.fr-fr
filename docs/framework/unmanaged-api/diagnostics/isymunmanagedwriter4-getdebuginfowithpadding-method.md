---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 4ac2cccfb17d82d8c62ad7db89161aa794825ae5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678275"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="d0ab4-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode</span><span class="sxs-lookup"><span data-stu-id="d0ab4-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="d0ab4-103">Fonctionne de la même façon que la [méthode GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne du chemin d’accès est complétée par des zéros après le caractère null de fin pour que les données de la chaîne soient de taille fixe `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="d0ab4-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="d0ab4-104">Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="d0ab4-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="d0ab4-105">Cela facilite l’écriture d’outils qui différencient les fichiers PE.</span><span class="sxs-lookup"><span data-stu-id="d0ab4-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ab4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0ab4-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0ab4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0ab4-107">Parameters</span></span>  
  
|<span data-ttu-id="d0ab4-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0ab4-108">Parameter</span></span>|<span data-ttu-id="d0ab4-109">Description</span><span class="sxs-lookup"><span data-stu-id="d0ab4-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="d0ab4-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d0ab4-110">Return Value</span></span>  

 <span data-ttu-id="d0ab4-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d0ab4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ab4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0ab4-112">Requirements</span></span>  

 <span data-ttu-id="d0ab4-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0ab4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ab4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0ab4-114">See also</span></span>

- [<span data-ttu-id="d0ab4-115">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="d0ab4-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
