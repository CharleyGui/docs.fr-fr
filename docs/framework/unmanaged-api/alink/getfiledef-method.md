---
title: GetFileDef, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 42935813579d7f1d55a9f1daf9d8c6c1241f85be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684705"
---
# <a name="getfiledef-method"></a><span data-ttu-id="a513c-102">GetFileDef, méthode</span><span class="sxs-lookup"><span data-stu-id="a513c-102">GetFileDef Method</span></span>

<span data-ttu-id="a513c-103">Récupère le jeton FileDef réel utilisé dans les métadonnées (par opposition au jeton assigné par ALink).</span><span class="sxs-lookup"><span data-stu-id="a513c-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a513c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a513c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a513c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a513c-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="a513c-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a513c-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="a513c-107">Jeton du fichier ajouté tel qu’il a été récupéré à partir de la méthode AddFile ou de la méthode AddImport,.</span><span class="sxs-lookup"><span data-stu-id="a513c-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="a513c-108">Reçoit le jeton FileDef.</span><span class="sxs-lookup"><span data-stu-id="a513c-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a513c-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a513c-109">Return Value</span></span>  

 <span data-ttu-id="a513c-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="a513c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a513c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a513c-111">Requirements</span></span>  

 <span data-ttu-id="a513c-112">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="a513c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a513c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a513c-113">See also</span></span>

- [<span data-ttu-id="a513c-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="a513c-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a513c-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="a513c-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a513c-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="a513c-116">ALink API</span></span>](index.md)
