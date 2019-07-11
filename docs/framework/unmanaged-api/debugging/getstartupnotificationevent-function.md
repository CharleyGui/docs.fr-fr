---
title: Fonction GetStartupNotificationEvent
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67f3ef57b4996eb4a956c596b76fb94b1bdfd7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738889"
---
# <a name="getstartupnotificationevent-function"></a>Fonction GetStartupNotificationEvent
Crée ou ouvre un gestionnaire d'événements qui sera signalé par un Common Language Runtime (CLR) qui est chargé dans le processus cible spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Paramètres  
 `debuggeePID`  
 [in] Identificateur du processus cible à partir duquel les notifications de démarrage du CLR sont reçues.  
  
 `phStartupEvent`  
 [out] Pointeur vers un handle qui sera signalé par un CLR au démarrage.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le handle de l'événement de notification de démarrage a été obtenu.  
  
 E_INVALIDARG  
 `phStartupEvent` est null ou `debuggeePID` ne fait pas référence à un processus en cours d'exécution.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible d'obtenir le handle de l'événement de notification de démarrage.  
  
## <a name="remarks"></a>Notes  
 Sur le système d'exploitation Windows, `debuggeePID` est mappé à un identificateur de processus du système d'exploitation.  
  
 L'événement est signalé avant l'exécution de code managé par le CLR ayant signalé l'événement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** dbgshim.h  
  
 **Bibliothèque :** dbgshim.dll  
  
 **Versions du .NET framework :** 3.5 SP1
