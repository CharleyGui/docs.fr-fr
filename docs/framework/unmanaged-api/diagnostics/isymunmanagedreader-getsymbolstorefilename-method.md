---
title: ISymUnmanagedReader::GetSymbolStoreFileName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: df503e44f20a0b1f02e2c609cc4b52712520faea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720566"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="63472-102">ISymUnmanagedReader::GetSymbolStoreFileName, méthode</span><span class="sxs-lookup"><span data-stu-id="63472-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="63472-103">Fournit le nom de fichier sur disque du magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="63472-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63472-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63472-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63472-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63472-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="63472-106">dans Taille de la `szName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="63472-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="63472-107">à Pointeur vers la variable qui reçoit la longueur du nom retourné dans `szName` , y compris l’arrêt null.</span><span class="sxs-lookup"><span data-stu-id="63472-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="63472-108">à Pointeur vers la variable qui reçoit le nom de fichier du magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="63472-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63472-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="63472-109">Return Value</span></span>  

 <span data-ttu-id="63472-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="63472-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63472-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="63472-111">Requirements</span></span>  

 <span data-ttu-id="63472-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="63472-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63472-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63472-113">See also</span></span>

- [<span data-ttu-id="63472-114">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="63472-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
