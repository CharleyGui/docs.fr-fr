---
title: Déploiement d'applications WCF à l'aide de ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 52657c5f3b5bc6c57c59f4ef23e73089f3c681eb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550369"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>Déploiement d'applications WCF à l'aide de ClickOnce
Les applications clientes qui utilisent Windows Communication Foundation (WCF) peuvent être déployées à l’aide de la technologie ClickOnce. Cette technologie leur permet de tirer parti des protections de sécurité d'exécution fournies par la sécurité d'accès du code, sous réserve qu'elles soient signées numériquement avec un certificat approuvé. Le certificat utilisé pour signer l'application ClickOnce doit résider dans le magasin d'éditeurs approuvés, et la stratégie de sécurité locale sur l'ordinateur client doit être configurée pour accorder des autorisations Confiance totale aux applications signées avec le certificat de l'éditeur.  
  
 Pour plus d’informations sur la configuration des applications ClickOnce et des éditeurs approuvés, consultez [Configuration des éditeurs approuvés ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview)
- [Déploiement ClickOnce pour les applications Windows Forms](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
