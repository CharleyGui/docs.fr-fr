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
# <a name="ftp"></a>FTP

Le.NET Framework fournit une prise en charge complète du protocole FTP avec les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse>. Ces classes sont dérivées de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse>. Dans la plupart des cas, les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> fournissent tout ce qui est nécessaire pour effectuer la demande mais, si vous avez besoin d’un accès aux fonctionnalités spécifiques à FTP exposées comme propriétés, vous pouvez convertir ces classes en <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.

## <a name="examples"></a>Exemples

Pour plus d’informations, consultez les rubriques suivantes : [Guide pratique pour télécharger des fichiers avec FTP](how-to-download-files-with-ftp.md), [Guide pratique pour charger des fichiers avec FTP](how-to-upload-files-with-ftp.md) et [Guide pratique pour répertorier le contenu d’un répertoire avec FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP et proxies

Si un proxy (spécifié par la propriété <xref:System.Net.FtpWebRequest.Proxy%2A>) est un proxy HTTP, seules les commandes <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> et <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> sont prises en charge.

## <a name="see-also"></a>Voir aussi

- [Accès à Internet par le biais d’un proxy](accessing-the-internet-through-a-proxy.md)
- [Exemples de programmation réseau](network-programming-samples.md)
- [Utilisation de protocoles d’application](using-application-protocols.md)
