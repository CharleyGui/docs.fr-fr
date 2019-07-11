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
ms.openlocfilehash: ec2c357cd56670f4f2deed8023bed7842a7f4ed7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741875"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="be07a-102">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="be07a-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="be07a-103">Récupère le jeton de clé publique pour un fichier de clé ou conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="be07a-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be07a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be07a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="be07a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be07a-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="be07a-106">Nom de fichier de la clé.</span><span class="sxs-lookup"><span data-stu-id="be07a-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="be07a-107">Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="be07a-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="be07a-108">Adresse où le jeton de clé doit être stocké.</span><span class="sxs-lookup"><span data-stu-id="be07a-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="be07a-109">Spécifie la taille, en octets, de la mémoire tampon indiqué par `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="be07a-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="be07a-110">Au retour, contient le nombre réel d’octets utilisés.</span><span class="sxs-lookup"><span data-stu-id="be07a-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be07a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be07a-111">Return Value</span></span>  
 <span data-ttu-id="be07a-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="be07a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be07a-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be07a-113">Requirements</span></span>  
 <span data-ttu-id="be07a-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="be07a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be07a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be07a-115">See also</span></span>

- [<span data-ttu-id="be07a-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="be07a-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="be07a-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="be07a-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="be07a-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="be07a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
