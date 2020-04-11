---
title: Procédure d'installation unique pour les exemples Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121629"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procédure d'installation unique pour les exemples Windows Communication Foundation

La plupart des échantillons de la Windows Communication Foundation (WCF) sont hébergés dans les services d’information Sur Internet (IIS) et sont gérés à partir d’un répertoire virtuel commun. Cette procédure de configuration unique crée un dossier sur le disque; il ajoute également un répertoire virtuel à l’IIS nommé **ServiceModelSamples**.

L’annuaire virtuel **ServiceModelSamples** est utilisé pour la construction et l’exécution de tous les échantillons qui utilisent un service hébergé par l’IIS. Il s'agit du seul répertoire virtuel requis pour exécuter les exemples. La génération d'un exemple remplace tout service déployé précédemment dans ce répertoire ; seul le dernier exemple généré sera déployé et disponible dans ce répertoire virtuel.

> [!NOTE]
> Vous devez exécuter toutes les commandes sous un compte d'administrateur local. Si vous utilisez Windows 7, Windows Vista ou Windows Server 2008 R2, vous devez également exécuter l’invite de commande avec des privilèges élevés. Pour ce faire, cliquez à droite sur l’icône d’invite de commande, puis cliquez sur **Run en tant qu’administrateur**. Toutes les commandes qui figurent dans cette rubrique doivent être exécutées dans une invite de commandes disposant des paramètres de chemin d’accès appropriés.  Le moyen le plus simple de vous en assurer consiste à utiliser l'invite de commandes de Visual Studio. Pour ouvrir cette invite, cliquez sur **Démarrer**, sélectionnez **Tous les programmes**, faites défiler vers le bas pour Visual Studio **2010**, sélectionnez **Visual Studio Tools**, clic droit Visual Studio Command Prompt **(2010)**, puis cliquez sur **Run en tant qu’administrateur**. Si l’une des éditions Visual Studio Express est installée, cette invite de commandes n’est pas disponible ; il vous faut ajouter « C:\Windows\Microsoft.Net\Framework\v4.0 » au chemin d’accès système.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procédure d'installation unique pour les exemples WCF

1. Assurez-vous que ASP.NET est mis en place. Pour plus d’informations sur la façon de mettre en place ASP.NET, voir [Internet Information Service Hosting Instructions](internet-information-service-hosting-instructions.md).

2. Assurez-vous que le cadre 4 de .NET est installé. Rechercher l’annuaire suivant pour v4.0 (ou plus tard): **'Windows’Microsoft.NET’Framework**

3. Assurez-vous d’avoir Visual Studio 2012 ou plus tard installé, ou votre système d’exploitation est Windows Server 2008 SP2 ou plus tard.

4. Exécutez les commandes suivantes : Pour plus d’informations sur les raisons pour lesquelles ces commandes doivent être exécutées, voir [IIS Hosted Service Fails](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Si vous avez réinstallé IIS, réexécutez les commandes suivantes.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > L’exécution `aspnet_regiis –i –enable` de la commande fera fonctionner le Pool d’applications par défaut à l’aide de .NET Framework 4, ce qui peut produire des problèmes d’incompatibilité pour d’autres applications sur le même ordinateur.

5. Suivez les instructions de [pare-feu](firewall-instructions.md) pour activer les ports utilisés par les échantillons.

6. Vérifiez pour l’annuaire \<par défaut suivant: InstallDrive>:**'WF_WCF_Samples**. Si les exemples ont été installés précédemment, il s'agit du répertoire par défaut.

7. Si les échantillons ne sont pas installés, installez-les à partir de [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Échantillons pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

8. Après l’installation des échantillons, rendez-vous sur : \<InstallDrive> :**'WF_WCF_Samples’WCF’Setup\\ **

9. Exécutez le fichier de lot **Setupvroot.bat.** Les étapes à exécuter sont les suivantes :

    - Un répertoire virtuel, nommé ServiceModelSamples, est créé dans IIS.

    - Des répertoires de disque nommés %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples et %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin sont créés.

    Si vous préférez configurer ces répertoires manuellement, consultez les [instructions d’installation de l’annuaire virtuel](virtual-directory-setup-instructions.md). Pour annuler toutes les modifications apportées lors de cette étape, exécutez cleanupvroot.bat une fois que vous aurez terminé d'utiliser les exemples.

    > [!NOTE]
    > Cette procédure doit être effectuée une fois seulement sur un ordinateur, sauf si cleanupvroot.bat est exécuté.

10. Vous devez accorder au compte utilisé pour générer les exemples et à l'utilisateur du service réseau des autorisations de modification sur le répertoire %SystemDrive%\inetpub\wwwroot. Lors de la génération, certains exemples hébergés par le Web peuvent tenter de copier les fichiers binaires compilés dans l'emplacement mentionné précédemment. Si vous n'avez pas défini les autorisations requises, leur génération échoue. Alternativement, vous pouvez laisser les autorisations telles qu’elles sont et exécuter l’invite de commande SDK ou Visual Studio Command Prompt (2012) en tant qu’administrateur, ou construire les échantillons dans Visual Studio 2012, également exécuté en tant qu’administrateur.

    > [!NOTE]
    > Si vous ne procédez pas à cette étape, tous les exemples hébergés par IIS échouent lors de la génération. Veillez à définir les autorisations correctement ou exécutez l'invite de commandes du Kit de développement logiciel (SDK) et de Visual Studio (2012) en tant qu'administrateur.

11. Créez sur l'ordinateur un répertoire C:\logs ; certains exemples peuvent en avoir besoin. Assurez-vous que le compte approprié dispose d’un accès en écriture sur ce dossier. Pour Windows 7, Windows Vista et Windows Server 2008 R2, ce compte est **Network Service**. Pour Windows Server 2008, le compte est NT Authority-Network Service. Pour Windows XP et Windows Server 2003, le compte est ASPNET.

12. Exécutez le fichier Setupcerttool.bat. Ce fichier est \<situé dans le dossier InstallPath>-WF_WCF_Samples-WCF-SetupMD.  Ce script effectue les tâches suivantes :

    - génération de l'outil FindPrivateKey ;

    - création d'un répertoire nommé %ProgramFiles%\ServiceModelSampleTools ;

    - copie du nouvel outil FindPrivateKey dans ce répertoire.

    Cet outil est requis pour les exemples qui utilisent des certificats et sont hébergés dans IIS.

    > [!NOTE]
    > Pour des raisons de sécurité, n'oubliez pas de supprimer la définition de répertoire virtuel et les autorisations accordées au cours des étapes d'installation ci-dessus lorsque vous en avez terminé avec les exemples en exécutant le fichier de commandes Cleanupvroot.bat.

13. Les exemples auto-hébergés (non hébergés dans IIS) doivent être autorisés à enregistrer des adresses HTTP sur l'ordinateur pour pouvoir écouter les données. Ces autorisations (qui permettent de réserver les espaces de noms HTTP) dépendent directement des autorisations dont les comptes d'utilisateurs utilisés pour exécuter ces exemples disposent. Par défaut, les comptes d'administrateur sont autorisés à enregistrer n'importe quelle adresse HTTP. L'autorisation pour les espaces de noms HTTP utilisés par les exemples doit être accordée aux comptes qui ne sont pas administrateur. Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](../feature-details/configuring-http-and-https.md).

14. Certains exemples nécessitent Message Queuing. Voir [Installation de messages file d’attente (MSMQ)](installing-message-queuing-msmq.md) pour les instructions d’installation.

    > [!NOTE]
    > Veillez à démarrez le service MSMQ avant d'exécuter un exemple qui requiert Message Queuing.

15. Certains exemples requièrent des certificats. Voir [Instructions d'installation du certificat de serveur des services Internet (IIS)](iis-server-certificate-installation-instructions.md).
