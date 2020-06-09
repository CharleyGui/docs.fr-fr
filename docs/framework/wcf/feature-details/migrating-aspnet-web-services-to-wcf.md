---
title: Migration des services Web ASP.NET vers WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: fa707a4246d5bc9940417072c098b2973140f878
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598799"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migration des services Web ASP.NET vers WCF
ASP.NET fournit des bibliothèques de classes .NET Framework et des outils permettant de générer des services Web, ainsi que des fonctionnalités d'hébergement des services dans les services IIS (Internet Information Services). Windows Communication Foundation (WCF) fournit .NET Framework bibliothèques de classes, des outils et des fonctionnalités d’hébergement pour permettre aux entités logicielles de communiquer à l’aide de n’importe quel protocole, y compris ceux utilisés par les services Web.  La migration des services Web ASP.NET vers WCF permet à vos applications de tirer parti des nouvelles fonctionnalités et améliorations propres à WCF.  
  
 WCF présente plusieurs avantages importants par rapport aux services Web ASP.NET. Alors que les outils de services Web ASP.NET sont uniquement destinés à la création de services Web, WCF fournit des outils qui peuvent être utilisés lorsque des entités logicielles doivent être établies pour communiquer entre elles. Cela réduira le nombre de technologies que les développeurs sont tenus de connaître pour s'adapter aux différents scénarios de communication logicielle, ce qui, en conséquence, réduira le coût des ressources de développement logiciel, ainsi que le délai de réalisation des projets de développement logiciel.  
  
 Même pour les projets de développement de services Web, WCF prend en charge davantage de protocoles de service Web que la prise en charge de services Web ASP.NET. Ces protocoles supplémentaires offrent des solutions plus sophistiquées impliquant, entre autres, des transactions et des sessions fiables.  
  
 WCF prend en charge davantage de protocoles pour le transport des messages que les services Web ASP.NET. Les services Web ASP.NET prennent uniquement en charge l'envoi de messages à l'aide du protocole HTTP (Hypertext Transfer Protocol). WCF prend en charge l’envoi de messages à l’aide de HTTP, ainsi que le protocole TCP (Transmission Control Protocol), les canaux nommés et Microsoft Message Queuing (MSMQ). Plus important, WCF peut être étendu pour prendre en charge des protocoles de transport supplémentaires. Par conséquent, les logiciels développés à l’aide de WCF peuvent être adaptés pour fonctionner avec une grande variété d’autres logiciels, augmentant ainsi le retour sur investissement potentiel.  
  
 WCF offre des fonctionnalités beaucoup plus riches pour le déploiement et la gestion d’applications que les services Web ASP.NET. En plus d’un système de configuration, qui ASP.NET également, WCF offre un éditeur de configuration, un suivi des activités des expéditeurs aux récepteurs et un nombre quelconque d’intermédiaires, une visionneuse de trace, la journalisation des messages, un grand nombre de compteurs de performances et la prise en charge de Windows Management Instrumentation.  
  
 Compte tenu de ces avantages potentiels de WCF par rapport aux services Web ASP.NET, si vous utilisez ou que vous envisagez d’utiliser les services Web ASP.NET, vous avez plusieurs options :  
  
- Continuez à utiliser les services Web ASP.NET et les avantages offerts par WCF.  
  
- Continuez à utiliser les services Web ASP.NET dans le but d’adopter WCF à un moment ultérieur. Les rubriques de cette section expliquent comment maximiser les prospects pour pouvoir utiliser les nouvelles applications de service Web ASP.NET avec les futures applications WCF. Les rubriques de cette section expliquent également comment créer de nouveaux services Web ASP.NET afin de faciliter leur migration vers WCF. Toutefois, si la sécurisation des services est importante, ou si des assurances de fiabilité ou de transaction sont requises, ou si des installations de gestion personnalisées doivent être construites, il est préférable d’adopter WCF. WCF est conçu pour de tels scénarios.  
  
- Adoptez WCF pour un nouveau développement, tout en continuant à gérer vos applications de service Web ASP.NET existantes. Ce choix est très probablement le plus optimal. Il offre les avantages de WCF, tout en permettant de modifier les applications existantes pour l’utiliser. Dans ce scénario, les nouvelles applications WCF peuvent coexister avec les applications ASP.NET existantes. Les nouvelles applications WCF seront en mesure d’utiliser les services Web ASP.NET existants, et WCF peut être utilisé pour programmer de nouvelles fonctionnalités opérationnelles dans les applications ASP.NET existantes en utilisant le mode de compatibilité ASP.NET WCF.  
  
- Adoptez WCF et migrez les applications de service Web ASP.NET existantes vers WCF. Vous pouvez choisir cette option pour améliorer les applications existantes avec les fonctionnalités fournies par WCF, ou pour reproduire les fonctionnalités des services Web ASP.NET existants dans de nouvelles applications WCF plus puissantes.  
  
> [!NOTE]
> Une attention particulière doit être prise si un service WCF est hébergé par IIS 5. x et que ASP.NET est désinstallé. Lorsqu’un service WCF est hébergé par IIS 5. x, le code du service peut être demandé si ASP.NET est désinstallé. Quand ASP.NET est désinstallé sur un système d’exploitation qui exécute IIS 5. x et que WCF est désinstallé, un fichier avec l’extension. svc est considéré comme un fichier texte et le contenu, y compris tout code source, est retourné au demandeur.  
  
 Cette section décrit ces options en détail, compare les services Web ASP.NET à WCF et fournit des instructions sur la migration de votre code de services Web ASP.NET vers WCF.  
  
## <a name="see-also"></a>Voir aussi

- [Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration](anticipating-adopting-wcf-migration.md)
- [Anticipation de l'adoption de Windows Communication Foundation : faciliter l'intégration future](anticipating-adopting-the-wcf-easing-future-integration.md)
- [Adoption de Windows Communication Foundation](adopting-wcf.md)
- [Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Comparaison des services Web ASP.NET et de WCF du point de vue du développement](comparing-aspnet-web-services-to-wcf-based-on-development.md)
