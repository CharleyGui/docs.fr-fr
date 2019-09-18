---
title: API et bibliothèques de classes supplémentaires
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053245"
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

La .NET Framework évolue constamment. Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, les nouvelles fonctionnalités sont publiées hors bande (OOB). Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.  
  
En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework. Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les encodages de pages de codes disponibles pour les applications UWP développées à l’aide de l' .NET Framework. Cette rubrique liste également ces bibliothèques.  
  
## <a name="oob-projects"></a>Projets OOB
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer. |
| <xref:System.Net.Http.WinHttpHandler> | Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows. |
| <xref:System.Numerics> | Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel. |  

## <a name="platform-specific-libraries"></a>Bibliothèques propres à une plateforme
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Étend la <xref:System.Text.EncodingProvider> classe pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle. |  
  
## <a name="private-apis"></a>API privées  

Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.  
  
| Nom de l'API |
| -------- |
| [Classe System .net. Connection](connection.md) |
| [Champ System .net. Connection.\_m WriteList](m_writelist.md) |
| [Classe System .net. ConnectionGroup](connectiongroup.md) |
| [Champ System .net. ConnectionGroup.\_m ConnectionList](m_connectionlist.md) |
| [Classe System .net. CoreResponseData](coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md) |
| [Champ StatusCode de System .net.\_CoreResponseData. m](coreresponsedata_m_statuscode.md) |
| [System .net. HttpWebRequest. \_Champ AutoRedirects](_autoredirects.md) |
| [System .net. HttpWebRequest. \_Champ CoreResponse](httpwebrequest__coreresponse.md) |
| [System .net. HttpWebRequest. \_HttpResponse (champ)](_httpresponse.md) |
| [Champ System .net. ServicePoint.\_m ConnectionGroupList](m_connectiongrouplist.md) |
| [Champ System .net. ServicePointManager.\_s ServicePointTable](s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md) |
| [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Voir aussi

- [Versions finales hors plage de .NET Framework](../get-started/the-net-framework-and-out-of-band-releases.md)
