---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642878"
---
# <a name="ftp"></a><span data-ttu-id="5973d-102">FTP</span><span class="sxs-lookup"><span data-stu-id="5973d-102">FTP</span></span>

<span data-ttu-id="5973d-103">Le.NET Framework fournit une prise en charge complète du protocole FTP avec les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5973d-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="5973d-104">Ces classes sont dérivées de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5973d-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="5973d-105">Dans la plupart des cas, les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> fournissent tout ce qui est nécessaire pour effectuer la demande mais, si vous avez besoin d’un accès aux fonctionnalités spécifiques à FTP exposées comme propriétés, vous pouvez convertir ces classes en <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5973d-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="5973d-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="5973d-106">Examples</span></span>

<span data-ttu-id="5973d-107">Pour plus d’informations, consultez les rubriques suivantes : [Guide pratique pour télécharger des fichiers avec FTP](how-to-download-files-with-ftp.md), [Guide pratique pour charger des fichiers avec FTP](how-to-upload-files-with-ftp.md) et [Guide pratique pour répertorier le contenu d’un répertoire avec FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="5973d-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="5973d-108">FTP et proxies</span><span class="sxs-lookup"><span data-stu-id="5973d-108">FTP and proxies</span></span>

<span data-ttu-id="5973d-109">Si un proxy (spécifié par la propriété <xref:System.Net.FtpWebRequest.Proxy%2A>) est un proxy HTTP, seules les commandes <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> et <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="5973d-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="5973d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5973d-110">See also</span></span>

- [<span data-ttu-id="5973d-111">Accès à Internet par le biais d’un proxy</span><span class="sxs-lookup"><span data-stu-id="5973d-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="5973d-112">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="5973d-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="5973d-113">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="5973d-113">Using Application Protocols</span></span>](using-application-protocols.md)
