---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 3c82cf45bca3cc9ec73255586db73a903edaf1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698570"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="57516-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode</span><span class="sxs-lookup"><span data-stu-id="57516-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>

<span data-ttu-id="57516-103">Obtient l’identificateur de l’algorithme de somme de contrôle, ou retourne un GUID de tous les zéros s’il n’y a pas de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="57516-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57516-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57516-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57516-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="57516-106">à Pointeur vers une variable qui reçoit l’identificateur d’algorithme de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="57516-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57516-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="57516-107">Return Value</span></span>  

 <span data-ttu-id="57516-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="57516-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57516-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57516-109">See also</span></span>

- [<span data-ttu-id="57516-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="57516-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
