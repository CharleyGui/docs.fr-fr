---
title: ISymUnmanagedVariable::GetAttributes, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 1142dbb83693f6104ba6e22e174ce02fb92997a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726897"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="17fe0-102">ISymUnmanagedVariable::GetAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="17fe0-102">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="17fe0-103">Obtient les indicateurs d’attribut pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="17fe0-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fe0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17fe0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17fe0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17fe0-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="17fe0-106">à Pointeur vers un `ULONG32` qui reçoit les attributs.</span><span class="sxs-lookup"><span data-stu-id="17fe0-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="17fe0-107">La valeur retournée sera l’une des valeurs définies dans l’énumération [CorSymVarFlag,](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="17fe0-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17fe0-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="17fe0-108">Return Value</span></span>  

 <span data-ttu-id="17fe0-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="17fe0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17fe0-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17fe0-110">Requirements</span></span>  

 <span data-ttu-id="17fe0-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="17fe0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17fe0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17fe0-112">See also</span></span>

- [<span data-ttu-id="17fe0-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="17fe0-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
