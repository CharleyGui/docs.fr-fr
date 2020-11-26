---
title: Instructions d'installation du répertoire virtuel
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: dba6547888935ccf36ec0924fd3c95e8fbda5688
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243649"
---
# <a name="virtual-directory-setup-instructions"></a>Instructions d'installation du répertoire virtuel

Les exemples de Windows Communication Foundation (WCF) sont destinés à partager un répertoire virtuel commun nommé servicemodelsamples mappé au dossier%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
> %SystemDrive% correspond généralement à C: ou D:, en fonction de l'emplacement de lecteur où Internet Information Services (IIS) est installé.  
  
 Vous pouvez exécuter les fichiers Setupvroot.bat et Cleanupvroot.bat à partir de la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) afin de créer le répertoire virtuel. Si vous préférez créer le répertoire virtuel manuellement, exécutez les procédures suivantes.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Pour créer un répertoire virtuel dans IIS 7,0 ou 7,5  
  
1. Dans le menu **Démarrer** , cliquez sur **exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).  
  
2. Dans le volet gauche, développez le nœud portant le nom de l’ordinateur, puis développez le nœud **sites** .  
  
3. Cliquez avec le bouton droit sur **site Web par défaut**, puis sélectionnez **Ajouter une application** pour ouvrir la **fenêtre Ajouter une application**.  
  
4. Dans la fenêtre, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.  
  
5. Créez le répertoire suivant : %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin d’accès physique.  La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.  
  
7. Cliquez sur **OK**. L'application Web est créée pour les exemples WCF.  
  
    > [!NOTE]
    > Cette tâche ne doit être effectuée qu’une seule fois, car tous les exemples WCF utilisent la même application Web servicemodelsamples.  
  
    > [!NOTE]
    > Dans cette documentation, le terme `virtual directory` est synonyme du terme `Web application`.  
  
     En plus de créer le répertoire virtuel, vous devez également définir ses propriétés pour permettre l’exécution des services WCF. Voir les détails ci-dessous.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Pour créer un répertoire virtuel dans IIS 5.1 ou 6.0 :  
  
1. Ouvrez une fenêtre d’invite de commandes et tapez `start inetmgr` pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).  
  
2. Dans le volet gauche, développez le nœud portant le nom de l’ordinateur, puis développez le nœud **sites Web** .  
  
3. Cliquez avec le bouton droit sur **site Web par défaut** et sélectionnez **nouveau, répertoire virtuel** pour ouvrir l’Assistant Création de répertoire virtuel.  
  
4. Dans l’Assistant, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.  
  
5. Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin. La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.  
  
6. Cliquez sur **Suivant**.  
  
7. Les cases à cocher suivantes sont activées par défaut :  
  
    - **Lire**  
  
    - **Exécuter les scripts (tels que ASP)**  
  
8. Cliquez sur **suivant**, puis sur **Terminer** pour terminer l’Assistant.  
  
    > [!NOTE]
    > Cette tâche ne doit être effectuée qu’une seule fois, car tous les exemples WCF utilisent le même répertoire virtuel servicemodelsamples.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 7,0 ou 7,5  
  
1. Cliquez sur le nœud servicemodelsamples. Deux vues figurent au bas de la fenêtre. Sélectionnez **affichage des fonctionnalités** s’il n’est pas déjà sélectionné.  
  
2. Double-cliquez sur l’entrée pour l' **exploration des répertoires**.  
  
3. Dans le volet Actions, sélectionnez l’option **activer** . Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.  
  
 Enfin, vous devez définir les propriétés de sécurité du dossier servicemodelsamples afin d’autoriser son accès. Voir les détails ci-dessous.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 5.1 ou 6.0  
  
1. Cliquez avec le bouton droit sur le nœud servicemodelsamples, puis cliquez sur **Propriétés**.  
  
2. Les cases à cocher suivantes sont activées par défaut :  
  
    - **Lire**  
  
    - **Visites des journaux**  
  
    - **Indexer cette ressource**  
  
3. Activez la case à cocher **exploration de répertoire** . Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Pour définir les propriétés de sécurité du dossier dans IIS 7,0 ou 7,5  
  
1. Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Cliquez avec le bouton droit sur le dossier servicemodelsamples, puis cliquez sur **partager** ou **partager avec**.  
  
3. Cliquez sur la flèche vers le bas située à gauche du bouton **Ajouter** .  
  
4. Sélectionnez l’entrée **Rechercher** . La fenêtre **Sélectionner les utilisateurs ou les groupes** s’ouvre.  
  
5. Cliquez sur **Avancé**.  
  
6. Cliquez sur **Emplacements**. La fenêtre **emplacements** est maintenant ouverte.  
  
7. Sélectionnez l'entrée correspondant à l'ordinateur en cours d'utilisation. Il est important de sélectionner l'ordinateur local et non une entrée correspondant à tous les domaines ou réseaux répertoriés. Une fois l’ordinateur sélectionné, cliquez sur **OK**.  
  
8. Cliquez sur **Rechercher**. Cela permet d'inclure dans les résultats de la recherche les objets associés à l'ordinateur local.  
  
9. Recherchez l’entrée **IIS_IUSRS** dans la colonne **nom (nom unique relatif)** . Sélectionnez cette entrée, puis cliquez sur **OK** pour fermer la fenêtre résultats de la recherche.  
  
10. Cliquez sur **OK** pour fermer la fenêtre **Sélectionner les utilisateurs ou les groupes** .  
  
11. Cliquez sur **partager** pour rendre les modifications persistantes.  
  
12. Une fois que les modifications apportées à activer le partage sont terminées, cliquez sur **terminé** pour fermer la fenêtre de **partage de fichiers** .  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Pour définir les propriétés de sécurité de ce dossier dans IIS 5.1 ou 6.0 :  
  
1. Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Cliquez avec le bouton droit sur le dossier **servicemodelsamples** , puis cliquez sur **partage et sécurité.**  
  
3. Cliquez sur l’onglet **Security** .  
  
4. Si vous utilisez IIS 6,0, dans la zone **noms de groupes ou d’utilisateurs** , vérifiez si le **compte invité Internet** est répertorié.  
  
     Si elle ne s'y trouve pas :  
  
    1. Cliquez sur **Démarrer** , puis sur **panneau de configuration**.  
  
    2. Si vous ne voyez pas l’icône **comptes d’utilisateur** , cliquez sur **basculer vers l’affichage des catégories**.  
  
    3. Cliquez sur l’icône **comptes d’utilisateurs** .  
  
    4. Sous « ou choisissez une icône du panneau de configuration », cliquez sur **comptes d’utilisateurs**.  
  
    5. Dans la boîte de dialogue **comptes d’utilisateur** , cliquez sur l’onglet **avancé** .  
  
    6. Cliquez sur **Avancé**.  
  
    7. Dans la boîte de dialogue **utilisateurs et groupes locaux** , cliquez pour développer le dossier **utilisateurs** .  
  
    8. Dans le volet droit, double-cliquez sur **compte invité Internet**.  
  
    9. Dans la boîte de dialogue **Propriétés** , copiez le nom utilisé en tant que compte invité Internet. Par défaut, le nom commence par « USR_ » suivi du nom de l'ordinateur.  
  
    10. Fermez la boîte de dialogue **Propriétés** .  
  
    11. Fermez la boîte de dialogue **utilisateurs et groupes locaux** .  
  
    12. Fermez la boîte de dialogue **comptes d’utilisateur** .  
  
    13. Fermez la boîte de dialogue autres **comptes d’utilisateur** .  
  
    14. Dans la boîte de dialogue **Propriétés de servicemodelsamples** , sous l’onglet **sécurité** , cliquez sur **Ajouter**.  
  
    15. Tapez le nom de l’ordinateur suivi d’une barre oblique inverse, puis collez le nom du compte d’utilisateur Internet, par exemple myMachineName \\ % InternetGuestAccountName%.  
  
    16. Cliquez sur **vérifier les noms** pour vérifier l’ajout. S'il est valide, ce nom figure en majuscules soulignées.  
  
5. Pour IIS 6,0, vérifiez également que SERVICE réseau est indiqué dans la zone **noms de groupes ou d’utilisateurs** .  
  
     Si SERVICE RÉSEAU n'est pas répertorié :  
  
    1. Cliquez sur **Add**.  
  
    2. Dans la boîte de dialogue **Sélectionner les utilisateurs ou les groupes** , tapez le nom de l’ordinateur suivi d’une barre oblique inverse.  
  
    3. Tapez **service** après la barre oblique inverse (sans espace).  
  
    4. Cliquez sur **vérifier les noms**.  
  
    5. Si plusieurs noms sont trouvés, sélectionnez **service réseau** , puis cliquez sur **OK**.  
  
    6. Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** .  
  
6. Si vous utilisez Windows XP SP2 avec IIS 5,1, vérifiez que compte invité Internet et ASPNET sont répertoriés dans la zone **noms de groupes ou d’utilisateurs** .  
  
     Notez que l’utilisateur ASPNET peut être membre du groupe de sécurité **utilisateurs** intégré. Si c’est le cas, si le groupe **utilisateurs** est répertorié dans la boîte de dialogue, vous n’avez pas besoin de l’ajouter en tant qu’élément distinct à la liste des utilisateurs autorisés.  
  
     Pour vérifier si ASPNET fait partie du groupe de sécurité **utilisateurs** :  
  
    1. Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.  
  
    2. Cliquez sur l’icône **comptes d’utilisateurs** .  
  
    3. Dans la colonne **groupe** , vérifiez que la valeur de **ASPNET** est « utilisateurs ».  
  
## <a name="see-also"></a>Voir aussi

- [Instructions relatives à l'hébergement dans les Services Internet (IIS)](internet-information-service-hosting-instructions.md)
