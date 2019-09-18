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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="31844-102">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="31844-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="31844-103">La .NET Framework évolue constamment.</span><span class="sxs-lookup"><span data-stu-id="31844-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="31844-104">Pour améliorer le développement multiplateforme et introduire de nouvelles fonctionnalités dès le début, les nouvelles fonctionnalités sont publiées hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="31844-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="31844-105">Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.</span><span class="sxs-lookup"><span data-stu-id="31844-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="31844-106">En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31844-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="31844-107">Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les encodages de pages de codes disponibles pour les applications UWP développées à l’aide de l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31844-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="31844-108">Cette rubrique liste également ces bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="31844-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="31844-109">Projets OOB</span><span class="sxs-lookup"><span data-stu-id="31844-109">OOB projects</span></span>
  
| <span data-ttu-id="31844-110">Projet</span><span class="sxs-lookup"><span data-stu-id="31844-110">Project</span></span> | <span data-ttu-id="31844-111">Description</span><span class="sxs-lookup"><span data-stu-id="31844-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="31844-112">Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer.</span><span class="sxs-lookup"><span data-stu-id="31844-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="31844-113">Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows.</span><span class="sxs-lookup"><span data-stu-id="31844-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="31844-114">Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.</span><span class="sxs-lookup"><span data-stu-id="31844-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="31844-115">La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="31844-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="31844-116">Bibliothèques propres à une plateforme</span><span class="sxs-lookup"><span data-stu-id="31844-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="31844-117">Projet</span><span class="sxs-lookup"><span data-stu-id="31844-117">Project</span></span> | <span data-ttu-id="31844-118">Description</span><span class="sxs-lookup"><span data-stu-id="31844-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="31844-119">Étend la <xref:System.Text.EncodingProvider> classe pour mettre les encodages de pages de codes à la disposition des applications qui ciblent le plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="31844-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="31844-120">API privées</span><span class="sxs-lookup"><span data-stu-id="31844-120">Private APIs</span></span>  

<span data-ttu-id="31844-121">Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.</span><span class="sxs-lookup"><span data-stu-id="31844-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="31844-122">Nom de l'API</span><span class="sxs-lookup"><span data-stu-id="31844-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="31844-123">Classe System .net. Connection</span><span class="sxs-lookup"><span data-stu-id="31844-123">System.Net.Connection Class</span></span>](connection.md) |
| [<span data-ttu-id="31844-124">Champ System .net. Connection.\_m WriteList</span><span class="sxs-lookup"><span data-stu-id="31844-124">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md) |
| [<span data-ttu-id="31844-125">Classe System .net. ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="31844-125">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md) |
| [<span data-ttu-id="31844-126">Champ System .net. ConnectionGroup.\_m ConnectionList</span><span class="sxs-lookup"><span data-stu-id="31844-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md) |
| [<span data-ttu-id="31844-127">Classe System .net. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="31844-127">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md) |
| [<span data-ttu-id="31844-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="31844-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="31844-129">Champ StatusCode de System .net.\_CoreResponseData. m</span><span class="sxs-lookup"><span data-stu-id="31844-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="31844-130">System .net. HttpWebRequest. \_Champ AutoRedirects</span><span class="sxs-lookup"><span data-stu-id="31844-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md) |
| [<span data-ttu-id="31844-131">System .net. HttpWebRequest. \_Champ CoreResponse</span><span class="sxs-lookup"><span data-stu-id="31844-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="31844-132">System .net. HttpWebRequest. \_HttpResponse (champ)</span><span class="sxs-lookup"><span data-stu-id="31844-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md) |
| [<span data-ttu-id="31844-133">Champ System .net. ServicePoint.\_m ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="31844-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md) |
| [<span data-ttu-id="31844-134">Champ System .net. ServicePointManager.\_s ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="31844-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md) |
| [<span data-ttu-id="31844-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="31844-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="31844-136">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="31844-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md) |
| [<span data-ttu-id="31844-137">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="31844-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="31844-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31844-138">See also</span></span>

- [<span data-ttu-id="31844-139">Versions finales hors plage de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="31844-139">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
