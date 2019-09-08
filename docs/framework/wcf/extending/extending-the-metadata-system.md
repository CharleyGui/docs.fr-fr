---
title: Extension du système de métadonnées
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795718"
---
# <a name="extending-the-metadata-system"></a>Extension du système de métadonnées
Le système de métadonnées Windows Communication Foundation (WCF) est un groupe de classes et d’interfaces qui représentent les métadonnées requises pour implémenter des applications basées sur les services. Modifiez ou étendez les classes ou implémentez et configurez les interfaces pour exporter et importer des métadonnées personnalisées telles que les extensions WSDL (Web Services Description Language) ou des assertions WS-PolicyAttachments personnalisées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exportation de métadonnées personnalisées pour une extension WCF](exporting-custom-metadata-for-a-wcf-extension.md)  
 Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> pour incorporer des assertions de stratégie personnalisées dans des documents WSDL.  
  
 [Importation de métadonnées personnalisées pour une extension WCF](importing-custom-metadata-for-a-wcf-extension.md)  
 Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> pour lire et répondre à des assertions de stratégie personnalisées dans des documents WSDL.  
  
 [Publication et récupération de métadonnées sur une liaison personnalisée](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Décrit comment échanger des métadonnées sur des liaisons personnalisées.
