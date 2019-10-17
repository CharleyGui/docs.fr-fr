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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="c54b9-102">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c54b9-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="c54b9-103">La .NET Framework évolue constamment.</span><span class="sxs-lookup"><span data-stu-id="c54b9-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="c54b9-104">Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, les nouvelles fonctionnalités sont publiées hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="c54b9-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="c54b9-105">Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.</span><span class="sxs-lookup"><span data-stu-id="c54b9-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="c54b9-106">En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c54b9-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="c54b9-107">Par exemple, la classe <xref:System.Text.CodePagesEncodingProvider> met les encodages de pages de codes à la disposition des applications UWP développées à l’aide du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c54b9-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="c54b9-108">Cette rubrique liste également ces bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="c54b9-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="c54b9-109">Projets OOB</span><span class="sxs-lookup"><span data-stu-id="c54b9-109">OOB projects</span></span>
  
| <span data-ttu-id="c54b9-110">Projet</span><span class="sxs-lookup"><span data-stu-id="c54b9-110">Project</span></span> | <span data-ttu-id="c54b9-111">Description</span><span class="sxs-lookup"><span data-stu-id="c54b9-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="c54b9-112">Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer.</span><span class="sxs-lookup"><span data-stu-id="c54b9-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="c54b9-113">Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows.</span><span class="sxs-lookup"><span data-stu-id="c54b9-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="c54b9-114">Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.</span><span class="sxs-lookup"><span data-stu-id="c54b9-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="c54b9-115">La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="c54b9-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="c54b9-116">Bibliothèques propres à une plateforme</span><span class="sxs-lookup"><span data-stu-id="c54b9-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="c54b9-117">Projet</span><span class="sxs-lookup"><span data-stu-id="c54b9-117">Project</span></span> | <span data-ttu-id="c54b9-118">Description</span><span class="sxs-lookup"><span data-stu-id="c54b9-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="c54b9-119">Étend la classe <xref:System.Text.EncodingProvider> pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="c54b9-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="c54b9-120">API privées</span><span class="sxs-lookup"><span data-stu-id="c54b9-120">Private APIs</span></span>  

<span data-ttu-id="c54b9-121">Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.</span><span class="sxs-lookup"><span data-stu-id="c54b9-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="c54b9-122">Microsoft. SqlServer. Server. SmiOrderProperty. Item, propriété</span><span class="sxs-lookup"><span data-stu-id="c54b9-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="c54b9-123">Méthode System. exception. PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="c54b9-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="c54b9-124">System. Data. SqlTypes. SqlChars. Stream, propriété</span><span class="sxs-lookup"><span data-stu-id="c54b9-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="c54b9-125">Constructeur System. Data. SqlTypes. SqlStreamChars</span><span class="sxs-lookup"><span data-stu-id="c54b9-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="c54b9-126">System. Data. SqlTypes. SqlStreamChars. CanSeek, propriété</span><span class="sxs-lookup"><span data-stu-id="c54b9-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="c54b9-127">Propriété System. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="c54b9-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="c54b9-128">Propriété System. Data. SqlTypes. SqlStreamChars. Length</span><span class="sxs-lookup"><span data-stu-id="c54b9-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="c54b9-129">System. Data. SqlTypes. SqlStreamChars. Close, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="c54b9-130">System. Data. SqlTypes. SqlStreamChars. dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="c54b9-131">System. Data. SqlTypes. SqlStreamChars. Flush, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="c54b9-132">System. Data. SqlTypes. SqlStreamChars. Read, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="c54b9-133">System. Data. SqlTypes. SqlStreamChars. Seek, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="c54b9-134">System. Data. SqlTypes. SqlStreamChars. SetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="c54b9-135">System. Data. SqlTypes. SqlStreamChars. Write, méthode</span><span class="sxs-lookup"><span data-stu-id="c54b9-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="c54b9-136">Classe System .net. Connection</span><span class="sxs-lookup"><span data-stu-id="c54b9-136">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="c54b9-137">System .net. Connection. m @ no__t-champ 1WriteList</span><span class="sxs-lookup"><span data-stu-id="c54b9-137">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="c54b9-138">Classe System .net. ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="c54b9-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="c54b9-139">System .net. ConnectionGroup. m @ no__t-1ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="c54b9-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="c54b9-140">Classe System .net. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="c54b9-140">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="c54b9-141">System .net. CoreResponseData. m @ no__t-1ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="c54b9-141">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="c54b9-142">System .net. CoreResponseData. m @ no__t-1StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="c54b9-142">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="c54b9-143">System .net. HttpWebRequest. @no__t-champ 1AutoRedirects</span><span class="sxs-lookup"><span data-stu-id="c54b9-143">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="c54b9-144">System .net. HttpWebRequest. @no__t-champ 1CoreResponse</span><span class="sxs-lookup"><span data-stu-id="c54b9-144">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="c54b9-145">System .net. HttpWebRequest. @no__t-champ 1HttpResponse</span><span class="sxs-lookup"><span data-stu-id="c54b9-145">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="c54b9-146">Champ System .net. ServicePoint. m @ no__t-1ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="c54b9-146">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="c54b9-147">System .net. ServicePointManager. s @ no__t-champ 1ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="c54b9-147">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="c54b9-148">System. Windows. Diagnostics. VisualDiagnostics. s @ no__t-1isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="c54b9-148">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="c54b9-149">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="c54b9-149">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="c54b9-150">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="c54b9-150">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="c54b9-151">ADODB. Interface de connexion</span><span class="sxs-lookup"><span data-stu-id="c54b9-151">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="c54b9-152">ADODB. Énumération EventReason</span><span class="sxs-lookup"><span data-stu-id="c54b9-152">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="c54b9-153">ADODB. Énumération EventStatus</span><span class="sxs-lookup"><span data-stu-id="c54b9-153">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="c54b9-154">stdole. DISPPARAMS, structure</span><span class="sxs-lookup"><span data-stu-id="c54b9-154">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="c54b9-155">stdole. EXCEPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="c54b9-155">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="c54b9-156">stdole. Propriété IFont.Name</span><span class="sxs-lookup"><span data-stu-id="c54b9-156">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="c54b9-157">stdole. IFontDisp, interface</span><span class="sxs-lookup"><span data-stu-id="c54b9-157">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="c54b9-158">stdole. IPicture. handle, propriété</span><span class="sxs-lookup"><span data-stu-id="c54b9-158">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="c54b9-159">stdole. IPictureDisp. handle (propriété)</span><span class="sxs-lookup"><span data-stu-id="c54b9-159">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="c54b9-160">stdole. StdFont (interface)</span><span class="sxs-lookup"><span data-stu-id="c54b9-160">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="c54b9-161">stdole. StdPicture, interface</span><span class="sxs-lookup"><span data-stu-id="c54b9-161">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="c54b9-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c54b9-162">See also</span></span>

* [<span data-ttu-id="c54b9-163">Versions finales hors plage de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c54b9-163">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
