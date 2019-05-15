---
title: Guide de déploiement du .NET Framework pour les administrateurs
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4710f299c97a6ef8039314243ca481db51c2bb52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614084"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Guide de déploiement du .NET Framework pour les administrateurs

Cet article explique étape par étape comment un administrateur système peut déployer [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et ses dépendances système dans un réseau à l'aide de Microsoft System Center Configuration Manager (SCCM). Cet article suppose que tous les ordinateurs clients cibles ont la configuration minimale requise pour le .NET Framework. Pour obtenir la liste des configurations logicielle et matérielle requises pour installer le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez [Configuration système requise](../../../docs/framework/get-started/system-requirements.md).

> [!NOTE]
> Les logiciels référencés dans ce document, y compris, mais de manière non limitative, le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager et Active Directory, sont tous soumis à des termes et conditions de contrat de licence. Les présentes instructions supposent que lesdits termes et conditions du contrat de licence ont été passés en revue et acceptés par les propriétaires de licences des logiciels concernés. Ces instructions ne remplacent pas les termes et conditions desdits contrats de licence.
>
> Pour plus d’informations sur la prise en charge du .NET Framework, consultez la [FAQ sur la politique de support pour Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) sur le site web Aide et Support de Microsoft.

Cette rubrique contient les sections suivantes :

- [Processus de déploiement](#the_deployment_process)
- [Déploiement du .NET Framework](#deploying_in_a_test_environment)
- [Créer un regroupement](#creating_a_collection)
- [Créer un package et un programme](#creating_a_package)
- [Sélectionner un point de distribution](#select_dist_point)
- [Déployer le package](#deploying_package)
- [Ressources](#resources)
- [Résolution des problèmes](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Processus de déploiement

Lorsque l'infrastructure de prise en charge est en place, utilisez System Center 2012 Configuration Manager pour déployer le package redistribuable .Net Framework sur les ordinateurs du réseau. Générer l’infrastructure implique la création et la définition de cinq éléments principaux : les regroupements, un package et un programme pour les logiciels, des points de distribution et des déploiements.

- Les **regroupements** sont des ensembles de ressources de Configuration Manager, tels que des utilisateurs, des groupes d’utilisateurs ou des ordinateurs, sur lesquels le .Net Framework est déployé. Pour plus d’informations, consultez [Présentation de regroupements dans System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) dans la bibliothèque de la documentation Configuration Manager.

- Les **packages et programmes** sont généralement les applications logicielles à installer sur un ordinateur client, mais ils peuvent également contenir des fichiers individuels, des mises à jour, ou même des commandes individuelles. Pour plus d’informations, consultez [Packages et programmes dans System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) dans la bibliothèque de la documentation Configuration Manager.

- Les **points de distribution** sont des rôles de système de site Configuration Manager qui stockent les fichiers requis pour l’exécution des logiciels sur les ordinateurs clients. Lorsque le client Configuration Manager reçoit et traite un déploiement de logiciel, il contacte un point de distribution pour télécharger le contenu associé au logiciel et démarrer le processus d'installation. Pour plus d’informations, consultez [Concepts fondamentaux de la gestion de contenu dans Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) dans la bibliothèque de la documentation Configuration Manager.

- Les **déploiements** font en sorte que les membres applicables du regroupement cible spécifié installent le package logiciel.

> [!IMPORTANT]
> Les procédures de cette rubrique contiennent les paramètres classiques pour créer et déployer un package et un programme, et ne couvrent pas tous les paramètres possibles. Pour d’autres options de déploiement de Configuration Manager, consultez la [Bibliothèque de documentation Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Déployer le .NET Framework

Vous pouvez utiliser System Center 2012 Configuration Manager pour déployer une installation sans assistance de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pour laquelle les utilisateurs n'interagissent pas avec le processus d'installation. Procédez comme suit :

1. [Créez un regroupement](#creating_a_collection).

2. [Créez un package et un programme pour le package redistribuable .Net Framework](#creating_a_package).

3. [Sélectionnez un point de distribution](#select_dist_point).

4. [Déployez le package](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Créer un regroupement

Dans cette étape, sélectionnez les ordinateurs sur lesquels seront déployés le package et le programme, et regroupez-les dans un regroupement de périphériques. Pour créer un regroupement dans Configuration Manager, utilisez des règles d’adhésion directes (où les membres du regroupement sont spécifiés manuellement) ou des règles de requête (où Configuration Manager détermine les membres du regroupement selon des critères que vous avez spécifiés). Pour plus d’informations sur les règles d’adhésion, notamment les règles directes et de requête, consultez [Présentation des regroupements dans System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) dans la bibliothèque de la documentation Configuration Manager.

Pour créer un regroupement

1. Dans la Console Configuration Manager, choisissez **Ressources et Conformité**.

2. Dans l’espace de travail **Ressources et Conformité**, choisissez **Regroupements de périphériques**.

3. Sous l’onglet **Accueil** dans le groupe **Créer**, choisissez **Créer un regroupement de périphériques**.

4. Dans la page **Général** de l’**Assistant Création d’un regroupement de périphériques**, entrez un nom pour le regroupement.

5. Choisissez **Parcourir** pour spécifier un regroupement limité.

6. Dans la page **Règles d’adhésion**, choisissez **Ajouter une règle**, puis **Règle directe** pour ouvrir l’**Assistant Création d’une règle d’adhésion directe**. Sélectionnez **Suivant**.

7. Dans la page **Rechercher des ressources**, dans la liste **Classe de ressource**, choisissez **Ressource système**. Dans la liste **Nom de l’attribut**, choisissez **Nom**. Dans le champ **Valeur**, entrez `%` et choisissez **Suivant**.

8. Dans la page **Sélectionner les ressources**, cochez la case de chaque ordinateur sur lequel vous souhaitez déployer le .Net Framework. Choisissez **Suivant**, puis terminez l’Assistant.

9. Dans la page **Règles d’adhésion** de l’**Assistant Création d’un regroupement de périphériques**, choisissez **Suivant**, puis terminez l’Assistant.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Créer un package et un programme pour le package redistribuable .Net Framework

Les étapes suivantes permettent de créer manuellement un package pour le package redistribuable .NET Framework. Le package contient les paramètres spécifiés pour l'installation du .Net Framework et l'emplacement à partir duquel le package sera distribué aux ordinateurs cibles.

Pour créer un package :

1. Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.

2. Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.

3. Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un package**.

4. Dans la page **Package** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :

    - Nom : `.NET Framework 4.5`

    - Fabricant : `Microsoft`

    - Langue : `English (US)`

5. Choisissez **Ce package contient des fichiers sources**, puis **Parcourir** pour sélectionner le dossier local ou réseau qui contient les fichiers d’installation du .Net Framework. Quand vous avez sélectionné le dossier, choisissez **OK**, puis **Suivant**.

6. Dans la page **Type de programme** de l’Assistant, choisissez **Programme standard**, puis **Suivant**.

7. Dans la page **Programme** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :

    1. **Nom :** `.NET Framework 4.5`

    2. **Ligne de commande :** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (les options de ligne de commande sont décrites dans le tableau après ces étapes)

    3. **Exécuter :** choisissez **Masqué**.

    4. **Le programme peut s’exécuter :** sélectionnez l’option qui spécifie que le programme peut s’exécuter que l’utilisateur soit connecté ou non.

8. Dans la page **Exigences**, acceptez les valeurs par défaut en choisissant **Suivant**, puis terminez l’Assistant.

Le tableau suivant décrit les options de ligne de commande spécifiées dans l'étape 7.

|Option|Description|
|------------|-----------------|
|**/q**|Définit le mode silencieux. Aucune entrée d'utilisateur n'est requise, et aucun résultat n'est affiché.|
|**/norestart**|Empêche le programme d'installation de redémarrer automatiquement. Si vous utilisez cette option, Configuration Manager doit gérer le redémarrage de l'ordinateur.|
|**/chainingpackage** *nom_package*|Spécifie le nom du package qui effectue le chaînage. Ces informations sont stockées avec d’autres informations de session d’installation pour les personnes inscrites au [Programme d’amélioration du produit Microsoft (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **/chainingpackage "Chaining Product"**.|

Les étapes suivantes créent un package nommé .Net Framework 4.5. Le programme déploie une installation sans assistance de .Net Framework 4.5. Dans une installation sans assistance, les utilisateurs n’interagissent pas avec le processus d’installation et l’application de chaînage doit capturer le code de retour et gérer le redémarrage. Pour plus d’informations, consultez [Getting Progress Information from an Installation Package](https://go.microsoft.com/fwlink/?LinkId=179606).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Sélectionner un point de distribution

Pour distribuer le package et le programme aux ordinateurs clients à partir d'un serveur, vous devez d'abord désigner un système de site comme un point de distribution, puis distribuer le package au point de distribution.

Utilisez les étapes suivantes pour sélectionner un point de distribution pour le package de .Net Framework 4.5 créé au cours la section précédente :

1. Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.

2. Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.

3. Dans la liste de packages, sélectionnez le package **.Net Framework 4.5** créé dans la section précédente.

4. Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Distribuer du contenu**.

5. Sous l’onglet **Général** de l’**Assistant Distribuer du contenu**, choisissez **Suivant**.

6. Dans la page **Destination du contenu** de l’Assistant, choisissez **Ajouter**, puis **Point de distribution**.

7. Dans la boîte de dialogue **Ajouter des points de distribution**, sélectionnez les points de distribution qui hébergeront le package et le programme, puis choisissez **OK**.

8. Effectuez toutes les étapes de l'Assistant.

Le package contient désormais toutes les informations nécessaires au déploiement sans assistance de .Net Framework 4.5. Avant de déployer le package et le programme, vérifiez qu’il a été installé sur le point de distribution ; consultez la section « Surveiller le contenu » de la page [Surveiller le contenu distribué avec System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) dans la bibliothèque de la documentation Configuration Manager.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Déployer le package

Pour déployer le package et le programme .Net Framework 4.5 :

1. Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.

2. Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.

3. Dans la liste des packages, sélectionnez le package que vous avez créé, appelé **.Net Framework 4.5**.

4. Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.

5. Dans la page **Général** de l’**Assistant Déploiement logiciel**, choisissez **Parcourir**, puis sélectionnez le regroupement créé précédemment. Sélectionnez **Suivant**.

6. Dans la page **Contenu** de l’Assistant, vérifiez que le point à partir duquel vous souhaitez distribuer le logiciel s’affiche, puis choisissez **Suivant**.

7. Dans la page **Paramètres de déploiement** de l’Assistant, vérifiez que **Action** est défini sur **Installer**, et **Objectif** sur **Requis**. Cela garantit que le package logiciel est une installation obligatoire sur les ordinateurs ciblés. Sélectionnez **Suivant**.

8. Dans la page **Planification** de l’Assistant, spécifiez à quel moment vous souhaitez que le .Net Framework soit installé. Choisissez **Nouveau** pour déterminer le moment de l’installation, ou demandez au logiciel d’effectuer l’installation quand l’utilisateur se connecte ou se déconnecte, ou dès que possible. Sélectionnez **Suivant**.

9. Dans la page **Expérience utilisateur** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.

    > [!WARNING]
    > Il est possible que votre environnement de production ait des stratégies qui requièrent des sélections différentes pour la planification de déploiement. Pour plus d’informations sur ces options, consultez [Propriétés du nom de la publication : Onglet Calendrier](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Dans la page **Points de distribution** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.

11. Effectuez toutes les étapes de l'Assistant. Vous pouvez surveiller la progression du déploiement dans le nœud **Déploiements** de l’espace de travail **Surveillance**.

Le package est déployé dans le regroupement ciblé et l’installation sans assistance du .Net Framework 4.5 peut commencer. Pour plus d’informations sur les codes d’erreur liés à l’installation du .NET Framework 4.5, consultez la section [Codes de retour](#return_codes) plus loin dans cette rubrique.

<a name="resources"></a>

## <a name="resources"></a>Ressources

Pour plus d'informations sur l'infrastructure pour tester le déploiement du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez les ressources suivantes.

**Active Directory, DNS, DHCP :**

- [Services de domaine Active Directory](/windows/desktop/ad/active-directory-domain-services)

- [DNS (Domain Name System)](/windows-server/networking/dns/dns-top)

- [DHCP (Dynamic Host Configuration Protocol)](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008 :**

- [Installation de SQL Server 2008 (Vidéo liée à SQL Server)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [Présentation de la sécurité SQL Server 2008 pour les administrateurs de base de données](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**System Center 2012 Configuration Manager (point de gestion, point de distribution) :**

- [Administration de site pour System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Planification et déploiement d’un site Configuration Manager unique](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Client System Center 2012 Configuration Manager pour des ordinateurs Windows :**

- [Déploiement de clients pour System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="log-file-locations"></a>Emplacements des fichiers journaux

Les fichiers journaux suivants sont générés lors de l’installation du .NET Framework :

- %temp%\Microsoft .NET Framework *version*\*.txt
- %temp%\Microsoft .NET Framework *version*\*.html

où *version* est la version du .NET Framework que vous installez, comme 4.5 ou 4.7.2.

Vous pouvez également spécifier le répertoire où les fichiers journaux sont écrits avec l’option de ligne de commande `/log` dans la commande d’installation du .NET Framework. Pour plus d’informations, consultez [Guide de déploiement du .NET Framework pour les développeurs](deployment-guide-for-developers.md#command-line-options).

Vous pouvez utiliser [l’outil de collecte des journaux](https://www.microsoft.com/download/details.aspx?id=12493) pour collecter les fichiers journaux du .NET Framework et créer un fichier CAB compressé (.cab) afin de réduire la taille des fichiers.

<a name="return_codes"></a>

### <a name="return-codes"></a>Codes de retour

Le tableau suivant répertorie les codes de retour les plus courants pour le programme d'installation du package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Les codes de retour sont identiques pour toutes les versions du programme d'installation.

Pour plus d’informations, consultez la section suivante : [Codes d’erreur de téléchargement](#additional_error_codes).

|Code de retour|Description|
|-----------------|-----------------|
|0|Installation terminée.|
|1602|L'utilisateur a annulé l'installation.|
|1603|Une erreur irrécupérable s'est produite pendant l'installation.|
|1641|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|
|3010|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|
|5100|L'ordinateur de l'utilisateur n'a pas la configuration requise.|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a>Codes d'erreur de téléchargement

- [Codes d’erreur du service de transfert intelligent en arrière-plan (BITS)](/windows/desktop/Bits/bits-return-values)

- [Codes d’erreur du moniker d’URL](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Codes d’erreur WinHttp](/windows/desktop/WinHttp/error-messages)

Autres codes d'erreur :

- [Codes d’erreur Windows Installer](/windows/desktop/msi/error-codes)

- [Codes de résultat de l’agent de mise à jour automatique Windows Update](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Voir aussi

- [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Configuration système requise](../../../docs/framework/get-started/system-requirements.md)
