---
title: Création de requêtes Internet
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
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048619"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="ccb2a-102">Création de requêtes Internet</span><span class="sxs-lookup"><span data-stu-id="ccb2a-102">Creating Internet Requests</span></span>
<span data-ttu-id="ccb2a-103">Les applications créent des instances de <xref:System.Net.WebRequest> par le biais de la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ccb2a-104">Il s’agit d’une méthode statique qui crée une classe dérivée de **WebRequest** basée sur le schéma d’URI qui lui est passé.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="ccb2a-105">Requêtes web, FTP et de fichier</span><span class="sxs-lookup"><span data-stu-id="ccb2a-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="ccb2a-106">Le .NET Framework fournit la classe <xref:System.Net.HttpWebRequest>, qui est dérivée de **WebRequest**, pour gérer les requêtes HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="ccb2a-107">Dans la plupart des cas, la classe **WebRequest** fournit toutes les propriétés dont vous avez besoin pour effectuer une requête ; toutefois, si nécessaire, vous pouvez effectuer un cast d’objets **WebRequest** créés par la méthode **WebRequest.Create** vers le type **HttpWebRequest** pour accéder aux propriétés de la requête propres à HTTP.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="ccb2a-108">De même, l’objet **HttpWebResponse** gère les réponses aux requêtes HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="ccb2a-109">Pour accéder aux propriétés de l’objet **HttpWebResponse** propres à HTTP, vous devez effectuer un cast des objets **WebResponse** vers le type **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="ccb2a-110">Le .NET Framework fournit également les classes <xref:System.Net.FileWebRequest> et <xref:System.Net.FileWebResponse> afin de gérer les requêtes pour les ressources qui utilisent le schéma d’URI « file: » .</span><span class="sxs-lookup"><span data-stu-id="ccb2a-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="ccb2a-111">De même, les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse> sont fournies pour gérer les requêtes pour les ressources qui utilisent le schéma d’URI « ftp: ».</span><span class="sxs-lookup"><span data-stu-id="ccb2a-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="ccb2a-112">Si votre requête concerne une ressource qui utilise l’un de ces schémas, vous pouvez utiliser la méthode **WebRequest.Create** pour obtenir un objet avec lequel effectuer votre requête.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="ccb2a-113">Pour gérer les requêtes qui utilisent d’autres protocoles au niveau de l’application, vous devez implémenter des classes propres au protocole dérivées de **WebRequest** et **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="ccb2a-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="ccb2a-114">Pour plus d’informations, consultez [Programmation de protocoles enfichables](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ccb2a-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb2a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccb2a-115">See also</span></span>

- [<span data-ttu-id="ccb2a-116">Guide pratique pour demander des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="ccb2a-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="ccb2a-117">Demande de données</span><span class="sxs-lookup"><span data-stu-id="ccb2a-117">Requesting Data</span></span>](requesting-data.md)
