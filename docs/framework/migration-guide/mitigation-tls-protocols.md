---
title: 'Atténuation : protocoles TLS'
description: En savoir plus sur l’impact et l’atténuation des changements de protocole TLS à compter de .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475357"
---
# <a name="mitigation-tls-protocols"></a>Atténuation : protocoles TLS
Depuis le .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> peuvent utiliser l'un des trois protocoles suivants : Tls1.0, Tls1.1 ou Tls 1.2. Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.  
  
## <a name="impact"></a>Impact  
 Cette modification affecte :  
  
- Toutes les applications qui utilisent SSL pour communiquer avec un serveur HTTPS ou un serveur socket à l'aide de l'un des types suivants : <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> et <xref:System.Net.Security.SslStream>.  
  
- Toutes les applications côté serveur ne peuvent pas être mises à niveau pour prendre en charge Tls1.0, Tls1.1 ou Tls 1.2.  
  
## <a name="mitigation"></a>Limitation des risques  
 L’atténuation recommandée consiste à mettre à niveau l’application côté serveur vers Tls1.0, Tls1.1 ou Tls 1.2. Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext> peut être utilisée pour désactiver cette fonctionnalité de deux manières :  
  
- Par programmation, à l'aide d'un extrait de code comme suit :  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Comme l'objet <xref:System.Net.ServicePointManager> est initialisé une seule fois, la définition de ces paramètres de compatibilité doit être la première chose que fait l'application.  
  
- En ajoutant la ligne suivante à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Notez, toutefois, que le refus du comportement par défaut n'est pas recommandé, car ce choix rend l'application moins sécurisée.  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
