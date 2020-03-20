---
title: 'Atténuation : protocoles TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457841"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="bc6e0-102">Atténuation : protocoles TLS</span><span class="sxs-lookup"><span data-stu-id="bc6e0-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="bc6e0-103">Depuis le .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> peuvent utiliser l'un des trois protocoles suivants : Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="bc6e0-104">Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="bc6e0-105">Impact</span><span class="sxs-lookup"><span data-stu-id="bc6e0-105">Impact</span></span>  
 <span data-ttu-id="bc6e0-106">Cette modification affecte :</span><span class="sxs-lookup"><span data-stu-id="bc6e0-106">This change affects:</span></span>  
  
- <span data-ttu-id="bc6e0-107">Toutes les applications qui utilisent SSL pour communiquer avec un serveur HTTPS ou un serveur socket à l'aide de l'un des types suivants : <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> et <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="bc6e0-108">Toutes les applications côté serveur ne peuvent pas être mises à niveau pour prendre en charge Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="bc6e0-109">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="bc6e0-109">Mitigation</span></span>  
 <span data-ttu-id="bc6e0-110">L’atténuation recommandée consiste à mettre à niveau l’application côté serveur vers Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="bc6e0-111">Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext> peut être utilisée pour désactiver cette fonctionnalité de deux manières :</span><span class="sxs-lookup"><span data-stu-id="bc6e0-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="bc6e0-112">Par programmation, à l'aide d'un extrait de code comme suit :</span><span class="sxs-lookup"><span data-stu-id="bc6e0-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="bc6e0-113">Comme l'objet <xref:System.Net.ServicePointManager> est initialisé une seule fois, la définition de ces paramètres de compatibilité doit être la première chose que fait l'application.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="bc6e0-114">En ajoutant la ligne suivante à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="bc6e0-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="bc6e0-115">Notez, toutefois, que le refus du comportement par défaut n'est pas recommandé, car ce choix rend l'application moins sécurisée.</span><span class="sxs-lookup"><span data-stu-id="bc6e0-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6e0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc6e0-116">See also</span></span>

- [<span data-ttu-id="bc6e0-117">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="bc6e0-117">Application compatibility</span></span>](application-compatibility.md)
