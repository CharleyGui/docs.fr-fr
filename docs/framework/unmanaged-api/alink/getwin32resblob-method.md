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
ms.openlocfilehash: 03f6c97b4a5bbbdc0aeaf7b3f07277e66d7d0e9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684510"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="5c572-102">GetWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="5c572-102">GetWin32ResBlob Method</span></span>

<span data-ttu-id="5c572-103">Récupère l’objet blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="5c572-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="5c572-104">Appelez cette méthode après avoir défini les options d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5c572-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c572-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c572-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5c572-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c572-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5c572-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5c572-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5c572-108">Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de version Win32</span><span class="sxs-lookup"><span data-stu-id="5c572-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="5c572-109">TRUE si le fichier est une DLL, false pour un EXE.</span><span class="sxs-lookup"><span data-stu-id="5c572-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="5c572-110">Icône facultative à insérer dans l’objet blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="5c572-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="5c572-111">Reçoit l’objet blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="5c572-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="5c572-112">Reçoit la taille de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="5c572-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c572-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5c572-113">Return Value</span></span>  

 <span data-ttu-id="5c572-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="5c572-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c572-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c572-115">Requirements</span></span>  

 <span data-ttu-id="5c572-116">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="5c572-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c572-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c572-117">See also</span></span>

- [<span data-ttu-id="5c572-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="5c572-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5c572-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="5c572-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5c572-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="5c572-120">ALink API</span></span>](index.md)
