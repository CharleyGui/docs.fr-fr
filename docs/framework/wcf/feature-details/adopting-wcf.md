---
title: Adoption de Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: a31bd5382e67565bd54272c5c7f400eacd5297d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576536"
---
# <a name="adopt-windows-communication-foundation"></a>Adopter Windows Communication Foundation

Vous pouvez choisir d’utiliser Windows Communication Foundation (WCF) pour le nouveau développement tout en continuant à gérer les applications existantes développées à l’aide de ASP.NET. Étant donné que WCF est le choix le plus approprié pour faciliter la communication avec les applications créées avec l' .NET Framework dans n’importe quel scénario, il peut servir d’outil standard pour la résolution d’un large éventail de problèmes de communication de logiciels d’une manière que ASP.NET ne peut pas.

Les nouvelles applications WCF peuvent être déployées sur les mêmes ordinateurs que les services Web ASP.NET existants. Si les services Web ASP.NET existants utilisent une version de la .NET Framework antérieure à la version 2,0, vous pouvez utiliser l’outil d’inscription ASP.NET IIS pour déployer de manière sélective les .NET Framework 2,0 vers les applications IIS dans lesquelles les nouvelles applications WCF doivent être hébergées. Cet outil est documenté dans [ASP.NET IIS Registration Tool (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))et dispose d’une interface utilisateur intégrée à la console de gestion IIS 6,0.

WCF peut être utilisé pour ajouter de nouvelles fonctionnalités aux services Web ASP.NET existants en ajoutant des services WCF configurés pour s’exécuter en mode de compatibilité ASP.NET pour les applications de service Web ASP.NET existantes dans IIS. En raison du mode de compatibilité de ASP.NET, le code pour les nouveaux services WCF peut accéder et mettre à jour les mêmes informations d’état de l’application que le code ASP.NET préexistant, à l’aide de la <xref:System.Web.HttpContext> classe. Les applications peuvent également partager les mêmes bibliothèques de classes.

Les clients WCF peuvent utiliser les services Web ASP.NET. Les services WCF configurés avec le <xref:System.ServiceModel.BasicHttpBinding> peuvent être utilisés par les clients du service Web ASP.net. Les services Web ASP.NET peuvent coexister avec les applications WCF, et WCF peut même être utilisé pour ajouter des fonctionnalités aux services Web ASP.NET existants. Compte tenu de toutes les façons dont les services Web WCF et ASP.NET peuvent être utilisés ensemble, vous souhaiterez peut-être migrer les services Web ASP.NET vers WCF uniquement si vous avez besoin de fonctionnalités fournies par WCF et non pas de services Web ASP.NET.

Même dans les rares cas où il est nécessaire, la migration du code d’une technologie vers une autre est rarement l’approche correcte. La raison de l’adoption de la nouvelle technologie est de répondre à de nouvelles exigences qui ne peuvent pas être satisfaites avec la technologie antérieure, et dans ce cas, la bonne chose à faire est de concevoir une nouvelle solution pour répondre à l’ensemble des exigences récemment développées. La nouvelle conception bénéficie de votre expérience avec le système existant et du savoir-faire acquis depuis que ce système a été conçu. La nouvelle conception peut également profiter de l'intégralité des possibilités offertes par les nouvelles technologies plutôt que de reproduire l'ancienne conception sur la nouvelle plate-forme. Après le prototypage des éléments clés de la nouvelle conception, il devient plus facile de réutiliser le code du système existant dans le nouveau.

## <a name="see-also"></a>Voir aussi

- [Comment : récupérer des métadonnées et implémenter un service conforme](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
