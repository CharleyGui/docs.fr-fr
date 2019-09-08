---
title: GetPublicKeyToken, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 158ecc036d56e2ad9a3fa650677c04ebcbfd7696
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777223"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="1a03f-102">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1a03f-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="1a03f-103">Récupère le jeton de clé publique pour un KeyFile ou un conteneur de clé donné.</span><span class="sxs-lookup"><span data-stu-id="1a03f-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a03f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a03f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a03f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a03f-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="1a03f-106">Nom de fichier de la clé.</span><span class="sxs-lookup"><span data-stu-id="1a03f-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="1a03f-107">Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1a03f-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="1a03f-108">Adresse à laquelle le jeton de clé doit être stocké.</span><span class="sxs-lookup"><span data-stu-id="1a03f-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="1a03f-109">Spécifie la taille, en octets, de la mémoire tampon `pvPublicKeyToken`indiquée par.</span><span class="sxs-lookup"><span data-stu-id="1a03f-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="1a03f-110">Lors du retour, contient le nombre réel d’octets utilisés.</span><span class="sxs-lookup"><span data-stu-id="1a03f-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a03f-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a03f-111">Return Value</span></span>  
 <span data-ttu-id="1a03f-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="1a03f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a03f-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a03f-113">Requirements</span></span>  
 <span data-ttu-id="1a03f-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="1a03f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a03f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a03f-115">See also</span></span>

- [<span data-ttu-id="1a03f-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="1a03f-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1a03f-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="1a03f-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1a03f-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="1a03f-118">ALink API</span></span>](index.md)
