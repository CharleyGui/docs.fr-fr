---
title: 'Atténuation : protocoles TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779155"
---
# <a name="mitigation-tls-protocols"></a>Atténuation : protocoles TLS
À compter de .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> peuvent utiliser l’un des trois protocoles suivants : Tls1.0, Tls1.1 ou Tls 1.2. Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.  
  
## <a name="impact"></a>Impact  
 Cette modification affecte :  
  
- Toutes les applications qui utilisent SSL pour communiquer avec un serveur HTTPS ou un serveur socket à l'aide de l'un des types suivants : <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> et <xref:System.Net.Security.SslStream>.  
  
- Toutes les applications côté serveur ne peuvent pas être mises à niveau pour prendre en charge Tls1.0, Tls1.1 ou Tls 1.2.  
  
## <a name="mitigation"></a>Atténuation  
 L'atténuation recommandée consiste à mettre à niveau l'application côté serveur vers Tls1.0, Tls1.1 ou Tls 1.2. Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext> peut être utilisée pour désactiver cette fonctionnalité de deux manières :  
  
- Par programmation, à l'aide d'un extrait de code comme suit :  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Comme l'objet <xref:System.Net.ServicePointManager> est initialisé une seule fois, la définition de ces paramètres de compatibilité doit être la première chose que fait l'application.  
  
- Pour ce faire, ajoutez la ligne suivante à la section [\<runtime](../configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Notez, toutefois, que le refus du comportement par défaut n'est pas recommandé, car ce choix rend l'application moins sécurisée.  
  
## <a name="see-also"></a>Voir aussi

- [Modifications de reciblage](retargeting-changes-in-the-net-framework-4-6.md)
