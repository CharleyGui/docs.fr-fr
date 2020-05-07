---
title: CorpubPublish (coclasse)
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860911"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish (coclasse)
Fournit les interfaces pour la publication d'informations sur les domaines d'application et les processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|[ICorPublish, interface](icorpublish-interface.md)|Fournit des méthodes pour la publication d’informations sur les processus et les domaines d’application dans ces processus.|  
|[ICorPublishAppDomain, interface](icorpublishappdomain-interface.md)|Représente et fournit des informations sur, un domaine d’application dans un processus.|  
|[ICorPublishAppDomainEnum, interface](icorpublishappdomainenum-interface.md)|Fournit des méthodes qui parcourent une collection de domaines d’application qui existent actuellement dans un processus.|  
|[ICorPublishProcess, interface](icorpublishprocess-interface.md)|Représente un processus qui s’exécute sur un ordinateur.|  
|[ICorPublishProcessEnum, interface](icorpublishprocessenum-interface.md)|Fournit des méthodes qui parcourent une collection de processus en cours d’exécution sur un ordinateur.|  
  
## <a name="remarks"></a>Notes   
 Un scénario de publication classique implique un développeur qui souhaite déboguer du code managé qui s’exécute sur un ordinateur au sein d’un domaine d’application. L’environnement d’hébergement peut exécuter plusieurs domaines d’application au sein d’un processus. Le développeur souhaite utiliser une interface graphique utilisateur ou d’autres moyens pour répertorier tous les processus en cours d’exécution sur l’ordinateur et choisir un processus spécifique. La liste doit inclure tous les domaines d’application dans les processus qui exécutent du code managé. Le développeur peut ensuite identifier le domaine d’application spécifique et attacher un débogueur à ce domaine.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
