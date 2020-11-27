---
title: Extensibilité des métadonnées
ms.date: 03/30/2017
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
ms.openlocfilehash: fb37e33026a5f99bfa033f04eea0bb85fbbe65c7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294324"
---
# <a name="metadata-extensibility"></a>Extensibilité des métadonnées

Cette section contient des exemples qui illustrent des métadonnées personnalisées.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Point de terminaison de métadonnées sécurisé personnalisée](custom-secure-metadata-endpoint.md)  
 Montre comment implémenter un service avec un point de terminaison de métadonnées sécurisé qui utilise l’une des liaisons d’échange de métadonnées non-et comment configurer [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ou des clients pour extraire les métadonnées d’un tel point de terminaison de métadonnées.  
  
 [Publication WSDL personnalisée](custom-wsdl-publication.md)  
 Montre comment implémenter un <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> sur un attribut <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> personnalisé pour exporter les propriétés de l'attribut en tant qu'annotations WSDL, entre autres fonctionnalités.
