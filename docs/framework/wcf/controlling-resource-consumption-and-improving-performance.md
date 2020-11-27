---
title: Contrôle de la consommation des ressources et amélioration des performances
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: f06dd0b7e66ae783b2f268551f15c5e6e8369b7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255063"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Contrôle de la consommation des ressources et amélioration des performances

Cette rubrique décrit différentes propriétés dans différentes zones de l’architecture Windows Communication Foundation (WCF) qui fonctionnent pour contrôler la consommation des ressources et affectent les mesures de performance.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Propriétés qui contraignent la consommation des ressources dans WCF

 Windows Communication Foundation (WCF) applique des contraintes sur certains types de processus, à des fins de sécurité ou de performances. Ces contraintes se présentent sous deux formes principales, les quotas et les accélérateurs. Les *quotas* sont des limites qui, lorsqu’ils sont atteints ou dépassés, déclenchent une exception immédiate à un moment donné dans le système. *Les limitations* sont des limites qui n’entraînent pas immédiatement la levée d’une exception. Au lieu de cela, lorsqu'une limite d'accélérateur est atteinte, le traitement continue mais dans les limites définies par la valeur de l'accélérateur. Ce traitement limité peut déclencher une exception ailleurs, mais cela dépend de l'application.

 Outre la distinction entre les quotas et les accélérateurs, certaines propriétés contraignantes se trouvent au niveau de la sérialisation, d'autres au niveau du transport et d'autres encore au niveau de l'application. Par exemple, le quota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, qui est implémenté par tous les éléments de liaison de transport fournis par le système a la valeur 65 536 octets par défaut afin d’empêcher des clients malveillants de prendre part à des attaques par déni de service contre un service en provoquant une consommation de mémoire excessive. (En général, vous pouvez augmenter les performances en diminuant cette valeur.)

 La propriété <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> est un exemple de quota de sérialisation, qui spécifie le nombre maximal d'objets que le sérialiseur sérialise ou désérialise dans un appel de méthode <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> unique. Un exemple d'accélérateur au niveau de l'application est la propriété <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> qui, par défaut, restreint le nombre de connexions de canal de session simultanées à 10. (Contrairement aux quotas, si cette valeur d'accélérateur est atteinte, l'application poursuit le traitement mais n'accepte aucun nouveau canal de session, ce qui signifie que les nouveaux clients ne peuvent pas se connecter jusqu'à ce que l'un des autres canaux de session prenne fin.)

 Ces contrôles sont conçus pour fournir une atténuation intégrée des risques liés à certains types d’attaques ou pour améliorer les mesures de performances telles que l’encombrement mémoire, le délai de démarrage, etc. Toutefois, selon l'application, ces contrôles peuvent entraver les performances de l'application de service ou empêcher globalement l'application de fonctionner. Par exemple, une application conçue pour transmettre en continu du contenu vidéo peut facilement dépasser la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> par défaut. Cette rubrique fournit une vue d’ensemble des différents contrôles appliqués aux applications à tous les niveaux de WCF, décrit les différentes façons d’obtenir plus d’informations sur la façon dont un paramètre entrave votre application et décrit les manières de corriger divers problèmes. La plupart des accélérateurs et certains quotas sont disponibles au niveau de l'application, même lorsque la propriété de base est une contrainte de sérialisation ou de transport. Par exemple, vous pouvez définir la propriété <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> en utilisant la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> sur la classe de service.

> [!NOTE]
> Si vous avez un problème particulier, vous devez d’abord lire le Guide de [démarrage rapide de la résolution des problèmes WCF](wcf-troubleshooting-quickstart.md) pour voir si votre problème (et une solution) y figure.

 Les propriétés qui restreignent les processus de sérialisation sont répertoriées dans considérations sur la [sécurité pour les données](./feature-details/security-considerations-for-data.md). Les propriétés qui restreignent la consommation des ressources liées aux transports sont répertoriées dans [quotas de transport](./feature-details/transport-quotas.md). Les propriétés qui restreignent la consommation de ressources au niveau de la couche d'application sont membres de la classe <xref:System.ServiceModel.Dispatcher.ServiceThrottle>.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Détection des problèmes d'application et de performances en rapport avec les paramètres de quota

 Les valeurs par défaut des valeurs précédentes ont été choisies pour activer les fonctionnalités d'application de base sur une large gamme de types d'applications tout en assurant une protection de base contre les problèmes de sécurité courants. Toutefois, des conceptions d'application différentes peuvent dépasser un ou plusieurs paramètres d'accélérateur bien que l'application soit par ailleurs sécurisée et qu'elle fonctionne comme prévu. Dans ces cas, vous devez identifier quelles valeurs d'accélérateur sont dépassées et à quel niveau, puis décider du plan d'action approprié pour augmenter le débit d'application.

 En général, lors de l'écriture de l'application et de son débogage, vous affectez à la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> la valeur `true` dans le fichier de configuration ou par programme. Cela indique à WCF de retourner les traces de pile d’exception de service à l’application cliente pour l’affichage. Cette fonctionnalité signale la plupart des exceptions au niveau de l'application de façon à afficher les paramètres de quota qui peuvent être impliqués, si tel est le problème.

 Certaines exceptions se produisent au moment de l'exécution, sous le seuil de visibilité de la couche d'application, et ne sont pas retournées à l'aide de ce mécanisme. Il est possible qu'elles ne soient pas traitées par une implémentation <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> personnalisée. Si vous utilisez un environnement de développement tel que Microsoft Visual Studio, la plupart de ces exceptions sont affichées automatiquement. Toutefois, certaines exceptions peuvent être masquées par des paramètres d’environnement de développement tels que [uniquement mon code](/visualstudio/debugger/just-my-code) Visual Studio.

 Quelles que soient les capacités de votre environnement de développement, vous pouvez utiliser les fonctionnalités de suivi et d’enregistrement des messages WCF pour déboguer toutes les exceptions et optimiser les performances de vos applications. Pour plus d’informations, consultez [utilisation du suivi pour résoudre les problèmes de votre application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problèmes de performances et XmlSerializer

 Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.

> [!NOTE]
> Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.

 L' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaire à partir des assemblys compilés pour l’application. Pour plus d’informations, consultez [Comment : améliorer le temps de démarrage des applications clientes WCF à l’aide de XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problèmes de performances lors de l'hébergement de services WCF sous ASP.NET

Lorsqu'un service WCF est hébergé sous IIS et ASP.NET, les paramètres de configuration d'IIS et ASP.NET peuvent affecter le débit et l'encombrement mémoire du service WCF.  Pour plus d’informations sur les performances de ASP.NET, consultez [amélioration des performances de ASP.net](/previous-versions/msp-n-p/ff647787(v=pandp.10)). Un paramètre qui peut avoir des conséquences inattendues est <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, qui est une propriété de <xref:System.Web.Configuration.ProcessModelSection>. Si votre application dispose d'un nombre fixe ou faible de clients, l'affectation de la valeur 2 à <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> peut fournir une relance de débit sur un ordinateur multiprocesseur dont l'utilisation de l'UC est proche de 100 %. Cette augmentation des performances a un coût : elle entraînera également une augmentation de l'utilisation de la mémoire, ce qui pourrait réduire l'évolutivité.

## <a name="see-also"></a>Voir aussi

- [Administration et diagnostics](./diagnostics/index.md)
- [Données volumineuses et diffusion en continu](./feature-details/large-data-and-streaming.md)
