---
title: ISymUnmanagedDocument::GetCheckSum, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 4030da31400b7075952d146e5d6740306863e9ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721086"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="d59d7-102">ISymUnmanagedDocument::GetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="d59d7-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>

<span data-ttu-id="d59d7-103">Obtient la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="d59d7-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d59d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59d7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d59d7-105">Parameters</span></span>  

 `cData`  
 <span data-ttu-id="d59d7-106">dans Longueur de la mémoire tampon fournie par le `data` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d59d7-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="d59d7-107">à Taille et longueur de la somme de contrôle, en octets.</span><span class="sxs-lookup"><span data-stu-id="d59d7-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="d59d7-108">à Mémoire tampon qui reçoit la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="d59d7-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59d7-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d59d7-109">Return Value</span></span>  

 <span data-ttu-id="d59d7-110">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d59d7-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59d7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d59d7-111">See also</span></span>

- [<span data-ttu-id="d59d7-112">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="d59d7-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
