---
title: GetWin32ResBlob, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdc1ef6490f250ebe93b0482adf244adfc0ffd56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741782"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="e5af0-102">GetWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="e5af0-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="e5af0-103">Récupère le blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="e5af0-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="e5af0-104">Appelez cette méthode après avoir défini les options d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e5af0-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5af0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5af0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5af0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5af0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e5af0-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e5af0-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5af0-108">Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de Version Win32</span><span class="sxs-lookup"><span data-stu-id="e5af0-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="e5af0-109">TRUE si le fichier est une DLL, false pour un fichier EXE.</span><span class="sxs-lookup"><span data-stu-id="e5af0-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="e5af0-110">Icône facultative à insérer dans le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="e5af0-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="e5af0-111">Reçoit le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="e5af0-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="e5af0-112">Reçoit la taille de l’objet blob.</span><span class="sxs-lookup"><span data-stu-id="e5af0-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5af0-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e5af0-113">Return Value</span></span>  
 <span data-ttu-id="e5af0-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="e5af0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5af0-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5af0-115">Requirements</span></span>  
 <span data-ttu-id="e5af0-116">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="e5af0-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5af0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5af0-117">See also</span></span>

- [<span data-ttu-id="e5af0-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e5af0-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e5af0-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e5af0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e5af0-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="e5af0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
