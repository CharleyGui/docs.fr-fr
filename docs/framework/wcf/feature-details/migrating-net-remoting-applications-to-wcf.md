---
title: Migration d'applications .NET Remoting vers WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 2cfaebd064d10e5b331412d177929ecb20117a07
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248212"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migration d'applications .NET Remoting vers WCF

**Cette rubrique est spécifique à une technologie héritée qui est conservée pour la compatibilité descendante avec les applications existantes et n’est pas recommandée pour un nouveau développement. Les applications distribuées doivent maintenant être développées à l’aide de WCF.**  
  
 Il existe deux façons de tirer parti de WCF avec les applications .NET Remoting existantes : intégration et migration. L’intégration vous permet d’avoir .NET Remoting 2,0 et WCF s’exécutant côte à côte, ce qui vous permet d’exposer les mêmes objets métier sur les deux technologies simultanément, sans avoir à modifier votre code .NET Remoting .NET 2,0 Remoting existant. Pour l’intégration, vous devez exécuter sur .NET Framework 2,0 ou une version ultérieure. Si vous souhaitez tirer parti des fonctionnalités WCF et que vous n’avez pas besoin de la compatibilité des câbles avec les systèmes Remoting 2,0, vous pouvez migrer l’ensemble de votre service vers WCF. La migration de .NET Remoting 2,0 vers WCF nécessite des modifications de l’interface de l’objet distant et de ses paramètres de configuration. Ces deux rubriques sont abordées dans [la rubrique de la communication à distance au Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble conceptuelle](../conceptual-overview.md)
