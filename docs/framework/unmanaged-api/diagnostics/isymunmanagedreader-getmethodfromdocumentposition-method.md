---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 5afd48b36355835647ab8d06691f2bd2058b00cb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426733"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="8c1b6-102">ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="8c1b6-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="8c1b6-103">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c1b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c1b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c1b6-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="8c1b6-106">dans Document spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="8c1b6-107">dans Ligne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="8c1b6-108">dans Colonne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8c1b6-109">à Pointeur vers l’adresse d’un objet d' [interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) qui représente la méthode contenant le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c1b6-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c1b6-110">Return Value</span></span>  
 <span data-ttu-id="8c1b6-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8c1b6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c1b6-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c1b6-112">Requirements</span></span>  
 <span data-ttu-id="8c1b6-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8c1b6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c1b6-114">See also</span></span>

- [<span data-ttu-id="8c1b6-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="8c1b6-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
