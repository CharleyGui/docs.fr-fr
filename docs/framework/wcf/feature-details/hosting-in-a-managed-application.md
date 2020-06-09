---
title: Hébergement dans une application managée
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 759257edf89d1af5c453bb98f41361b54cf113ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597343"
---
# <a name="hosting-in-a-managed-application"></a>Hébergement dans une application managée
Les services Windows Communication Foundation (WCF) peuvent être hébergés dans n’importe quelle application .NET Framework. Les services auto-hébergés constituent l'option d'hébergement la plus flexible parce qu'ils requièrent le déploiement de moins d'infrastructure. Toutefois, il s’agit également de l’option d’hébergement la moins fiable, car les applications gérées ne fournissent pas les fonctionnalités d’hébergement et de gestion avancées d’autres options d’hébergement dans WCF, telles que Internet Information Services (IIS) et les services Windows.  
  
 Pour créer un service auto-hébergé, créez et ouvrez une instance d'objet <xref:System.ServiceModel.ServiceHost>, qui démarre un service d'écoute des messages. Pour plus d’informations, consultez [Comment : héberger un service WCF dans une application managée](../how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pour obtenir un exemple complet sur la façon de définir un contrat, d’implémenter le contrat et d’héberger un service à l’intérieur d’une application gérée, consultez le [didacticiel prise en main](../getting-started-tutorial.md) et l' [auto-hébergement](../samples/self-host.md).  
  
 Les sections suivantes décrivent des scénarios courants utilisant cette option d'hébergement.  
  
## <a name="console-applications"></a>Applications console  
 Les scénarios courants que l’auto-hébergement active sont les services WCF qui s’exécutent dans les applications console. L’hébergement d’un service WCF à l’intérieur d’une application console est généralement utile pendant la phase de développement du service. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement.  
  
## <a name="rich-client-applications"></a>Applications clientes complexes  
 D’autres scénarios courants que l’auto-hébergement active sont des applications clientes riches, telles que celles basées sur Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Cette option d’hébergement permet également aux applications clientes riches, telles que les applications WPF et WinForms, de communiquer facilement avec le monde extérieur. Par exemple, un client de collaboration pair à pair qui utilise WPF pour son interface utilisateur et héberge également un service WCF qui permet à d’autres clients de s’y connecter et de partager des informations.  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement de services](../hosting-services.md)
- [Didacticiel Prise en main](../getting-started-tutorial.md)
