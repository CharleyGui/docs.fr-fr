---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: f363bed8e7002bf898755b434c919f8722dea3fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614498"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="afb79-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2, méthode</span><span class="sxs-lookup"><span data-stu-id="afb79-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="afb79-103">Permet à un compilateur d’omettre les fonctions qui n’ont pas été modifiées à partir du flux de la base de données du programme (PDB), à condition que les informations de ligne répondent à la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="afb79-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="afb79-104">Les informations de ligne correctes peuvent être déterminées par les anciennes informations de ligne PDB et un Delta pour toutes les lignes de la fonction.</span><span class="sxs-lookup"><span data-stu-id="afb79-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb79-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afb79-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb79-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="afb79-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="afb79-107">dans Pointeur vers un [IStream](/windows/desktop/api/objidl/nn-objidl-istream) qui contient les informations de ligne.</span><span class="sxs-lookup"><span data-stu-id="afb79-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="afb79-108">dans Pointeur vers une structure [SYMLINEDELTA](symlinedelta-structure.md) qui contient les lignes qui ont changé.</span><span class="sxs-lookup"><span data-stu-id="afb79-108">[in] A pointer to a [SYMLINEDELTA](symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="afb79-109">dans `ULONG`Qui représente le nombre de lignes qui ont changé.</span><span class="sxs-lookup"><span data-stu-id="afb79-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afb79-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="afb79-110">Return Value</span></span>  
 <span data-ttu-id="afb79-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="afb79-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb79-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="afb79-112">Requirements</span></span>  
 <span data-ttu-id="afb79-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="afb79-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb79-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb79-114">See also</span></span>

- [<span data-ttu-id="afb79-115">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="afb79-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
