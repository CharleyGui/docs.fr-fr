---
title: 'Comment : rendre des certificats X.509 accessibles à WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184893"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Comment : rendre des certificats X.509 accessibles à WCF
Pour rendre un certificat X.509 accessible à la Windows Communication Foundation (WCF), le code de demande doit spécifier le nom et l’emplacement du magasin de certificats. Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509. Pour obtenir la clé privée associée à un certificat X.509 dans un magasin de certificats, WCF doit avoir la permission de le faire. Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Pour rendre des certificats X.509 accessibles à WCF  
  
1. Donnez au compte en vertu duquel WCF est en cours d’exécution l’accès lu au fichier qui contient la clé privée associée au certificat X.509.  
  
    1. Déterminer si WCF exige l’accès à la clé privée pour le certificat X.509.  
  
         Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.  
  
        |Utilisation d'un certificat X.509|Clé privée|  
        |---------------------------|-----------------|  
        |Signature numérique d'un message SOAP sortant.|Oui|  
        |Vérification de la signature d'un message SOAP entrant.|Non |  
        |Chiffrement d'un message SOAP sortant.|Non |  
        |Déchiffrement d'un message SOAP entrant.|Oui|  
  
    2. Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.  
  
         Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration. Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Déterminez où se trouve la clé privée du certificat sur l’ordinateur en utilisant [l’outil FindPrivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)  
  
         [L’outil FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) exige le nom du magasin de certificats, l’emplacement du magasin de certificats, et quelque chose qui identifie uniquement le certificat. Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique. Pour plus d’informations sur la façon de déterminer l’empreinte du pouce pour un certificat, voir [comment: Récupérer l’empreinte de pouce d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         L’exemple de code suivant utilise [l’outil FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) pour déterminer `My` l’emplacement de la clé privée pour un certificat dans `CurrentUser` le magasin avec une empreinte de pouce de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Déterminez le compte sous lequel WCF est en cours d’exécution.  
  
         Le tableau suivant détaille le compte dans lequel WCF est en cours d’exécution pour un scénario donné.  
  
        |Scénario|Identité du processus|  
        |--------------|----------------------|  
        |Client (console ou application WinForms).|Utilisateur actuellement connecté.|  
        |Service auto-hébergé.|Utilisateur actuellement connecté.|  
        |Service hébergé dans IIS 6.0 (Windows Server 2003) ou IIS 7.0 (Windows Vista).|SERVICE RÉSEAU|  
        |Service hébergé dans IIS 5.X (Windows XP).|Contrôlé par l'élément `<processModel>` dans le fichier Machine.config. Le compte par défaut est ASPNET.|  
  
    5. Grant lire l’accès au fichier qui contient la clé privée du compte que WCF est en cours d’exécution sous, en utilisant un outil tel que icacls.exe.  
  
         L’exemple de code suivant modifie la liste de contrôle d’accès discrétionnaire (DACL) pour que le fichier spécifié accorde au compte NETWORK SERVICE lus (:R) l’accès au fichier.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Voir aussi

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Comment : récupérer l'empreinte numérique d'un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
