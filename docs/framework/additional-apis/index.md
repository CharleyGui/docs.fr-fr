---
title: API et bibliothèques de classes supplémentaires
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 3a5134aa4407598e223fd2c938bfaac02cf9178c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215530"
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

La .NET Framework évolue constamment. Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, les nouvelles fonctionnalités sont publiées hors bande (OOB). Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.  
  
En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework. Par exemple, la classe <xref:System.Text.CodePagesEncodingProvider> rend les encodages de pages de codes disponibles pour les applications UWP développées à l’aide du .NET Framework. Cette rubrique liste également ces bibliothèques.  
  
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
* [Méthode System. IO. MemoryStream. InternalGetOriginAndLength](system.io.memorystream.internalgetoriginandlength.md)
* [Classe System .net. Connection](connection.md)
* [System .net. Connection. m\_WriteList champ)](m_writelist.md)
* [Classe System .net. ConnectionGroup](connectiongroup.md)
* [Champ System .net. ConnectionGroup. m\_ConnectionList](m_connectionlist.md)
* [System .net. ConnectStream. Connection, propriété](system.net.connectstream.connection.md)
* [Classe System .net. CoreResponseData](coreresponsedata.md)
* [Champ System .net. CoreResponseData. m\_ResponseHeaders](coreresponsedata_m_responseheaders.md)
* [System .net. CoreResponseData. m\_champ StatusCode](coreresponsedata_m_statuscode.md)
* [Champ AutoRedirects de System .net. HttpWebRequest.\_](_autoredirects.md)
* [Champ CoreResponse de System .net. HttpWebRequest.\_](httpwebrequest__coreresponse.md)
* [Champ HttpResponse System .net. HttpWebRequest.\_](_httpresponse.md)
* [System .net. PooledStream. NetworkStream, propriété](system.net.pooledstream.networkstream.md)
* [Classe System .net. RtcState](system.net.rtcstate.md)
* [Champ System .net. ServicePoint. m\_ConnectionGroupList](m_connectiongrouplist.md)
* [System .net. ServicePointManager. s\_champ ServicePointTable](s_servicepointtable.md)
* [Champ System .net. TlsStream. m_Worker](system.net.tlsstream.m_worker.md)
* [System .net. Security. SslState. SslProtocol, propriété](system.net.security.sslstate.sslprotocol.md)
* [System. ServiceModel. Channels. message. BodyToString, méthode](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. message. WriteStartHeaders, méthode](system.servicemodel.channels.message.writestartheaders.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s\_champ isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md)
* [System. Xml. XmlReader. CreateSqlReader, méthode](system.xml.xmlreader.createsqlreader.md)
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
