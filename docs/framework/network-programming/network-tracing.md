---
title: Traçage réseau dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: afb9c3a04258b543e373b6973e576f71f90d7003
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047595"
---
# <a name="network-tracing-in-the-net-framework"></a>Traçage réseau dans le .NET Framework
Le traçage réseau dans .NET Framework fournit l'accès aux informations sur les appels de méthodes et le trafic réseau généré par une application managée. Cette fonctionnalité permet de déboguer les applications en cours de développement et d'analyser celles qui sont déployées. La sortie fournie par un traçage réseau est personnalisable pour prendre en charge différents scénarios d'utilisation au moment du développement et dans un environnement de production.  
  
 Pour activer le traçage réseau dans .NET Framework, vous devez sélectionner une destination pour la sortie de traçage et ajouter des paramètres de configuration de traçage à l'application ou au fichier de configuration de l'ordinateur. Pour obtenir une description des fichiers de configuration et de leur mode d’utilisation, consultez [Fichiers de configuration](../configure-apps/index.md). Pour plus d’informations sur l’activation du traçage réseau, consultez [Activation du traçage réseau](enabling-network-tracing.md). Pour plus d’informations sur les paramètres que vous devez ajouter au fichier de configuration, consultez [Guide pratique pour configurer le traçage réseau](how-to-configure-network-tracing.md).  
  
 Lorsque la traçage est activé, vous pouvez capturer les informations de trace qui sont générées par les classes **System.Net**. Les membres de la classe réseau qui génèrent des informations de traçage contiennent la remarque suivante dans la section Remarques de la documentation bibliothèque de classes .NET Framework :  
  
> [!NOTE]
> Ce membre génère des informations de traçage lorsque vous activez le traçage réseau dans votre application. Pour plus d'informations, consultez Traçage réseau.  
  
## <a name="see-also"></a>Voir aussi

- [Activation du suivi réseau](enabling-network-tracing.md)
- [Guide pratique pour configurer le traçage réseau](how-to-configure-network-tracing.md)
- [Interprétation du suivi réseau](interpreting-network-tracing.md)
- [Suivi et instrumentation d’applications](../debug-trace-profile/tracing-and-instrumenting-applications.md)
