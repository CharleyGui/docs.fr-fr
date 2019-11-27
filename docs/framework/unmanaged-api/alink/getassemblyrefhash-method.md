---
title: GetAssemblyRefHash, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433874"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="93553-102">GetAssemblyRefHash, méthode</span><span class="sxs-lookup"><span data-stu-id="93553-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="93553-103">Récupère un objet blob de hachage pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="93553-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93553-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93553-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="93553-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93553-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="93553-106">ID de l’assembly auquel le hachage fait référence.</span><span class="sxs-lookup"><span data-stu-id="93553-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="93553-107">Reçoit l’objet blob de hachage résultant.</span><span class="sxs-lookup"><span data-stu-id="93553-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="93553-108">Reçoit la taille, en octets, de l’objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="93553-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93553-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="93553-109">Return Value</span></span>  
 <span data-ttu-id="93553-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="93553-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93553-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93553-111">Requirements</span></span>  
 <span data-ttu-id="93553-112">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="93553-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93553-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93553-113">See also</span></span>

- [<span data-ttu-id="93553-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="93553-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="93553-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="93553-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="93553-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="93553-116">ALink API</span></span>](index.md)
