---
title: Création de requêtes Internet
description: Découvrez comment les applications créent des instances WebRequest via WebRequest. Create, une méthode statique qui crée une classe dérivée basée sur le modèle URI qui lui est passé.
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502624"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="404ad-103">Création de requêtes Internet</span><span class="sxs-lookup"><span data-stu-id="404ad-103">Creating Internet Requests</span></span>
<span data-ttu-id="404ad-104">Les applications créent des instances de <xref:System.Net.WebRequest> par le biais de la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="404ad-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="404ad-105">Il s’agit d’une méthode statique qui crée une classe dérivée de **WebRequest** basée sur le schéma d’URI qui lui est passé.</span><span class="sxs-lookup"><span data-stu-id="404ad-105">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="404ad-106">Requêtes web, FTP et de fichier</span><span class="sxs-lookup"><span data-stu-id="404ad-106">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="404ad-107">Le .NET Framework fournit la classe <xref:System.Net.HttpWebRequest>, qui est dérivée de **WebRequest**, pour gérer les requêtes HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="404ad-107">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="404ad-108">Dans la plupart des cas, la classe **WebRequest** fournit toutes les propriétés dont vous avez besoin pour effectuer une requête ; toutefois, si nécessaire, vous pouvez effectuer un cast d’objets **WebRequest** créés par la méthode **WebRequest.Create** vers le type **HttpWebRequest** pour accéder aux propriétés de la requête propres à HTTP.</span><span class="sxs-lookup"><span data-stu-id="404ad-108">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="404ad-109">De même, l’objet **HttpWebResponse** gère les réponses aux requêtes HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="404ad-109">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="404ad-110">Pour accéder aux propriétés de l’objet **HttpWebResponse** propres à HTTP, vous devez effectuer un cast des objets **WebResponse** vers le type **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="404ad-110">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="404ad-111">Le .NET Framework fournit également les classes <xref:System.Net.FileWebRequest> et <xref:System.Net.FileWebResponse> afin de gérer les requêtes pour les ressources qui utilisent le schéma d’URI « file: ».</span><span class="sxs-lookup"><span data-stu-id="404ad-111">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="404ad-112">De même, les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse> sont fournies pour gérer les requêtes pour les ressources qui utilisent le schéma d’URI « ftp: ».</span><span class="sxs-lookup"><span data-stu-id="404ad-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="404ad-113">Si votre requête concerne une ressource qui utilise l’un de ces schémas, vous pouvez utiliser la méthode **WebRequest.Create** pour obtenir un objet avec lequel effectuer votre requête.</span><span class="sxs-lookup"><span data-stu-id="404ad-113">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="404ad-114">Pour gérer les requêtes qui utilisent d’autres protocoles au niveau de l’application, vous devez implémenter des classes propres au protocole dérivées de **WebRequest** et **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="404ad-114">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="404ad-115">Pour plus d’informations, consultez [programmation de protocoles enfichables](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="404ad-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="404ad-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="404ad-116">See also</span></span>

- [<span data-ttu-id="404ad-117">Guide pratique pour demander des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="404ad-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="404ad-118">Demande de données</span><span class="sxs-lookup"><span data-stu-id="404ad-118">Requesting Data</span></span>](requesting-data.md)
