---
title: Déploiement d'applications WCF à l'aide de ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802234"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>Déploiement d'applications WCF à l'aide de ClickOnce
Les applications clientes qui utilisent Windows Communication Foundation (WCF) peuvent être déployées à l’aide de la technologie ClickOnce. Cette technologie leur permet de tirer parti des protections de sécurité d'exécution fournies par la sécurité d'accès du code, sous réserve qu'elles soient signées numériquement avec un certificat approuvé. Le certificat utilisé pour signer l'application ClickOnce doit résider dans le magasin d'éditeurs approuvés, et la stratégie de sécurité locale sur l'ordinateur client doit être configurée pour accorder des autorisations Confiance totale aux applications signées avec le certificat de l'éditeur.  
  
 Pour plus d’informations sur la configuration des applications ClickOnce et des éditeurs approuvés, consultez [Configuration des éditeurs approuvés ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview)
- [Déploiement ClickOnce pour les applications Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
