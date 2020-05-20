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
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441095"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="4b942-102">ISymUnmanagedDocument::GetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="4b942-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="4b942-103">Obtient la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="4b942-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b942-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b942-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b942-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b942-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="4b942-106">dans Longueur de la mémoire tampon fournie par le `data` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4b942-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="4b942-107">à Taille et longueur de la somme de contrôle, en octets.</span><span class="sxs-lookup"><span data-stu-id="4b942-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="4b942-108">à Mémoire tampon qui reçoit la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="4b942-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b942-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4b942-109">Return Value</span></span>  
 <span data-ttu-id="4b942-110">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4b942-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b942-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b942-111">See also</span></span>

- [<span data-ttu-id="4b942-112">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="4b942-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
