---
title: 'Procédure : configurer un port avec un certificat SSL'
description: Découvrez comment configurer un port avec un certificat X. 509, requis pour un service WCF auto-hébergé avec la classe WSHttpBinding à l’aide de la sécurité de transport.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 619a893e0973f6691e32446d75f101201a0b6799
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556380"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Procédure : configurer un port avec un certificat SSL

Lorsque vous créez un service de Windows Communication Foundation (WCF) auto-hébergé avec la <xref:System.ServiceModel.WSHttpBinding> classe qui utilise la sécurité de transport, vous devez également configurer un port avec un certificat X. 509. Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS). Pour plus d’informations, consultez [sécurité du transport http](http-transport-security.md).  
  
 Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.  
  
 Si vous exécutez Windows Server 2003, utilisez l’outil HttpCfg.exe. Sur Windows Server 2003, cet outil est installé. Pour plus d’informations, consultez [vue d’ensemble de Httpcfg](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)). La [documentation](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) sur les outils de support de Windows explique la syntaxe de l’outil Httpcfg.exe.  
  
 Si vous exécutez Windows Vista, utilisez l’outil Netsh.exe qui est déjà installé.
  
> [!NOTE]
> La modification des certificats stockés sur l’ordinateur requiert des privilèges d’administrateur.  
  
## <a name="determine-how-ports-are-configured"></a>Déterminer le mode de configuration des ports  
  
1. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe pour afficher la configuration de port actuelle, à l’aide des commutateurs de **requête** et **SSL** , comme indiqué dans l’exemple suivant.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Dans Windows Vista, utilisez l’outil Netsh.exe pour afficher la configuration de port actuelle, comme indiqué dans l’exemple suivant.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Obtenir l’empreinte numérique d’un certificat  
  
1. Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client. Pour plus d’informations, consultez la page [Affichage de certificats à l’aide du composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Accédez à l'empreinte numérique du certificat. Pour plus d’informations, consultez l’article [Comment : récupérer l’empreinte numérique d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.  
  
4. Supprimez tous les espaces entre les caractères hexadécimaux. Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Lier un certificat SSL à un numéro de port  
  
1. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe en mode « set » sur le magasin protocole SSL (SSL) pour lier le certificat à un numéro de port. L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Le commutateur **-i** a la syntaxe `IP` suivante : `port` et indique à l’outil de définir le certificat sur le port 8012 de l’ordinateur. Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.  
  
    - Le commutateur **-h** spécifie l’empreinte numérique du certificat.  
  
2. Dans Windows Vista, utilisez l’outil Netsh.exe, comme indiqué dans l’exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - Le paramètre **certhash** spécifie l’empreinte numérique du certificat.  
  
    - Le paramètre **ipport** spécifie l’adresse IP et le port, et fonctionne de la même façon que le commutateur **-i** de l’outil Httpcfg.exe décrit.  
  
    - Le paramètre **AppID** est un GUID qui peut être utilisé pour identifier l’application propriétaire.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Lier un certificat SSL à un numéro de port et prendre en charge les certificats clients  
  
1. Dans Windows Server 2003 ou Windows XP, pour prendre en charge les clients qui s’authentifient avec des certificats X. 509 au niveau de la couche de transport, suivez la procédure précédente, mais transmettez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme illustré dans l’exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Le commutateur **-f** a la syntaxe, `n` où n est un nombre compris entre 1 et 7. Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport. La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows. Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.  
  
2. Dans Windows Vista, pour prendre en charge les clients qui s’authentifient avec des certificats X. 509 au niveau de la couche de transport, suivez la procédure précédente, mais avec un paramètre supplémentaire, comme indiqué dans l’exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Supprimer un certificat SSL d’un numéro de port  
  
1. Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur. Pour imprimer les informations sur le disque, utilisez le caractère de redirection « > », comme indiqué dans l’exemple suivant.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Dans Windows Server 2003 ou Windows XP, utilisez l’outil HttpCfg.exe avec les mots clés **Delete** et **SSL** . Utilisez le commutateur **-i** pour spécifier le `IP` `port` nombre : et le commutateur **-h** pour spécifier l’empreinte numérique.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Dans Windows Vista, utilisez l’outil Netsh.exe, comme indiqué dans l’exemple suivant.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a> Exemple  

 Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport. Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de transport HTTP](http-transport-security.md)
