---
title: 'Comment : configurer un port avec un certificat SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185106"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Comment : configurer un port avec un certificat SSL

Lors de la création d’un service auto-hébergé <xref:System.ServiceModel.WSHttpBinding> Windows Communication Foundation (WCF) avec la classe qui utilise la sécurité des transports, vous devez également configurer un port avec un certificat X.509. Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS). Pour plus d’informations, voir [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.  
  
 Si vous exécutez Windows Server 2003, utilisez l’outil HttpCfg.exe. Sur Windows Server 2003, cet outil est installé. Pour plus d’informations, voir [Httpcfg Aperçu](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)). La [documentation Windows Support Tools](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explique la syntaxe de l’outil Httpcfg.exe.  
  
 Si vous exécutez Windows Vista, utilisez l’outil Netsh.exe qui est déjà installé.
  
> [!NOTE]
> La modification des certificats stockés sur l’ordinateur nécessite des privilèges administratifs.  
  
## <a name="determine-how-ports-are-configured"></a>Déterminer comment les ports sont configurés  
  
1. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe pour afficher la configuration portuaire actuelle, en utilisant les commutateurs de **requête** et **de ssl,** comme indiqué dans l’exemple suivant.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Dans Windows Vista, utilisez l’outil Netsh.exe pour afficher la configuration portuaire actuelle, comme le montre l’exemple suivant.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Obtenir l’empreinte du pouce d’un certificat  
  
1. Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client. Pour plus d’informations, consultez la page [Affichage de certificats à l’aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Accédez à l'empreinte numérique du certificat. Pour plus d’informations, consultez l’article [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.  
  
4. Supprimez tous les espaces entre les caractères hexadécimaux. Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Lier un certificat SSL à un numéro de port  
  
1. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe en mode «set» sur le magasin Secure Sockets Layer (SSL) pour lier le certificat à un numéro de port. L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Le **commutateur -i** a `IP`la`port` syntaxe de : et instruit l’outil pour définir le certificat au port 8012 de l’ordinateur. Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.  
  
    - L’interrupteur **-h** spécifie l’empreinte du certificat.  
  
2. Dans Windows Vista, utilisez l’outil Netsh.exe, comme le montre l’exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - Le **paramètre certhash** spécifie l’empreinte du certificat.  
  
    - Le **paramètre ipport** spécifie l’adresse IP et le port, et fonctionne tout comme le commutateur **-i** de l’outil Httpcfg.exe décrit.  
  
    - Le **paramètre appid** est un GUID qui peut être utilisé pour identifier l’application propriétaire.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Lier un certificat SSL à un numéro de port et prendre en charge les certificats de clients  
  
1. Dans Windows Server 2003 ou Windows XP, pour prendre en charge les clients qui s’authentifient avec des certificats X.509 à la couche de transport, suivez la procédure précédente, mais passez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme le montre l’exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Le **commutateur -f** a `n` la syntaxe de l’endroit où n est un nombre entre 1 et 7. Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport. La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows. Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.  
  
2. Dans Windows Vista, pour prendre en charge les clients qui s’authentifient avec des certificats X.509 à la couche de transport, suivez la procédure précédente, mais avec un paramètre supplémentaire, comme indiqué dans l’exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Supprimer un certificat SSL à partir d’un numéro de port  
  
1. Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur. Pour imprimer l’information sur disque, utilisez le caractère de redirection «>», comme indiqué dans l’exemple suivant.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe avec les mots clés **supprimer** et **ssl.** Utilisez le **commutateur -i** pour spécifier le `IP``port` : numéro, et le commutateur **-h** pour spécifier l’empreinte du pouce.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Dans Windows Vista, utilisez l’outil Netsh.exe, comme le montre l’exemple suivant.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a> Exemple  

 Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport. Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
