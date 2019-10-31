---
title: 'Atténuation : protocoles TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 2a2f95be92ec08185f627e862b0f62e40a1d764b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126137"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="5a0df-102">Atténuation : protocoles TLS</span><span class="sxs-lookup"><span data-stu-id="5a0df-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="5a0df-103">Depuis le .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> peuvent utiliser l'un des trois protocoles suivants : Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="5a0df-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="5a0df-104">Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5a0df-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5a0df-105">Impact</span><span class="sxs-lookup"><span data-stu-id="5a0df-105">Impact</span></span>  
 <span data-ttu-id="5a0df-106">Cette modification affecte :</span><span class="sxs-lookup"><span data-stu-id="5a0df-106">This change affects:</span></span>  
  
- <span data-ttu-id="5a0df-107">Toutes les applications qui utilisent SSL pour communiquer avec un serveur HTTPS ou un serveur socket à l'aide de l'un des types suivants : <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> et <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="5a0df-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="5a0df-108">Toutes les applications côté serveur ne peuvent pas être mises à niveau pour prendre en charge Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="5a0df-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5a0df-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="5a0df-109">Mitigation</span></span>  
 <span data-ttu-id="5a0df-110">L'atténuation recommandée consiste à mettre à niveau l'application côté serveur vers Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="5a0df-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="5a0df-111">Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext> peut être utilisée pour désactiver cette fonctionnalité de deux manières :</span><span class="sxs-lookup"><span data-stu-id="5a0df-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="5a0df-112">Par programmation, à l'aide d'un extrait de code comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a0df-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="5a0df-113">Comme l'objet <xref:System.Net.ServicePointManager> est initialisé une seule fois, la définition de ces paramètres de compatibilité doit être la première chose que fait l'application.</span><span class="sxs-lookup"><span data-stu-id="5a0df-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="5a0df-114">Pour ce faire, ajoutez la ligne suivante à la section [\<runtime](../configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="5a0df-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="5a0df-115">Notez, toutefois, que le refus du comportement par défaut n'est pas recommandé, car ce choix rend l'application moins sécurisée.</span><span class="sxs-lookup"><span data-stu-id="5a0df-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0df-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a0df-116">See also</span></span>

- [<span data-ttu-id="5a0df-117">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="5a0df-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
