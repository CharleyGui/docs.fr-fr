---
title: Détection automatique de proxy
description: En savoir plus sur la détection automatique de proxy, où le système identifie un serveur proxy Web et l’utilise pour envoyer des demandes pour le compte du client.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: 8d1b904a8acc6d3960a076c54c2d5f5de54820c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250630"
---
# <a name="automatic-proxy-detection"></a>Détection automatique de proxy

La détection automatique de proxy est un processus par lequel un serveur proxy web est identifié par le système et utilisé pour envoyer des demandes pour le compte du client. Cette fonctionnalité est également connue sous le nom de Découverte automatique de proxy Web (WPAD, Web Proxy Auto-Discovery). Quand la détection automatique de proxy est activée, le système tente de localiser un script de configuration de proxy qui est chargé de retourner l’ensemble des proxys pouvant être utilisés pour la requête. Si le script de configuration de proxy est trouvé, il est téléchargé, compilé et exécuté sur l’ordinateur local quand les informations de proxy, le flux de requête ou la réponse sont obtenus pour une requête qui utilise une instance de <xref:System.Net.WebProxy>.  
  
 La détection automatique de proxy est effectuée par la classe <xref:System.Net.WebProxy> et peut utiliser des paramètres au niveau de la requête, des paramètres dans des fichiers de configuration et des paramètres spécifiés à l’aide de la boîte de dialogue **Réseau local** d’Internet Explorer.  
  
> [!NOTE]
> Vous pouvez afficher la boîte de dialogue **Réseau local** d’Internet Explorer en sélectionnant **Outils** dans le menu principal d’Internet Explorer, puis **Options Internet**. Ensuite, sélectionnez l’onglet **Connexions** et cliquez sur **Paramètres du réseau local**.  
  
 Quand la détection automatique de proxy est activée, la classe <xref:System.Net.WebProxy> tente de localiser le script de configuration de proxy comme suit :  
  
1. La fonction `InternetQueryOption` WinINet est utilisée pour accéder au script de configuration de proxy le plus récemment détecté par Internet Explorer.  
  
2. Si le script est introuvable, la classe <xref:System.Net.WebProxy> utilise le protocole DHCP (Dynamic Host Configuration Protocol) pour accéder au script. Le serveur DHCP peut répondre avec l’emplacement (nom d’hôte) du script ou avec l’URL complète du script.  
  
3. Si le protocole DHCP n’identifie pas l’hôte WPAD, le système DNS est interrogé pour trouver un hôte avec WPAD comme nom ou alias.  
  
4. Si l’hôte n’est pas identifié et que l’emplacement d’un script de configuration de proxy est spécifié par les paramètres de réseau local d’Internet Explorer ou un fichier de configuration, cet emplacement est utilisé.  
  
> [!NOTE]
> Les applications qui s’exécutent en tant que service NT ou dans le cadre d’ASP.NET utilisent les paramètres de serveur proxy d’Internet Explorer (s’ils sont disponibles) de l’utilisateur appelant. Ces paramètres peuvent ne pas être disponibles pour toutes les applications de service.  
  
 Les proxys sont configurés sur la base de chaque connectoid. Un connectoid est un élément dans la boîte de dialogue de connexion réseau. Il peut s’agir d’un appareil réseau physique (un modem ou une carte Ethernet) ou d’une interface virtuelle (par exemple, une connexion VPN qui s’exécute sur un appareil réseau). Quand un connectoid change (par exemple quand une connexion sans fil change un point d’accès, ou qu’un réseau VPN est activé), l’algorithme de détection de proxy est réexécuté.  
  
 Par défaut, les paramètres de proxy d’Internet Explorer sont utilisés pour détecter le serveur proxy. Si votre application s’exécute sous un compte non interactif (sans un moyen pratique de configurer les paramètres du proxy IE), ou si vous souhaitez utiliser des paramètres de proxy différents des paramètres d’IE, vous pouvez configurer votre proxy en créant un fichier de configuration avec les éléments [ \<defaultProxy> élément (paramètres réseau)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) et [ \<proxy> élément (paramètres réseau)](../configure-apps/file-schema/network/proxy-element-network-settings.md) définis.  
  
 Pour les requêtes que vous créez, vous pouvez désactiver la détection automatique de proxy au niveau de la requête en utilisant un <xref:System.Net.WebRequest.Proxy%2A> null avec votre requête, comme indiqué dans l’exemple de code suivant.  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub
```  
  
 Les requêtes qui n’ont pas de proxy utilisent le proxy par défaut de votre domaine d’application, qui est disponible dans la propriété <xref:System.Net.WebRequest.DefaultWebProxy%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net> , Élément (paramètres réseau)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
