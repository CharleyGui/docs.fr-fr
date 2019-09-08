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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db205993bc1a0665dc0003948ce805813251f48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787452"
---
# <a name="getfiledef-method"></a><span data-ttu-id="013cd-102">GetFileDef, méthode</span><span class="sxs-lookup"><span data-stu-id="013cd-102">GetFileDef Method</span></span>
<span data-ttu-id="013cd-103">Récupère le jeton FileDef réel utilisé dans les métadonnées (par opposition au jeton assigné par ALink).</span><span class="sxs-lookup"><span data-stu-id="013cd-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="013cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="013cd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="013cd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="013cd-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="013cd-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="013cd-107">Jeton du fichier ajouté tel qu’il a été récupéré à partir de la méthode AddFile ou de la méthode AddImport,.</span><span class="sxs-lookup"><span data-stu-id="013cd-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="013cd-108">Reçoit le jeton FileDef.</span><span class="sxs-lookup"><span data-stu-id="013cd-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="013cd-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="013cd-109">Return Value</span></span>  
 <span data-ttu-id="013cd-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="013cd-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013cd-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="013cd-111">Requirements</span></span>  
 <span data-ttu-id="013cd-112">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="013cd-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013cd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="013cd-113">See also</span></span>

- [<span data-ttu-id="013cd-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="013cd-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="013cd-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="013cd-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="013cd-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="013cd-116">ALink API</span></span>](index.md)
