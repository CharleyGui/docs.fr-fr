---
title: Procédure d'installation unique pour les exemples Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 1d7b5f6cb5922bde4b002611209ea3464f8e457c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921172"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procédure d'installation unique pour les exemples Windows Communication Foundation

La plupart des exemples de Windows Communication Foundation (WCF) sont hébergés dans Internet Information Services (IIS) et exécutés à partir d’un répertoire virtuel commun. Cette procédure d’installation unique crée un dossier sur le disque. Il ajoute également un répertoire virtuel à IIS nommé **servicemodelsamples**.

Le répertoire virtuel **servicemodelsamples** est utilisé pour générer et exécuter tous les exemples qui utilisent un service hébergé par IIS. Il s'agit du seul répertoire virtuel requis pour exécuter les exemples. La génération d'un exemple remplace tout service déployé précédemment dans ce répertoire ; seul le dernier exemple généré sera déployé et disponible dans ce répertoire virtuel.

> [!NOTE]
> Vous devez exécuter toutes les commandes sous un compte d'administrateur local. Si vous utilisez Windows 7, Windows Vista ou Windows Server 2008 R2, vous devez également exécuter l’invite de commandes avec des privilèges élevés. Pour ce faire, cliquez avec le bouton droit sur l’icône de l’invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur**. Toutes les commandes qui figurent dans cette rubrique doivent être exécutées dans une invite de commandes disposant des paramètres de chemin d’accès appropriés.  Le moyen le plus simple de vous en assurer consiste à utiliser l'invite de commandes de Visual Studio. Pour ouvrir cette invite, cliquez **sur Démarrer**, sélectionnez **tous les programmes**, faites défiler jusqu’à **Visual Studio 2010**, sélectionnez **Visual Studio Tools**, cliquez avec le bouton droit sur **invite de commandes Visual Studio (2010)** , puis cliquez sur **exécuter en tant qu’administrateur**. Si l’une des éditions Visual Studio Express est installée, cette invite de commandes n’est pas disponible ; il vous faut ajouter « C:\Windows\Microsoft.Net\Framework\v4.0 » au chemin d’accès système.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procédure d'installation unique pour les exemples WCF

1. Vérifiez que ASP.NET est configuré. Pour plus d’informations sur la configuration de ASP.NET, consultez [instructions d’hébergement d’Internet Information Service](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).

2. Assurez-vous que .NET Framework 4 est installé. Recherchez v 4.0 (ou version ultérieure) dans le répertoire suivant : **\Windows\Microsoft.NET\Framework**

3. Assurez-vous que Visual Studio 2012 ou version ultérieure est installé, ou que votre système d’exploitation est Windows Server 2008 SP2 ou une version ultérieure.

4. Exécutez les commandes suivantes. Pour plus d’informations sur la raison pour laquelle ces commandes doivent être exécutées, consultez [échec du service hébergé IIS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Si vous avez réinstallé IIS, réexécutez les commandes suivantes.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Si vous exécutez la commande `aspnet_regiis –i –enable`, le pool d’applications par défaut est exécuté à l’aide de .NET Framework 4, ce qui peut entraîner des problèmes d’incompatibilité pour d’autres applications sur le même ordinateur.

5. Suivez les [instructions du pare-feu](../../../../docs/framework/wcf/samples/firewall-instructions.md) pour activer les ports utilisés par les exemples.

6. Recherchez le répertoire par défaut suivant : \<Lecteurinstall >: **\ WF_WCF_Samples**. Si les exemples ont été installés précédemment, il s'agit du répertoire par défaut.

7. Si les exemples ne sont pas installés, installez-les à partir de l' [C#](https://go.microsoft.com/fwlink/?LinkId=190939)emplacement de téléchargement des exemples pour.

8. Après avoir installé les exemples, accédez à : \<Lecteurinstall >: **\ WF_WCF_Samples \wcf\setup\\**

9. Exécutez le fichier de commandes **Setupvroot. bat** . Les étapes suivantes sont exécutées :

    - Un répertoire virtuel, nommé ServiceModelSamples, est créé dans IIS.

    - Des répertoires de disque nommés %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples et %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin sont créés.

    Si vous préférez configurer ces répertoires manuellement, consultez les [instructions d’installation du répertoire virtuel](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Pour annuler toutes les modifications apportées lors de cette étape, exécutez cleanupvroot.bat une fois que vous aurez terminé d'utiliser les exemples.

    > [!NOTE]
    > Cette procédure doit être effectuée une fois seulement sur un ordinateur, sauf si cleanupvroot.bat est exécuté.

10. Vous devez accorder au compte utilisé pour générer les exemples et à l'utilisateur du service réseau des autorisations de modification sur le répertoire %SystemDrive%\inetpub\wwwroot. Lors de la génération, certains exemples hébergés par le Web peuvent tenter de copier les fichiers binaires compilés dans l'emplacement mentionné précédemment. Si vous n'avez pas défini les autorisations requises, leur génération échoue. Vous pouvez également conserver les autorisations telles quelles et exécuter l’invite de commandes du kit de développement logiciel (SDK) ou l’invite de commandes de Visual Studio (2012) en tant qu’administrateur, ou générer les exemples dans Visual Studio 2012, également exécuter en tant qu’administrateur.

    > [!NOTE]
    > Si vous ne procédez pas à cette étape, tous les exemples hébergés par IIS échouent lors de la génération. Veillez à définir les autorisations correctement ou exécutez l'invite de commandes du Kit de développement logiciel (SDK) et de Visual Studio (2012) en tant qu'administrateur.

11. Créez sur l'ordinateur un répertoire C:\logs ; certains exemples peuvent en avoir besoin. Assurez-vous que le compte approprié dispose d’un accès en écriture sur ce dossier. Pour Windows 7, Windows Vista et Windows Server 2008 R2, ce compte est **service réseau**. Pour Windows Server 2008, le compte est NT Authority\Network Service. Pour Windows XP et Windows Server 2003, le compte est ASPNET.

12. Exécutez le fichier Setupcerttool.bat. Ce fichier se trouve dans le \<dossier InstallPath > \WF_WCF_Samples\WCF\Setup  Ce script effectue les tâches suivantes :

    - génération de l'outil FindPrivateKey ;

    - création d'un répertoire nommé %ProgramFiles%\ServiceModelSampleTools ;

    - copie du nouvel outil FindPrivateKey dans ce répertoire.

    Cet outil est requis pour les exemples qui utilisent des certificats et sont hébergés dans IIS.

    > [!NOTE]
    > Pour des raisons de sécurité, n'oubliez pas de supprimer la définition de répertoire virtuel et les autorisations accordées au cours des étapes d'installation ci-dessus lorsque vous en avez terminé avec les exemples en exécutant le fichier de commandes Cleanupvroot.bat.

13. Les exemples auto-hébergés (non hébergés dans IIS) doivent être autorisés à enregistrer des adresses HTTP sur l'ordinateur pour pouvoir écouter les données. Ces autorisations (qui permettent de réserver les espaces de noms HTTP) dépendent directement des autorisations dont les comptes d'utilisateurs utilisés pour exécuter ces exemples disposent. Par défaut, les comptes d'administrateur sont autorisés à enregistrer n'importe quelle adresse HTTP. L'autorisation pour les espaces de noms HTTP utilisés par les exemples doit être accordée aux comptes qui ne sont pas administrateur. Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).

14. Certains exemples nécessitent Message Queuing. Pour obtenir des instructions d’installation [, consultez Installation de Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) .

    > [!NOTE]
    > Veillez à démarrez le service MSMQ avant d'exécuter un exemple qui requiert Message Queuing.

15. Certains exemples requièrent des certificats. Consultez les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).
