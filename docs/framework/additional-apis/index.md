---
title: API et bibliothèques de classes supplémentaires
description: Explorez les bibliothèques de classes et les API supplémentaires dans .NET, y compris les projets hors bande (OOB), les bibliothèques spécifiques à la plateforme et les API privées.
ms.date: 08/11/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: c6404df5d4f0be381bc0a9c1924fcf82cf078306
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88075473"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="2ed95-103">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2ed95-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="2ed95-104">Cet article répertorie les .NET Framework API qui ont été publiées hors bande, qui ciblent une plateforme spécifique ou qui sont des types privés ou internes.</span><span class="sxs-lookup"><span data-stu-id="2ed95-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="2ed95-105">Projets OOB</span><span class="sxs-lookup"><span data-stu-id="2ed95-105">OOB projects</span></span>

<span data-ttu-id="2ed95-106">Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, certaines fonctionnalités de .NET Framework ont été publiées hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="2ed95-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="2ed95-107">Projet</span><span class="sxs-lookup"><span data-stu-id="2ed95-107">Project</span></span> | <span data-ttu-id="2ed95-108">Description</span><span class="sxs-lookup"><span data-stu-id="2ed95-108">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="2ed95-109">Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer.</span><span class="sxs-lookup"><span data-stu-id="2ed95-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="2ed95-110">Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows.</span><span class="sxs-lookup"><span data-stu-id="2ed95-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="2ed95-111">Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.</span><span class="sxs-lookup"><span data-stu-id="2ed95-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="2ed95-112">La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="2ed95-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="2ed95-113">Bibliothèques propres à une plateforme</span><span class="sxs-lookup"><span data-stu-id="2ed95-113">Platform-specific libraries</span></span>

<span data-ttu-id="2ed95-114">Certaines bibliothèques ciblent des plateformes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2ed95-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="2ed95-115">Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les encodages de pages de codes disponibles pour les applications UWP développées à l’aide de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ed95-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>
  
| <span data-ttu-id="2ed95-116">Projet</span><span class="sxs-lookup"><span data-stu-id="2ed95-116">Project</span></span> | <span data-ttu-id="2ed95-117">Description</span><span class="sxs-lookup"><span data-stu-id="2ed95-117">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="2ed95-118">Étend la <xref:System.Text.EncodingProvider> classe pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="2ed95-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="2ed95-119">API privées</span><span class="sxs-lookup"><span data-stu-id="2ed95-119">Private APIs</span></span>  

<span data-ttu-id="2ed95-120">Ces API prennent en charge l’infrastructure du produit et ne sont pas conçues ou prises en charge pour être utilisées directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2ed95-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="2ed95-121">Microsoft. SqlServer. Server. SmiOrderProperty. Item, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="2ed95-122">Méthode System. exception. PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="2ed95-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="2ed95-123">System. Data. SqlTypes. SqlChars. Stream, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="2ed95-124">Constructeur System. Data. SqlTypes. SqlStreamChars</span><span class="sxs-lookup"><span data-stu-id="2ed95-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="2ed95-125">System. Data. SqlTypes. SqlStreamChars. CanSeek, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="2ed95-126">Propriété System. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="2ed95-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="2ed95-127">Propriété System. Data. SqlTypes. SqlStreamChars. Length</span><span class="sxs-lookup"><span data-stu-id="2ed95-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="2ed95-128">System. Data. SqlTypes. SqlStreamChars. Close, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="2ed95-129">System. Data. SqlTypes. SqlStreamChars. dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="2ed95-130">System. Data. SqlTypes. SqlStreamChars. Flush, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="2ed95-131">System. Data. SqlTypes. SqlStreamChars. Read, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="2ed95-132">System. Data. SqlTypes. SqlStreamChars. Seek, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="2ed95-133">System. Data. SqlTypes. SqlStreamChars. SetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="2ed95-134">System. Data. SqlTypes. SqlStreamChars. Write, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="2ed95-135">Méthode System. IO. MemoryStream. InternalGetOriginAndLength</span><span class="sxs-lookup"><span data-stu-id="2ed95-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="2ed95-136">Classe System .net. ComNetOS</span><span class="sxs-lookup"><span data-stu-id="2ed95-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="2ed95-137">Classe System .net. Connection</span><span class="sxs-lookup"><span data-stu-id="2ed95-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="2ed95-138">Champ System .net. Connection. m \_ WriteList</span><span class="sxs-lookup"><span data-stu-id="2ed95-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="2ed95-139">Classe System .net. ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="2ed95-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="2ed95-140">Champ System .net. ConnectionGroup. m \_ ConnectionList</span><span class="sxs-lookup"><span data-stu-id="2ed95-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="2ed95-141">System .net. ConnectStream. Connection, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="2ed95-142">Classe System .net. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="2ed95-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="2ed95-143">Champ System .net. CoreResponseData. m \_ responseHeaders</span><span class="sxs-lookup"><span data-stu-id="2ed95-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="2ed95-144">Champ StatusCode de System .net. CoreResponseData. m \_</span><span class="sxs-lookup"><span data-stu-id="2ed95-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="2ed95-145">Classe System .net. ExceptionHelper</span><span class="sxs-lookup"><span data-stu-id="2ed95-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="2ed95-146">Classe System .net. HttpStatusDescription</span><span class="sxs-lookup"><span data-stu-id="2ed95-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="2ed95-147">System .net. HttpWebRequest. \_ Champ AutoRedirects</span><span class="sxs-lookup"><span data-stu-id="2ed95-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="2ed95-148">System .net. HttpWebRequest. \_ Champ CoreResponse</span><span class="sxs-lookup"><span data-stu-id="2ed95-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="2ed95-149">System .net. HttpWebRequest. \_ HttpResponse (champ)</span><span class="sxs-lookup"><span data-stu-id="2ed95-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="2ed95-150">Classe System .net. Logging</span><span class="sxs-lookup"><span data-stu-id="2ed95-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="2ed95-151">Classe System .net. mail. MailAddressParser</span><span class="sxs-lookup"><span data-stu-id="2ed95-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="2ed95-152">Classe System .net. mail. QuotedPairReader</span><span class="sxs-lookup"><span data-stu-id="2ed95-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="2ed95-153">System .net. MIME. MailBnfHelper, classe</span><span class="sxs-lookup"><span data-stu-id="2ed95-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="2ed95-154">System .net. PooledStream. NetworkStream, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="2ed95-155">Classe System .net. RtcState</span><span class="sxs-lookup"><span data-stu-id="2ed95-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="2ed95-156">System .net. Security. SslState. SslProtocol, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="2ed95-157">Champ System .net. ServicePoint. m \_ ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="2ed95-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="2ed95-158">System .net. ServicePointManager. CloseConnectionGroups, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="2ed95-159">Champ System .net. ServicePointManager. s \_ ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="2ed95-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="2ed95-160">Champ System .net. TlsStream. m_Worker</span><span class="sxs-lookup"><span data-stu-id="2ed95-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="2ed95-161">Classe System .net. UnsafeNclNativeMethods</span><span class="sxs-lookup"><span data-stu-id="2ed95-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="2ed95-162">System .net. WebHeaderCollection. AddInternal, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="2ed95-163">System. ServiceModel. Channels. message. BodyToString, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="2ed95-164">System. ServiceModel. Channels. message. WriteStartHeaders, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed95-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="2ed95-165">System. Web. Compilation. ControlBuilderInterceptor, classe</span><span class="sxs-lookup"><span data-stu-id="2ed95-165">System.Web.Compilation.ControlBuilderInterceptor class</span></span>](controlbuilderinterceptor-class.md)
* [<span data-ttu-id="2ed95-166">Champ System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="2ed95-166">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="2ed95-167">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="2ed95-167">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="2ed95-168">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="2ed95-168">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="2ed95-169">MéthodeSystem.Xml.XmlReader. CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="2ed95-169">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="2ed95-170">ADODB. Interface de connexion</span><span class="sxs-lookup"><span data-stu-id="2ed95-170">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="2ed95-171">ADODB. Énumération EventReason</span><span class="sxs-lookup"><span data-stu-id="2ed95-171">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="2ed95-172">ADODB. Énumération EventStatus</span><span class="sxs-lookup"><span data-stu-id="2ed95-172">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="2ed95-173">stdole. DISPPARAMS, structure</span><span class="sxs-lookup"><span data-stu-id="2ed95-173">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="2ed95-174">stdole. EXCEPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="2ed95-174">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="2ed95-175">stdole. Propriété IFont.Name</span><span class="sxs-lookup"><span data-stu-id="2ed95-175">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="2ed95-176">stdole. IFontDisp, interface</span><span class="sxs-lookup"><span data-stu-id="2ed95-176">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="2ed95-177">stdole. IPicture. handle, propriété</span><span class="sxs-lookup"><span data-stu-id="2ed95-177">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="2ed95-178">stdole. IPictureDisp. handle (propriété)</span><span class="sxs-lookup"><span data-stu-id="2ed95-178">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="2ed95-179">stdole. StdFont (interface)</span><span class="sxs-lookup"><span data-stu-id="2ed95-179">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="2ed95-180">stdole. StdPicture, interface</span><span class="sxs-lookup"><span data-stu-id="2ed95-180">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="2ed95-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ed95-181">See also</span></span>

* [<span data-ttu-id="2ed95-182">Versions .NET Framework et hors plage</span><span class="sxs-lookup"><span data-stu-id="2ed95-182">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
