---
title: Hébergement dans une application managée
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 1895f6622f7c528979badd741f5994970bbd1a8c
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169798"
---
# <a name="hosting-in-a-managed-application"></a>Hébergement dans une application managée
Services de Windows Communication Foundation (WCF) peuvent être hébergés dans n’importe quelle application .NET Framework. Les services auto-hébergés constituent l'option d'hébergement la plus flexible parce qu'ils requièrent le déploiement de moins d'infrastructure. Toutefois, il est également l’option d’hébergement moins fiable, car les applications gérées ne fournissent pas d’hébergement avancés et de fonctionnalités de gestion d’autres options d’hébergement dans WCF, comme les services Internet Information Services (IIS) et Windows.  
  
 Pour créer un service auto-hébergé, créez et ouvrez une instance d'objet <xref:System.ServiceModel.ServiceHost>, qui démarre un service d'écoute des messages. Pour plus d'informations, voir [Procédure : Héberger un Service WCF dans une Application managée](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pour obtenir un exemple complet sur la façon de définir un contrat, implémentez le contrat, et héberger un service à l’intérieur d’une application managée, consultez le [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) et [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Les sections suivantes décrivent des scénarios courants utilisant cette option d'hébergement.  
  
## <a name="console-applications"></a>Applications console  
 Scénarios courants qui permet à l’auto-hébergement sont les services WCF qui s’exécutent dans des applications de console. Hébergement d’un service WCF à l’intérieur d’une application console est généralement utile pendant la phase de développement du service. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement.  
  
## <a name="rich-client-applications"></a>Applications clientes complexes  
 Autres scénarios courants qu’auto-hébergement sont les applications clientes riches, tels que ceux basés sur Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Cette option d’hébergement rend également plus facile pour les applications clientes riches, telles que les applications WPF et WinForms, pour communiquer avec le monde extérieur. Par exemple, un client de collaboration pair à pair qui utilise WPF pour son interface utilisateur et héberge également un service WCF qui permet aux autres clients pour vous connecter à celui-ci et partager des informations.  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)
- [Didacticiel Bien démarrer](../../../../docs/framework/wcf/getting-started-tutorial.md)
