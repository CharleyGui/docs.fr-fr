---
title: Extension du système de métadonnées
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7113120a3cde6b4e6a7eb1d329da625e25996952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272981"
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="4622a-102">Extension du système de métadonnées</span><span class="sxs-lookup"><span data-stu-id="4622a-102">Extending the Metadata System</span></span>

<span data-ttu-id="4622a-103">Le système de métadonnées Windows Communication Foundation (WCF) est un groupe de classes et d’interfaces qui représentent les métadonnées requises pour implémenter des applications basées sur les services.</span><span class="sxs-lookup"><span data-stu-id="4622a-103">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="4622a-104">Modifiez ou étendez les classes ou implémentez et configurez les interfaces pour exporter et importer des métadonnées personnalisées telles que les extensions WSDL (Web Services Description Language) ou des assertions WS-PolicyAttachments personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4622a-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4622a-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4622a-105">In This Section</span></span>  

 [<span data-ttu-id="4622a-106">Exportation de métadonnées personnalisées pour une extension WCF</span><span class="sxs-lookup"><span data-stu-id="4622a-106">Exporting Custom Metadata for a WCF Extension</span></span>](exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="4622a-107">Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> pour incorporer des assertions de stratégie personnalisées dans des documents WSDL.</span><span class="sxs-lookup"><span data-stu-id="4622a-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="4622a-108">Importation de métadonnées personnalisées pour une extension WCF</span><span class="sxs-lookup"><span data-stu-id="4622a-108">Importing Custom Metadata for a WCF Extension</span></span>](importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="4622a-109">Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> pour lire et répondre à des assertions de stratégie personnalisées dans des documents WSDL.</span><span class="sxs-lookup"><span data-stu-id="4622a-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="4622a-110">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="4622a-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="4622a-111">Décrit comment échanger des métadonnées sur des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4622a-111">Describes how to exchange metadata over custom bindings.</span></span>
