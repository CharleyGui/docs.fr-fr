---
title: LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59565b28991f6d61ff2c6c77540eace92461aa89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490168"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
Pointe vers une fonction qui avertit l’hôte lorsqu’un chevauchement (autrement dit, asynchrone) e/s sur un appareil est terminée.  
  
 Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwErrorCode`  
 [in] Une valeur qui est un code d’erreur si l’appareil a été fermée ; Sinon, cette valeur est zéro.  
  
 Fermeture d’un périphérique entraîne tout en attente d’e/s à l’appareil pour être achevée immédiatement.  
  
 `dwNumberOfBytesTransfered`  
 [in] Le nombre d’octets transférés par l’opération d’e/s.  
  
 `lpOverlapped`  
 [in] Un pointeur vers une structure qui contient des informations à utiliser pour terminer la demande d’e/s.  
  
## <a name="remarks"></a>Notes  
 La fonction à laquelle `LPOVERLAPPED_COMPLETION_ROUTINE` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement. La fonction de rappel permet à l’hôte traiter la demande d’e/s terminée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorWks.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
