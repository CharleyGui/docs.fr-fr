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
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155906"
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

Le cadre .NET est en constante évolution. Afin d’améliorer le développement multiplateforme et d’introduire de nouvelles fonctionnalités tôt, de nouvelles fonctionnalités sont libérées hors bande (OOB). Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.  
  
En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework. Par exemple, <xref:System.Text.CodePagesEncodingProvider> la classe met à la disposition des applications UWP des encodages de pages de code développées à l’aide du cadre .NET. Cette rubrique liste également ces bibliothèques.  
  
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
| <xref:System.Text.CodePagesEncodingProvider> | Étend <xref:System.Text.EncodingProvider> la classe pour mettre à la disposition des applications qui ciblent la plate-forme Windows universelle. |  
  
## <a name="private-apis"></a>API privées  

Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.  
  
* [Microsoft.SqlServer.Server.SmiOrderProperty.Item Propriété](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Méthode System.Exception.PrepForRemoting](system.exception.prepforremoting.md)
* [System.Data.SqlTypes.SqlChars.Stream Propriété](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Constructor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System.Data.SqlTypes.SqlStreamChars.CanSeek Propriété](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Propriété System.Data.SqlTypes.SqlStreamChars.IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System.Data.SqlTypes.SqlStreamChars.Length Propriété](system.data.sqltypes.sqlstreamchars.length.md)
* [System.Data.SqlTypes.SqlStreamChars.Fermer la méthode](system.data.sqltypes.sqlstreamchars.close.md)
* [Méthode System.Data.SqlTypes.SqlStreamChars.Dispose](system.data.sqltypes.sqlstreamchars.dispose.md)
* [Méthode System.Data.SqlTypes.SqlStreamChars.Flush Méthode](system.data.sqltypes.sqlstreamchars.flush.md)
* [System.Data.SqlTypes.SqlStreamChars.Read Méthode](system.data.sqltypes.sqlstreamchars.read.md)
* [System.Data.SqlTypes.SqlStreamChars.Seek Méthode](system.data.sqltypes.sqlstreamchars.seek.md)
* [Méthode System.Data.SqlTypes.SqlStreamChars.SetLength](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System.Data.SqlTypes.SqlStreamChars.Méthode d’écriture](system.data.sqltypes.sqlstreamchars.write.md)
* [System.io.MemoryStream.InternalGetOriginAndLength Méthode](system.io.memorystream.internalgetoriginandlength.md)
* [Classe System.Net.Connection](connection.md)
* [System.Net.Connection.m\_Champ WriteList](m_writelist.md)
* [Classe System.Net.ConnectionGroup](connectiongroup.md)
* [Champ System.Net.ConnectionGroup.m\_ConnectionList](m_connectionlist.md)
* [Propriété System.Net.ConnectStream.Connection](system.net.connectstream.connection.md)
* [Classe System.Net.CoreResponseData](coreresponsedata.md)
* [System.Net.CoreResponseData.m\_ResponseHeaders Field (en)](coreresponsedata_m_responseheaders.md)
* [System.Net.CoreResponseData.m\_StatusCode Field (en)](coreresponsedata_m_statuscode.md)
* [System.Net.httpWebRequest. \_Champ AutoRedirects](_autoredirects.md)
* [System.Net.httpWebRequest. \_Champ CoreResponse](httpwebrequest__coreresponse.md)
* [System.Net.httpWebRequest. \_Champ httpResponse](_httpresponse.md)
* [System.Net.PooledStream.NetworkStream Propriété](system.net.pooledstream.networkstream.md)
* [Classe System.Net.RtcState](system.net.rtcstate.md)
* [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md)
* [System.Net.ServicePointManager.s\_ServicePointTable Field (en anglais)](s_servicepointtable.md)
* [Terrain System.Net.TlsStream.m_Worker](system.net.tlsstream.m_worker.md)
* [System.Net.Security.SslState.SslProtocol Propriété](system.net.security.sslstate.sslprotocol.md)
* [System.ServiceModel.Channels.Message.BodyToString Méthode](system.servicemodel.channels.message.bodytostring.md)
* [System.ServiceModel.Channels.Message.WriteStartHeaders Méthode](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Classe System.Windows.Forms.Design.DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [System.Windows.Forms.Design.DataMemberListEditor Classe](datamemberlisteditor-class.md)
* [System.Xml.XmlReader.CreateSqlReader Méthode](system.xml.xmlreader.createsqlreader.md)
* [Adodb. Interface de connexion](adodb.connection.md)
* [Adodb. ÉvénementReason Enum](adodb.eventreasonenum.md)
* [Adodb. EventStatus Enum](adodb.eventstatusenum.md)
* [stdole. DISPPARAMS Structure](stdole.dispparams.md)
* [stdole. EXCEPINFO Structure](stdole.excepinfo.md)
* [stdole. Propriété IFont.Name](stdole.ifont.name.md)
* [stdole. IFontDisp Interface](stdole.ifontdisp.md)
* [stdole. Propriété IPicture.Handle](stdole.ipicture.handle.md)
* [stdole. Propriété IPictureDisp.Handle](stdole.ipicturedisp.handle.md)
* [stdole. StdFont Interface](stdole.stdfont.md)
* [stdole. StdPicture Interface](stdole.stdpicture.md)
  
## <a name="see-also"></a>Voir aussi

* [Versions finales hors plage de .NET Framework](../get-started/the-net-framework-and-out-of-band-releases.md)
