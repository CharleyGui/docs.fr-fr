---
title: API et bibliothèques de classes supplémentaires
description: Explorez les bibliothèques de classes et les API supplémentaires dans .NET, y compris les projets hors bande (OOB), les bibliothèques spécifiques à la plateforme et les API privées.
ms.date: 06/12/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 0b888d2f0e80685ba993682b2f3067cf8aee15bc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989744"
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

Cet article répertorie les .NET Framework API qui ont été publiées hors bande, qui ciblent une plateforme spécifique ou qui sont des types privés ou internes.

## <a name="oob-projects"></a>Projets OOB

Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, certaines fonctionnalités de .NET Framework ont été publiées hors bande (OOB).

| Project | Description |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer. |
| <xref:System.Net.Http.WinHttpHandler> | Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows. |
| <xref:System.Numerics> | Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.|
| <xref:System.Threading.Tasks.Dataflow> | La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel. |  

## <a name="platform-specific-libraries"></a>Bibliothèques propres à une plateforme

Certaines bibliothèques ciblent des plateformes spécifiques. Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les encodages de pages de codes disponibles pour les applications UWP développées à l’aide de .NET Framework.
  
| Project | Description |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Étend la <xref:System.Text.EncodingProvider> classe pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle. |  
  
## <a name="private-apis"></a>API privées  

Ces API prennent en charge l’infrastructure du produit et ne sont pas conçues ou prises en charge pour être utilisées directement à partir de votre code.  
  
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
* [Méthode System. IO. MemoryStream. InternalGetOriginAndLength](system.io.memorystream.internalgetoriginandlength.md)
* [Classe System .net. ComNetOS](system.net.comnetos.md)
* [Classe System .net. Connection](connection.md)
* [Champ System .net. Connection. m \_ WriteList](m_writelist.md)
* [Classe System .net. ConnectionGroup](connectiongroup.md)
* [Champ System .net. ConnectionGroup. m \_ ConnectionList](m_connectionlist.md)
* [System .net. ConnectStream. Connection, propriété](system.net.connectstream.connection.md)
* [Classe System .net. CoreResponseData](coreresponsedata.md)
* [Champ System .net. CoreResponseData. m \_ responseHeaders](coreresponsedata_m_responseheaders.md)
* [Champ StatusCode de System .net. CoreResponseData. m \_](coreresponsedata_m_statuscode.md)
* [Classe System .net. ExceptionHelper](system.net.exceptionhelper.md)
* [Classe System .net. HttpStatusDescription](system.net.httpstatusdescription.md)
* [System .net. HttpWebRequest. \_ Champ AutoRedirects](_autoredirects.md)
* [System .net. HttpWebRequest. \_ Champ CoreResponse](httpwebrequest__coreresponse.md)
* [System .net. HttpWebRequest. \_ HttpResponse (champ)](_httpresponse.md)
* [Classe System .net. Logging](system.net.logging.md)
* [Classe System .net. mail. MailAddressParser](system.net.mail.mailaddressparser.md)
* [Classe System .net. mail. QuotedPairReader](system.net.mail.quotedpairreader.md)
* [System .net. MIME. MailBnfHelper, classe](system.net.mime.mailbnfhelper.md)
* [System .net. PooledStream. NetworkStream, propriété](system.net.pooledstream.networkstream.md)
* [Classe System .net. RtcState](system.net.rtcstate.md)
* [System .net. Security. SslState. SslProtocol, propriété](system.net.security.sslstate.sslprotocol.md)
* [Champ System .net. ServicePoint. m \_ ConnectionGroupList](m_connectiongrouplist.md)
* [System .net. ServicePointManager. CloseConnectionGroups, méthode](system.net.servicepointmanager.closeconnectiongroups.md)
* [Champ System .net. ServicePointManager. s \_ ServicePointTable](s_servicepointtable.md)
* [Champ System .net. TlsStream. m_Worker](system.net.tlsstream.m_worker.md)
* [Classe System .net. UnsafeNclNativeMethods](system.net.unsafenclnativemethods.md)
* [System .net. WebHeaderCollection. AddInternal, méthode](system.net.webheadercollection.addinternal.md)
* [System. ServiceModel. Channels. message. BodyToString, méthode](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. message. WriteStartHeaders, méthode](system.servicemodel.channels.message.writestartheaders.md)
* [Champ System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md)
* [MéthodeSystem.Xml.XmlReader. CreateSqlReader](system.xml.xmlreader.createsqlreader.md)
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

* [Versions .NET Framework et hors plage](../get-started/the-net-framework-and-out-of-band-releases.md)
