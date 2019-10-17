---
title: API et bibliothèques de classes supplémentaires
ms.date: 10/09/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: b869ca2f5e17db9a204a8b757b5e24ebb209d7c5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395658"
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

La .NET Framework évolue constamment. Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, les nouvelles fonctionnalités sont publiées hors bande (OOB). Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.  
  
En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework. Par exemple, la classe <xref:System.Text.CodePagesEncodingProvider> met les encodages de pages de codes à la disposition des applications UWP développées à l’aide du .NET Framework. Cette rubrique liste également ces bibliothèques.  
  
## <a name="oob-projects"></a>Projets OOB
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer. |
| <xref:System.Net.Http.WinHttpHandler> | Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows. |
| <xref:System.Numerics> | Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel. |  

## <a name="platform-specific-libraries"></a>Bibliothèques propres à une plateforme
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Étend la classe <xref:System.Text.EncodingProvider> pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle. |  
  
## <a name="private-apis"></a>API privées  

Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.  
  
* [Microsoft. SqlServer. Server. SmiOrderProperty. Item, propriété](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Méthode System. exception. PrepForRemoting](system.exception.prepforremoting.md)
* [System. Data. SqlTypes. SqlChars. Stream, propriété](system.data.sqltypes.sqlchars.stream.md)
* [Constructeur System. Data. SqlTypes. SqlStreamChars](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System. Data. SqlTypes. SqlStreamChars. CanSeek, propriété](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Propriété System. Data. SqlTypes. SqlStreamChars. IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [Propriété System. Data. SqlTypes. SqlStreamChars. Length](system.data.sqltypes.sqlstreamchars.length.md)
* [System. Data. SqlTypes. SqlStreamChars. Close, méthode](system.data.sqltypes.sqlstreamchars.close.md)
* [System. Data. SqlTypes. SqlStreamChars. dispose, méthode](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System. Data. SqlTypes. SqlStreamChars. Flush, méthode](system.data.sqltypes.sqlstreamchars.flush.md)
* [System. Data. SqlTypes. SqlStreamChars. Read, méthode](system.data.sqltypes.sqlstreamchars.read.md)
* [System. Data. SqlTypes. SqlStreamChars. Seek, méthode](system.data.sqltypes.sqlstreamchars.seek.md)
* [System. Data. SqlTypes. SqlStreamChars. SetLength, méthode](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System. Data. SqlTypes. SqlStreamChars. Write, méthode](system.data.sqltypes.sqlstreamchars.write.md)
* [Classe System .net. Connection](connection.md)
* [System .net. Connection. m @ no__t-champ 1WriteList](m_writelist.md)
* [Classe System .net. ConnectionGroup](connectiongroup.md)
* [System .net. ConnectionGroup. m @ no__t-1ConnectionList Field](m_connectionlist.md)
* [Classe System .net. CoreResponseData](coreresponsedata.md)
* [System .net. CoreResponseData. m @ no__t-1ResponseHeaders Field](coreresponsedata_m_responseheaders.md)
* [System .net. CoreResponseData. m @ no__t-1StatusCode Field](coreresponsedata_m_statuscode.md)
* [System .net. HttpWebRequest. @no__t-champ 1AutoRedirects](_autoredirects.md)
* [System .net. HttpWebRequest. @no__t-champ 1CoreResponse](httpwebrequest__coreresponse.md)
* [System .net. HttpWebRequest. @no__t-champ 1HttpResponse](_httpresponse.md)
* [Champ System .net. ServicePoint. m @ no__t-1ConnectionGroupList](m_connectiongrouplist.md)
* [System .net. ServicePointManager. s @ no__t-champ 1ServicePointTable](s_servicepointtable.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s @ no__t-1isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md)
* [ADODB. Interface de connexion](adodb.connection.md)
* [ADODB. Énumération EventReason](adodb.eventreasonenum.md)
* [ADODB. Énumération EventStatus](adodb.eventstatusenum.md)
* [stdole. DISPPARAMS, structure](stdole.dispparams.md)
* [stdole. EXCEPINFO, structure](stdole.excepinfo.md)
* [stdole. Propriété IFont.Name](stdole.ifont.name.md)
* [stdole. IFontDisp, interface](stdole.ifontdisp.md)
* [stdole. IPicture. handle, propriété](stdole.ipicture.handle.md)
* [stdole. IPictureDisp. handle (propriété)](stdole.ipicturedisp.handle.md)
* [stdole. StdFont (interface)](stdole.stdfont.md)
* [stdole. StdPicture, interface](stdole.stdpicture.md)
  
## <a name="see-also"></a>Voir aussi

* [Versions finales hors plage de .NET Framework](../get-started/the-net-framework-and-out-of-band-releases.md)
