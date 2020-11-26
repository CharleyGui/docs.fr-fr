---
title: Instructions relatives à l'hébergement dans les Services Internet (IIS)
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 151c5ba8dd79e8554e7d79fb5b8182740b0be18e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237688"
---
# <a name="internet-information-service-hosting-instructions"></a>Instructions relatives à l'hébergement dans les Services Internet (IIS)

Pour exécuter les exemples hébergés par les services IIS (Internet Information Services), vous devez vous assurer que les services IIS sont correctement installés et en cours d'exécution.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Pour installer IIS version 7.5 sur Windows Server 2008 R2  
  
1. Dans **Gestionnaire de serveur**, sélectionnez **rôles.** Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.  
  
2. Cliquez sur **suivant** pour afficher la boîte de dialogue **Sélectionner des rôles de serveurs** .  
  
3. Sélectionnez **serveur d’applications** dans la liste **rôles** , puis cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue Sélectionner des **services de rôle** pour le rôle de serveur d’applications.  
  
4. Activez la case à cocher **serveur Web (IIS)** . Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les fonctionnalités requises**. Cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner des services de rôle** pour le rôle serveur Web (IIS).  
  
5. Développez **outils de gestion**, puis développez **compatibilité avec la gestion IIS 6**. Sélectionnez **outils de script IIS 6**. Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les services de rôle requis**. Cliquez sur **Suivant**.  
  
6. Si le résumé des sélections est correct, cliquez sur **installer**.  
  
7. Une fois l’installation terminée, cliquez sur **Fermer**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Pour installer IIS version 7.5 sur Windows 7  
  
1. Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
2. Ouvrez le groupe **programmes** .  
  
3. Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.  
  
4. La boîte de dialogue **contrôle de compte d’utilisateur** s’affiche. Cliquez sur **Continuer**.  
  
5. La boîte de dialogue **fonctionnalités de Windows** s’affiche. Développez l’élément intitulé **Internet Information Services**.  
  
6. Développez l’élément intitulé **Services World Wide Web**.  
  
7. Développez l’élément **fonctionnalités de développement d’applications**.  
  
8. Assurez-vous que les éléments suivants sont sélectionnés :  
  
    1. **Extensibilité .NET**  
  
    2. **ASP.NET**  
  
    3. **Extensions ISAPI**  
  
    4. **Filtres ISAPI**  
  
9. Sous l’élément intitulé **Services World Wide Web**, développez **fonctionnalités http communes**.  
  
10. Assurez-vous que **contenu statique** est sélectionné.  
  
11. Sous l’élément nommé **World Wide Web services**, développez **sécurité**.  
  
12. Assurez-vous que **l’option authentification Windows** est sélectionnée.  
  
13. Sous le répertoire **Internet Information Services** , développez l’élément **Outils d’administration Web**, puis sélectionnez **console de gestion IIS**.  
  
14. Développez l’élément **compatibilité avec la gestion IIS 6**, puis sélectionnez **outils de script IIS 6**.  
  
15. Sous le répertoire **Internet Information Services** , développez l’élément intitulé **Microsoft .NET Framework 3.5.1**, puis sélectionnez **Windows Communication Foundation activation http**.  
  
16. Cliquez sur **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Pour installer IIS version 7.0 sur Windows Server 2008  
  
1. Dans **Gestionnaire de serveur**, sélectionnez **rôles**. Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.  
  
2. Cliquez sur **suivant** pour afficher la boîte de dialogue **Sélectionner des rôles de serveurs** .  
  
3. Sélectionnez **serveur d’applications** dans la liste **rôles** , puis cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue Sélectionner des **services de rôle** pour le rôle de serveur d’applications.  
  
4. Activez la case à cocher **serveur Web (IIS)** . Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les fonctionnalités requises**. Cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner des services de rôle** pour le rôle serveur Web (IIS).  
  
5. Développez **outils de gestion**, puis développez **compatibilité avec la gestion IIS 6**. Sélectionnez **outils de script IIS 6**. Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les services de rôle requis**. Cliquez sur **Suivant**.  
  
6. Si le résumé des sélections est correct, cliquez sur **installer**.  
  
7. Une fois l’installation terminée, cliquez sur **Fermer**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Pour installer IIS version 7.0 sur Windows Vista  
  
1. Cliquez sur Démarrer, puis sur Panneau de configuration.  
  
2. Sélectionnez le groupe **programmes** .  
  
3. Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.  
  
4. La boîte de dialogue **contrôle de compte d’utilisateur** s’affiche. Cliquez sur **Continuer**.  
  
5. La boîte de dialogue **fonctionnalités de Windows** s’affiche. Développez l’élément intitulé **Internet Information Services**.  
  
6. Développez l’élément intitulé **Services World Wide Web**.  
  
7. Développez l’élément **fonctionnalités de développement d’applications**.  
  
8. Assurez-vous que les éléments suivants sont sélectionnés :  
  
    1. **Extensibilité .NET**  
  
    2. **ASP.NET**  
  
    3. **Extensions ISAPI**  
  
    4. **Filtres ISAPI**  
  
9. Développez l’élément **Outils d’administration Web**, puis sélectionnez **console de gestion IIS**.  
  
10. Sous l’élément intitulé **Services World Wide Web**, développez **fonctionnalités http communes**.  
  
11. Assurez-vous que **contenu statique** est sélectionné.  
  
12. Sous l’élément nommé **World Wide Web services**, développez **sécurité**.  
  
13. Vérifiez que **l’option authentification Windows** est sélectionnée.  
  
14. Développez l’élément **compatibilité avec la gestion IIS 6**, puis sélectionnez **outils de script IIS 6**.  
  
15. Développez l’élément intitulé **Microsoft .NET Framework 3,0**, puis sélectionnez **Windows Communication Foundation activation http**.  
  
16. Cliquez sur **OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Pour installer IIS version 6.0 sur Windows Server 2003  
  
1. Dans **gérer votre serveur**, cliquez sur **Ajouter ou supprimer un rôle**, puis cliquez sur **suivant**.  
  
2. Sélectionnez **serveur d’applications (IIS, ASP.net)** dans la liste **rôle de serveur** , puis cliquez sur **suivant**.  
  
3. Activez la case à cocher **activer ASP.net** , puis cliquez sur **suivant**.  
  
4. Si l'aperçu des sélections est correct, cliquez sur Suivant.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Pour installer IIS version 5.1 sur Windows XP avec Service Pack 2 et Service Pack 3 installés  
  
1. Dans le Panneau de configuration, cliquez sur **Ajout/Suppression de programmes**.  
  
2. Dans la boîte de dialogue **Ajouter ou supprimer des programmes**, cliquez sur **Ajouter ou supprimer des composants Windows**.  
  
3. Dans l **'Assistant composants de Windows**, activez la case à cocher **Internet Information Services (IIS)** , puis cliquez sur **suivant**.  
  
4. Si la boîte de dialogue **fichiers nécessaires** s’affiche, insérez le disque d’installation du système d’exploitation, accédez au dossier i386, puis cliquez sur **OK**.  
  
5. Une fois l’installation terminée, cliquez sur **Terminer**.  
  
6. Fermez la boîte de dialogue **Ajout/suppression de programmes** , puis fermez le **panneau de configuration**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Pour vérifier l'installation d'IIS et d'ASP.NET  
  
1. Enregistrez le fichier HTML indiqué à la fin de cette rubrique dans le répertoire \InetPub\wwwroot racine et nommez-le Default.aspx.  
  
2. Ouvrez une fenêtre de navigateur.  
  
3. Tapez `http://localhost/Default.aspx` dans la zone adresse, puis appuyez sur entrée.  
  
4. Une page web contenant le texte « Hello World » doit apparaître.  
  
> [!NOTE]
> Chaque fois que vous installez une nouvelle version du .NET Framework, vous devez réinscrire aspnet_isapi en tant qu’extension de service Web pour IIS. Pour ce faire, émettez la commande `aspnet_regiis –I –enable`.  
  
## <a name="sample-code"></a>Exemple de code  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
