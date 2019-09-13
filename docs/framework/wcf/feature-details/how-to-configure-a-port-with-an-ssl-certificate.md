---
title: 'Procédure : configurer un port avec un certificat SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893314"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Procédure : configurer un port avec un certificat SSL
Lorsque vous créez un service de Windows Communication Foundation (WCF) auto-hébergé <xref:System.ServiceModel.WSHttpBinding> avec la classe qui utilise la sécurité de transport, vous devez également configurer un port avec un certificat X. 509. Si vous ne créez pas de service auto-hébergé, vous pouvez héberger votre service sur les services Internet (IIS). Pour plus d’informations, consultez [sécurité du transport http](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pour configurer un port, l'outil que vous utilisez dépend du système d'exploitation qui s'exécute sur votre ordinateur.  
  
 Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe. Avec [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], cet outil est installé. Avec [!INCLUDE[wxp](../../../../includes/wxp-md.md)], vous pouvez télécharger l’outil à partir des [outils de support de Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Pour plus d’informations, consultez [vue d’ensemble de Httpcfg](https://go.microsoft.com/fwlink/?LinkId=88605). La [documentation](https://go.microsoft.com/fwlink/?LinkId=94840) sur les outils de support de Windows explique la syntaxe de l’outil HttpCfg. exe.  
  
 Si vous exécutez [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe qui est déjà installé.  
  
 Cette rubrique décrit comment exécuter plusieurs procédures :  
  
- Détermination de la configuration de port actuelle d'un ordinateur.  
  
- Obtention de l'empreinte numérique d'un certificat (nécessaire pour les deux procédures suivantes).  
  
- Liaison d’un certificat SSL à une configuration de port.  
  
- Liaison d'un certificat SSL à une configuration de port et prise en charge des certificats clients.  
  
- Suppression d’un certificat SSL d’un numéro de port.  
  
 Notez que la modification des certificats stockés sur l'ordinateur requiert des privilèges d'administrateur.  
  
### <a name="to-determine-how-ports-are-configured"></a>Pour déterminer comment sont configurés les ports  
  
1. Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg. exe pour afficher la configuration de port actuelle, à l’aide des commutateurs de **requête** et **SSL** , comme indiqué dans l’exemple suivant.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe pour consulter la configuration de port actuelle, comme indiqué dans l'exemple suivant.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Pour obtenir l'empreinte numérique d'un certificat  
  
1. Utilisez le composant logiciel enfichable MMC Certificats pour rechercher un certificat X.509 ayant pour objectif l'authentification du client. Pour plus d'informations, voir [Procédure : Affichez les certificats avec le composant logiciel](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)enfichable MMC.  
  
2. Accédez à l'empreinte numérique du certificat. Pour plus d’informations, consultez [Guide pratique pour Récupérez l’empreinte numérique d'](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)un certificat.  
  
3. Copiez l'empreinte numérique du certificat dans un éditeur de texte, tel que le Bloc-notes.  
  
4. Supprimez tous les espaces entre les caractères hexadécimaux. Pour ce faire, vous pouvez utiliser la fonctionnalité rechercher et remplacer de l’éditeur de texte pour remplacer chaque espace par un caractère Null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Pour lier un certificat SSL à un numéro de port  
  
1. Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l'outil HttpCfg.exe en mode « défini » dans le magasin SSL (Secure Sockets Layer) pour lier le certificat à un numéro de port. L'outil utilise l'empreinte numérique pour identifier le certificat, comme indiqué dans l'exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Le commutateur **-i** a la syntaxe `IP`suivante :`port` et indique à l’outil de définir le certificat sur le port 8012 de l’ordinateur. Le cas échéant, les quatre zéros qui précédent le nombre peuvent aussi être remplacés par l'adresse IP réelle de l'ordinateur.  
  
    - Le commutateur **-h** spécifie l’empreinte numérique du certificat.  
  
2. Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - Le paramètre **certhash** spécifie l’empreinte numérique du certificat.  
  
    - Le paramètre **ipport** spécifie l’adresse IP et le port, et fonctionne comme le commutateur **-i** de l’outil HttpCfg. exe décrit.  
  
    - Le paramètre **AppID** est un GUID qui peut être utilisé pour identifier l’application propriétaire.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Pour lier un certificat SSL à un numéro de port et prendre en charge les certificats clients  
  
1. Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais passez un paramètre de ligne de commande supplémentaire à HttpCfg.exe, comme indiqué dans l'exemple suivant.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Le commutateur **-f** a la syntaxe `n` , où n est un nombre compris entre 1 et 7. Une valeur de 2, comme indiqué dans l'exemple précédent, active des certificats clients au niveau de la couche de transport. La valeur 3 active les certificats clients et mappe ces certificats à un compte Windows. Consultez l'aide de HttpCfg.exe pour connaître le comportement des autres valeurs.  
  
2. Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], pour prendre en charge les clients authentifiés avec les certificats X.509 au niveau de la couche de transport, suivez la procédure précédente mais avec un paramètre supplémentaire, comme indiqué dans l'exemple suivant.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Pour supprimer un certificat SSL d’un numéro de port  
  
1. Utilisez l’outil HttpCfg.exe ou Netsh.exe pour consulter les ports et les empreintes numériques de toutes les liaisons sur l’ordinateur. Pour imprimer les informations sur le disque, utilisez le caractère de redirection « > », comme indiqué dans l’exemple suivant.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Dans [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], utilisez l’outil HttpCfg. exe avec les mots clés **Delete** et **SSL** . Utilisez le commutateur **-i** pour spécifier le `IP`nombre`port` : et le commutateur **-h** pour spécifier l’empreinte numérique.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Dans [!INCLUDE[wv](../../../../includes/wv-md.md)], utilisez l'outil Netsh.exe, comme indiqué dans l'exemple suivant.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment créer un service auto-hébergé à l'aide de la classe <xref:System.ServiceModel.WSHttpBinding> à laquelle est attribuée la sécurité de transport. Lorsque vous créez une application, spécifiez le numéro de port dans l'adresse.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
